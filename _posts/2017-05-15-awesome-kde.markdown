---
comments: true
layout: post
title: "Awesome::KDE Community :)"
date: "2017-05-15"
slug: "awesome_kde"
author: Aniketh Girish
project: 'KDE'
draft: false
tags:
- OSS
- KDE
---

Hey, fellow GSoCer's ;). I'm Aniketh Girish and I am working on a project for Krita this summer. What's up people, how's your community bonding period going on? I'm here to share my experience during and some tips from the past few days. Hope you all have contacted your mentors and having a good bonding with your community as well as the whole organisation. I hope all of you got a clear idea of the project and all. During the community bonding period, It is interesting to meet new people online and talk about your project and how are you going to tackle the problems. And also listen to theirs as well right? It would be good to gain knowledge in different fields and that itself inside our organisation KDE, much better, isn't it? :) and also getting to know good people who are contributing to KDE from the day KDE was evolved, getting to know their experience with the community and talk with highly skilled developers, it feels really cool. I must admit the people in our community is really helpful :). They are just happy to help you in any ways they can. You could just pop up in the respective IRC channels and pop out your questions and Vualá! there will be at least a couple of people to help you out. I would strictly advise you guys to keep everything in the public channel since most of the people won't prefer personal messages and it's good to make your community know that you are working on something good :) Hence feel free to ask any doubts you have because you will only learn by asking and sharing the knowledge.

We all need a developer access to commit right? Hope all of you guys have got that and if not please do apply for it in identity.kde.org, so that we could do our commits(PS: If only your project community asks for it, I don't know if every project community has the requirement of pushing your code yourself. For me there is). Let me share something, After getting the developer access(Yeayy!! I'm offically a KDE developer now :P) I was setting this up and was facing some issue, that I wasn't able to push it to my project branch because I was facing an error like fatal: remote error: service not enabled: /krita.git. It happened because I was trying to push it to the read-only mode of git that is anongit. We need the write mode as well for pushing it. So it would be better to do the clone like, 

```
~$ git clone kde:<repo_name> 
```

if and only if you are cloning from scratch. Else just set your URL to the ssh URL for pushing it to git. 

```
~$ git remote set-url origin ssh://git@git.kde.org/<repo_name>
```

Then just push your work in :)

I would suggest you guys have a look at the following links as well. 

[0]- https://community.kde.org/Guidelines_and_HOWTOs/Build_from_source#Git_remote_prefix

[1]- http://community.kde.org/Sysadmin/GitKdeOrgManual

Next, we would setting up your blog and link it with planet.kde.org and do blog about your project as your project community asks you to.

Whenever you are stuck, don't hesitate to ask guys, there are a lot of good helping people around who will love to help 24*7 :). Any doubts on the above mentioned, ping me no problem :)

Thanks to [Valorie](http://linuxgrandma.blogspot.in/) for helping me out on random things at times and pointing out that I should spread a word about this to everyone of us about these things and my experience with the community at the starting of the community bonding itself. Will post other experiences soon :) I will do another post, just giving my experience with the Krita team as well as how my whole journey was with KDE, from my first bug fix to KDE-SoK to giving a talk during KDE India Conference'17 and now here at GSoC'17

Cheers.