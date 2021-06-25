---
comments: true
layout: post
title: "Kick Starter: How to Start contribution to KDE."
date: "2017-05-17"
slug: "start_contributing_to_kde"
author: Aniketh Girish
project: 'Tutorials'
tags: 
- KDE
- OSS
---

Basically, to fix bugs or to make contributions to a codebase, you are first required to build the application from source as not to make any problems in the existing code base. Obviously, you need to fetch the source first, which you can get by browsing through cgit.kde.org Once you have the source, you're required to build the code that you just fetched/cloned. KDE projects make use of CMake - a cross-platform makefile generator.

So, to build an application, you can either follow the instructions given in the README or INSTALL files inside the repository. Usually, this involves the following steps:


``` bash
~$ cd "your-source-code-directory"
~$ mkdir build cd build cmake .. (don't forget the dots! )
~$ make -j"no of processors -1" (eg: make -j5) ​
~$ make install
```

​What happens when you follow these set of commands is that ​your application is compiled and the build files, i.e the output of the compilation stage are left inside the build folder you just created.

Now in the last step, i.e when you run "make install", all your build output is put in the right place, so as to get picked up at the time you launch your application. This is by default in /usr/bin or so.

So when any file needs to be moved to / prefix, it requires you to authenticate with "sudo" and it's not advisable to install any application to a / prefix.

If you haven't followed the above, don't worry. Just remember, try NOT to use "sudo" in any commands you might use while building your applications.

​So what is the workaround for this? Whatever you build needs to be put(or installed) to a place from where your system can pick it up on runtime(i.e when you launch any app).​ For this purpose, it is suggested that you always install any application which you build from source to a custom prefix. In my case, development environment looks like this:

![devel](https://anikethgirish.files.wordpress.com/2017/05/devel.png)

so when you configure your prefix properly, instead of installing to /usr, your build outputs would be installed to ~/devel/install/ and for this, you do not need to use "sudo" anywhere. The whole idea is that if something were to go wrong with an executable or if while installing, some configurations get altered your system wide configurations shouldn't get affected(i.e configs in / prefix).

​​So in my case, I intend to install to ~/devel/install and I clone my source codes inside ~/devel/src folder. Once you have this directory structure, to make things simple for you, add this in bashrc or zshrc according to which bash you are using. 

``` bash
export KDE_SRC=/home/aniketh/devel/src 
export KDE_BUILD=/home/aniketh/devel/build 
export KDE_INSTALL=/home/aniketh/devel/install 
#export QTDIR=/usr export KF5=$KDE_INSTALL
export PATH=$KF5/bin:$PATH export XDG_DATA_DIRS=$KF5/share:$XDG_DATA_DIRS 
export XDG_CONFIG_DIRS=$KF5/etc/xdg:$XDG_CONFIG_DIRS:/etc/xdg:/usr/local/etc/xdg 
export QT_PLUGIN_PATH=$KF5/lib64/plugins:/usr/local/lib64/plugins:$QT_PLUGIN_PATH 
export QML2_IMPORT_PATH=$KF5/lib64/qml:$KF5/lib/x86_64-linux-gnu/qml:/usr/local/lib64/qml:$QML2_IMPORT_PATH 
export QML_IMPORT_PATH=$QML2_IMPORT_PATH:$QML_IMPORT_PATH 
export CMAKE_PREFIX_PATH=$KF5:$CMAKE_PREFIX_PATH 
export KDEDIRS=$KDE_INSTALL:$KDEDIRS export LD_LIBRARY_PATH=$KDE_INSTALL/lib64:$LD_LIBRARY_PATH 
export PKG_CONFIG_PATH=/usr/lib/pkgconfig:$KDE_INSTALL/lib64/pkgconfig:/usr/share/pkgconfig:$PKG_CONFIG_PATH 
export KDE_INTEGRATION="true"
```

You just need to open the terminal and write down.

``` bash
~$ vim .zshrc or .bashrc
```

You can use any of the text editors and add the variables.

So, the obvious thing to do here would be to add a command to your .bashrc or .zshrc which would source the environment variables in your script on every session's startup. (This is what we have done, instead of writing down the whole set of the environment variable in a file and source it every time. So rather doing this we have initialised it once and no more we have to worry about that).

Once you've done this, to build any application, you will need to do just the following: 

``` bash
cmake -DCMAKE_INSTALL_PREFIX=$KDE_INSTALL .. 
make -j"no_of_processors" 
make install
```

That's it really. When we run the cmake command, it is obvious that we would encounter with error messages saying that some API’s needed for the project is missing, hence we will have to find the package which is missing.

The best way to do that is to give a search in the apt cache. 

``` bash
~$ apt-cache search package_name
```
After that run the cmake again till you get the configuration is done.

Hence that it, we will get the project up and running. If you encounter with other problems please feel free to contact me :)

Cheers.