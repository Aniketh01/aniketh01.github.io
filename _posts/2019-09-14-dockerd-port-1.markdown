---
comments: true
layout: post
title: "Dockerd port for macOS - Part 1."
date: "2019-09-14"
slug: "dockerd_port_part_1"
author: Aniketh Girish
project: 'Dockerd'
tags: 
- OSS
- dockerd
---

TLDR; This is something that I proposed for the entire workflow of dockerd port for macOS.

Hi all,

I have graciously given up on my wish of regularly blogging my life or even my work :(. Hence another late blog. I had spent 2 months in Tokyo interning as a research associate in Internet Initiative Japan - Innovation Institute(IIJ-II) where I worked on Docker port to macOS - and hence such a post. As always, I will try to write another blog on my experience living in Tokyo for two months in another post - but let this post be complete technical.

I'm splitting the contents of this post into two. This post will contain the background study on what exactly are we looking at the port of dockerd for macOS and why we actually need that? Next post will be all about the work I did and the results.

Let's start with understanding the background of docker and how docker works.

Docker is composed of two main components, a command-line application for users and a daemon which manages containers. The daemon relies on two sub-components to perform its job, storage on the host file system for image and container data; and the LXC interface(runC) to abstract away the raw kernel calls needed to construct a Linux container.

All these functionalities are tightly coupled with Linux kernel features and our main motive is to bring agility for the docker project to co-exist in multiple platforms.

Core Kernel dependencies were:

- Kernel namespaces (ipc, uts, mount, pid, network and user)
- Apparmor and SELinux profiles
- Seccomp policies
- Chroots (using pivot_root)
- Kernel capabilities
- and CGroups (control groups)

To port **dockerd** server side daemon of docker to macOS. macOS currently uses a hypervisor to run the dockerd daemon on linux kernel system. Our goal is to eliminate this middleware, let the dockerd daemon communicate directly with the darwin kernel instead of running the daemon inside a isolated hypervisor providing Linux kernel architecture. 

The current scenario for macOS to run docker in the host system is that, it availes a docker client which runs in the host system itself while the server side dockerd daemon runs in the Linux VM/hypervisor. Therefore, for the client to connect with the server dockerd daemon it has to tunnel through this Linux hypervisor. 

Our intention is to port dockerd daemon to run in macOS without an intermediate Linux hypervisor to let docker communicate with the dockerd server directly without an overhead of another stack running beneath. Which implies. We provide Darwin based support for docker to run dockerd independent of LKL based VM and henceforth, let the dockerd  after the port to be able to instantiate a Linux application. 

Docker engine exposes the rest API which can be used to control the daemon. The client, docker uses this API to give instructions to the daemon. The Docker client interfacing through dockerd CLI to connect with the dockerd daemon, listens for Docker API requests and this dockerd  tracks everything related to Docker, including containers, images, volumes, service definition, and secrets. 

 Docker engine is responsible for running processes in isolated environments. For each process, it generates a new Linux container, allocates a new filesystem for it, allocates a network interface, sets an IP for it, sets NAT for it and then runs processes inside of it. It also manages such things as creating, removing images, fetching images from the registry of choice, creating, restarting, removing containers and many other things. 

![](https://lh6.googleusercontent.com/pQM3InukQ-puwKegsZMQwgEsrroqs4oo-9mWkGslK1Wi8m60W8hv2O6E2R7S02cpFppD23veRAXTEC8xLLb7drOoLY-tN1860ugtxi3Xp1wNyV0T-rxihl2XGYRVA1vWuvrhbKoU)

The above image illustrates the way how docker works on macOS. Our main goal is to eliminate the LinuxKit VM from this architecture. Docker daemon uses Linux kernel vastly to communicate with the host. We need to figure out where all Linux kernel modules, drivers are used and further port those to analogues darwin based code. Further, while we remove the LinuxVM kit, there will dependencies that are related to the hypervisor (virtualisation), networking and the filesystem part. We have to bring in all of that changes into the engine so that dockerd runs independent of Linux kernel.

We will start of with few minor ports which can be easily found out by compilation and building the dockerd engine in macOS system. This would give enough time to help us understand a bit of code architecture as well as would let us plan ahead on where are major changes has to be brought. 

On Docker for Mac, clients can connect to the Docker Engine through a Unix socket: `unix:///var/run/docker.sock`. We have to debug and trace how this call goes and connect the dockerd daemon server and port most of the underlying code that the stack shows.

### - **Virtualization**

As mentioned, currently this is how virtualization happens inside the docker for macOS: 

<center><img src="https://i1.wp.com/www.docker.com/blog/wp-content/uploads/Blog.-Are-containers-..VM-Image-1-1024x435.png?ssl=1"></center>


### - **Networking**


<center><img src="https://docs.docker.com/engine/tutorials/bridge2.png" width="700"></center>

Our aim at this point is an effective way to reconstruct container traffic into separate TCP/IP flows and translate them into native OSX socket. Currently, it uses a VPN kit to channel the traffic between the client and the server. 

We need to figure out a way to have DHCP, NTP as a standalone ethernet datagram as how docker for Linux illustrates brought into macOS as well by separating the needful module from the VPN kit.  Henceforth, This lets the container to run and create socket with it to expose the container to localhost. 

Next, There is no docker0 bridge on macOS Because of the way networking is implemented in Docker Desktop for Mac, you cannot see a docker0 interface on the host. That is, there is no docker0 interface on the host for macOS, we need to separate that from the hypervisor network management interface. This interface is actually within the virtual machine. We need to bring that out of the virtual system and integrate it directly to the engine.

### - **Filesystem sharing**

<center><img src="https://image.slidesharecdn.com/dockerinternals-mountainviewmeetup-150422173344-conversion-gate02/95/docker-internals-7-638.jpg?cb=1429724071"></center>

Here in the filesystem segment, we have to figure out ways to communicate with osxfs system without a intermediate Linux host client like FUSE that provides API calls to osxfs system.

**Namespaces**

Docker uses a technology called namespaces to provide the isolated workspace called the container. When you run a container, Docker creates a set of namespaces for that container.

These namespaces provide a layer of isolation. Each aspect of a container runs in a separate namespace and its access is limited to that namespace.

Docker Engine uses namespaces such as the following on Linux:

- The pid namespace: Process isolation (PID: Process ID).
- The net namespace: Managing network interfaces (NET: Networking).
- The ipc namespace: Managing access to IPC resources (IPC: InterProcess Communication).
- The mnt namespace: Managing filesystem mount points (MNT: Mount).
- The uts namespace: Isolating kernel and version identifiers. (UTS: Unix Timesharing System).

**Control groups**

Docker Engine on Linux also relies on another technology called control groups (cgroups). A cgroup limits an application to a specific set of resources. Control groups allow Docker Engine to share available hardware resources to containers and optionally enforce limits and constraints. For example, you can limit the memory available to a specific container.

**Union file systems**

Union file systems, or UnionFS, are file systems that operate by creating layers, making them very lightweight and fast. Docker Engine uses UnionFS to provide the building blocks for containers. Docker Engine can use multiple UnionFS variants, including AUFS, btrfs, vfs, and DeviceMapper.

**Container format**

Docker Engine combines the namespaces, control groups, and UnionFS into a wrapper called a container format. The default container format is libcontainer.

This is the background study that we need to do a complete port of dockerd. Note, these changes are not just limited to dockerd alone but can span across containerd, runU and much more.

Due to the time constraints, I couldn't explain each and everything on how docker works exactly, but you can find other blog posts on the same. This majorly is a proposal on how I think dockerd could be ported to macOS without a Linux VM enacting as middleware and hence directly communicate with the host and provide a general cross-platform docker implementation.

This post contains the rest of my work and how I achieved a cross-platform docker implementation: 

[https://anikethgirish.wordpress.com/2019/09/14/dockerd-port-for-macos-part-2/](https://anikethgirish.wordpress.com/2019/09/14/dockerd-port-for-macos-part-2/)

Happy reading peeps!

Cheers.