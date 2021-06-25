---
comments: true
layout: post
title: "[GNU-Wget2] GSoC'18: DNS-over-HTTPS"
date: "2018-04-25"
slug: "gsoc_18_doh"
author: Aniketh Girish
project: 'GSoC'
tags:
- GSoC
- OSS
- Wget2
---

Hey folks,

Again, cheers to another fantastic summer coming up next :D.

A few days before, or better to be - 2 months before, I started to contribute towards GNU project and specifically to Wget2. To be honest, I could say that the exposure towards it and learning exposure I received by just submitting a few patches and researching about the GSoC project was tremendously huge.

By this time I hope you all understood that I got in as a student developer Intern with Google Summer of Code, again!!

This is just an introductory post, further details and others will be following this as soon as possible according to the way I would be able to accommodate my schedule. Since this summer is going to be tight as hell. (Will let you know why later :P).

Basically, my project for wget2 in GNU project is to provide support for a DNS resolver over HTTP with SSL verification, that is, DNS-over-HTTPS. For that, I would be implementing the whole DNS packet acquiring and everything from scratch since Wget2 doesn't have support for it.  On an overview, I will be implementing DNS packets, IPv4, IPv6, DNS-SD, EDNS and much more.

DNS over HTTPS is a web protocol that argues for sending DNS requests and receiving DNS responses via HTTPS connections, hence providing query confidentiality. DoH provides more than just privacy – it also helps guarantee the integrity of the response users receives to their requests. Because the DNS response is invisible between responder and user, ISPs and others in the end-to-end network chain can't interfere in the responses.

Henceforth, we provide a plan for a new implementation of a parsing DNS over HTTPS. In the process, we would create a new library to handle DNS resolution. Further, we provided added support for handling IPv4 and IPv6 DNS packets as well as support for EDNS. The integration with HTTP provides a transport suitable for traditional DNS clients seeking access to the DNS. In the end, our client will be capable of sending DNS queries and getting DNS responses over HTTP using https:// and implies TLS security integrity and confidentiality.

Furthermore, we plan to provide support for DNS Service Discovery which is a way of using standard DNS programming interfaces, servers, and packet formats to browse the network for services.

That would be it for this time folks, will get back to you with further details and updates regularly from now onwards.

You can read the full [GSoC proposal here](https://docs.google.com/document/d/1B3j9Z11iPSoN5XshYJr1Jc7kxlgD6AY3D8v4YPBAXKc/edit?usp=sharing) if someone wishes to see it and if somebody is familiar with DNS-over-HTTPS implementation, please do feel free to ping me and help me out with your valuable suggestions :)

Cheers.