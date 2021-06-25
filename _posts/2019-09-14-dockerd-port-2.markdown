---
comments: true
layout: post
title: "Dockerd port for macOS - Part 2."
date: "2019-09-14"
slug: "dockerd_port_part_2"
author: Aniketh Girish
project: 'Dockerd'
draft: false
---

TLDR;

Hey!!,

This is the continuation of the last post since I thought once I gave an introduction about what docker is and what this project was all about, it is better to have the rest written as a separate blog since it will be easier to skim through :D

The dockerd port to macOS eventually started as a subset research goal carried in the redesign of container stack to experiment and measure extensible and platform independence attained in containers on `µKontainer` of which a library operating system was introduced which decouples the kernel component and uses that as the container kernel within pure user space processes. On this light, docker has introduced a light guest VM for docker to run on macOS - while docker in Linux run directly on the host machine. With the introduction of `µKontainer` docker could be run directly on the macOS host. Therefore, this port of dockerd on macOS looks at the implementation of docker in macOS with the help of `µKontainer` and henceforth attain an implementation of docker independent of the host kernel it runs on.

<center>
<img src="https://lh4.googleusercontent.com/WQ3x3rBTL2SzyxLJw4uwODr479R_8LAwoVmT2EPlJZj65cdtBNfFy7DdCPG9tYyHVK0w19l-794laN4LYdE7w44X_Wr_e0q8iydyaskWJp55FLd5-_XMeDUy5hPV2Vzgh7uYYWoP">
</center>

With the context of the image above, docker for macOS heavily relies on the guest Linux VM to emulate missing components of Linux kernel in darwin host. Due to this advent of the guest Linux VM, Docker daemon is intertwined vastly with Linux kernel to communicate with the host. Henceforth, this makes it impossible to run dockerd directly on the host machine and rather has to use an intermediate guest VM - where the dockerd, the daemon side of docker exists within the VM while the docker client on host. Our proposed fix with `µKontainer` improves this scenario of the existence of dockerd on macOS host without this intermediate guest VM to run docker independent of the host. 

Introduction of `µKontainer` does not only promises the platform independence attained by docker, but it also provides enough extensibility to introduce analogues components/features into the docker engine we introduce.


The low-level OCI Runtime environment, run**U** handles the creation of containers. Within the context of run**U,** it does a fork+exec call to initiate calls towards LKL (libOS) and the application to be executed. Containerd enacts as a process that could be used to manage these containers to build and start the execution of the application within the scope of these containers. Further, Docker engine/dockerd is responsible to run an application over the containers and scale.

Docker in macOS is split into two processes; docker client and dockerd daemon. Docker client uses dockerd daemon to communicate with the container processes. 

With frankenlibc, and runu under ukontainer github-org, you can run Linux application on macOS.  we've also integrated this with docker image, which can be used with containerd and ctr utilities.

The docker image which we created, named runu-base[1] - this image gets executed since the image contains cross linked binaries of Linux specific programs compiled and build from the respective program-specific source code.

on a Linux host, you can run `docker run alpine uname -a` with LKL-ed kernel (with Alpine Linux official image). This major focus of this project was to port dockerd daemon, which currently only supports Linux to macOS.

Currently, docker on macOS  uses guest Linux VM using Hypervisor.framework exposed by darwin kernel(macOS) to run the dockerd daemon on darwin kernel system. This hypervisor framework helps the VM to emulate a physical environment for the Linux kernel to act as an intermediate on darwin.  Our goal is to eliminate this middleware(guest VM), let the dockerd daemon communicate directly with the darwin kernel instead of running the daemon inside an isolated hypervisor providing Linux kernel architecture.


Initially on the port, learning more about the existing codebase, we realised that instead of porting each subset of features in the codebase as such, it was better to focus on the port which would let us completely execute `docker container run..` command. Because, we learned that `docker container run` has dependency over `docker create`, `docker start` and much more internals of the code. This way we don’t need to look at just one aspect of the codebase but instead port major components at one go.

To achieve this subset of the research project - the port of docker engine was divided into mainly three aspects:

1. **Operating system-level port**: The codebase of docker engine doesn’t support the direct compilation of docker engine on darwin platform. One of the tasks over this project was to extend the codebase to avoid such build/compile constraints and hence have the codebase to be platform-independent.
2. **Runtime level port**: In the codebase, there exist components which should be executed only during runtime on specific platforms. This type of constraints blocked the docker engine port to successfully run over darwin as it neglected much-required features that should also be in darwin to build/run. Our work during the phase of runtime level port focused on exposing such aspect of the codebase to darwin as well. Apart from this, one of the major goals of this phase was the streamlined integration of the code in order to get docker engine running irrespective of the platform it runs on. Since there was a particular subset of components integrated that would only work in a specific platform, such runtime level segregation helped to improve the code integration. Henceforth, this led us to include platform-specific code, yet, this integration wouldn't break the system as a whole either.
3. **The system features port:** Apart from exposing features like chroot, exposing mounting options and establishing ociSpec use for darwin the majority work for the port relied on the porting of Libnetwork, Libcontainerd, moby/buildkit modules.

**Note**: Currently, our port of docker engine is supported only over VFS via graph driver module in docker engine. 

Libcontainerd package of docker engine is a collection of gRPC client API for containerd. It initiates a gRPC client to invoke containerd process Since this package mostly handled the gRPC POST requests from the client to create, start, restart etc on the containerd process. A notable use case of libcontainerd is that at first it tries to spawn a dockerd managed containerd process. If that fails, then the only dockerd tries to spawn containerd as a different process. Most of the port here was only to attain platform independency of libcontainerd package which was Linux only and to extend it for darwin as well.

The libnetwork project of docker handles the networking of containers. The current docker libnetwork port consists of streamlined integration of darwin platform-specific code and build constraints in order to let docker engine use libnetwork APIs into the docker engine in darwin.

The buildkit API dependency of docker engine had to go through a series of changes in order to let its snapshotter control the filesystem to build the bundles properly and mount irrespective of the platform it is running upon after deflating the images. Updating the codebase of buildkit, we saw there were Linux only specific code like seccomp, speccov etc which were silently ignored over runtime while on darwin or introduced missing components in order to let docker run properly irrespective of the platform.

<center>
<img src="https://s3.amazonaws.com/media-p.slid.es/uploads/618982/images/6392798/Screen_Shot_2019-07-26_at_9.57.44_AM.png" width="500">
</center>


Another aspect of our work to port dockerd for macOS heavily relied on silently overriding the namespace and cgroups Linux only features. Containers are implemented using Linux namespaces and cgroups. Namespaces let you virtualize system resources, like the file system or networking, for each container. Cgroups provide a way to limit the number of resources like CPU and memory that each container can use. At the lowest level, container runtimes are responsible for setting up these namespaces and cgroups for containers and then running commands inside those namespaces and cgroups. Low-level runtimes support using these operating system features. 

Additionally, we added support of another dependency of `sysconf` [1] for Go, without using cgo or external binaries in libcontainer module in opencontainers/runc to get clock ticks. Which measures CPU ticks between the start and end of a process. This integration of `sysconf` would help the future of docker engine port to include system platform-independent system configuration related functions calls in APIs directly which used to come from host kernels.

After the port of dockerd on darwin, we successfully support docker container to do major functionalities like `create`, `run`, `pull` etc. 

![]()


<div class="row" align="center">
  <div class="column">
<img src="https://s3.amazonaws.com/media-p.slid.es/uploads/618982/images/6392791/Screen_Shot_2019-07-26_at_9.52.18_AM.png" width="440" height="800">
  </div>
  <div class="column">
<img src="https://s3.amazonaws.com/media-p.slid.es/uploads/618982/images/6392792/Screen_Shot_2019-07-26_at_9.52.41_AM.png" width="440" height="800">
  </div>
</div>
 

### **Work in progress**

Containerd process spawns multiple Childs as containerd-shim according to the number of containers running. Top to down, containerd initiates the call to create the containers and through this containerd-shim process, gives runU the action to create the containers.

Once runU creates the container properly and containerd is able build and handle the container, the low-level runtime runU process exits from the process chain and the container is handled by containerd-shim process alone.

That is, containerd-shim allows the runtime, runU to exit after it starts the container: This way we can run daemon-less containers because we are not having to have the long-running runtime processes for containers.

Once the `docker run` is successfully executed, ideally, containerd-shim process should exit as well. In the current scenario, it doesn’t happen. One of the reasons for this is that the filesystem implementation (mount/unmount) is not well implemented to be used in darwin and henceforth docker engine is not able to find a rootfs path to currently mount and unmount. We have landed up in a few workarounds to do this, but that is not ideal.

Apart from the `thehajime/runu-base:0.1` image we are not able to run another image, for example, an alpine image. Initially, the image as such wasn’t pulled/downloaded from the docker hub since it is unlikely to run Linux image over darwin host directly without a guest Linux VM. Currently, We have introduced a patch that would let this image to be successfully downloaded into the host system. Once the image is unpacked as bundles, docker engine fails to flatten these layers properly. We suspect this also occurs due to the inadequate implementation of graph driver in darwin. 

### **Future additions proposed**

Improvement of VFS to actually mount and unmount functionalities and the rest of the features that it offers. Along with this, maybe it should be possible to add other filesystem support as well.

Improvement on the libnetwork port. Current port of libnetwork only cares about the system platform independence while there still need to do a serious amount of work to actually use the libnetwork as a container networking platform. It would be ideal to replicate something similar to docker0 bridge which actually exists in Linux do communicate with the client and the server. 

Code refactor: There exist stub functions which would be useful if we fill it in. As well as there exists a lot of hacky workaround in the codebase. To actually able to add our work into the upstream moby repository - it would be ideal to refactor the code in a better way.

### <ins> **Reference** </ins>

1. [https://docs.docker.com/engine/reference/commandline/dockerd/](https://docs.docker.com/engine/reference/commandline/dockerd/)
2. [https://docs.docker.com/engine/docker-overview/](https://docs.docker.com/engine/docker-overview/)
3. [http://collabnix.com/how-docker-for-mac-works-under-the-hood/](http://collabnix.com/how-docker-for-mac-works-under-the-hood/)
4. [https://github.com/docker/docker.github.io/tree/master/docker-for-mac](https://github.com/docker/docker.github.io/tree/master/docker-for-mac)
5. [https://www.slideshare.net/AnilMadhavapeddy/advanced-docker-developer-workflows-on-macos-x-and-windows?ref=https://blog.docker.com/2016/05/docker-unikernels-open-source/](https://www.slideshare.net/AnilMadhavapeddy/advanced-docker-developer-workflows-on-macos-x-and-windows?ref=https://blog.docker.com/2016/05/docker-unikernels-open-source/)
6. https://ieeexplore.ieee.org/document/5541547/
7. [https://hub.docker.com/r/thehajime/runu-base](https://hub.docker.com/r/thehajime/runu-base)