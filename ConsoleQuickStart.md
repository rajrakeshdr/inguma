# Console UI Quick Start #

While the goal of inguma is not complexity and obscurity, it may not be intuitive to all at first glance. The goal of this page is to demonstrate various usages of Inguma and its functions so that the user feels at ease delving deeper into the robustness of the application. This will most likely be a continuous work in progress so please do not hesitate to refer to this page often.

After obtaining the required dependencies as noted on **Getting Started**, you are set to run Inguma. Please be advised that Inguma _must be run as **root**_ or with superuser privileges (`*`nix based systems) in order to utilize it's full capabilities. For the curious, this is necessary as certain functions require raw sockets and other goodies which are often restricted by user and/or group rights. As the [PyGtk GUI](PyGtkQuickStart.md) is currently less than stable, this usage overview will be handled through the CLI. Be aware that all instructions are relative to your OS outside of the inguma environment, when working from the _inguma>_ prompt you should be able to follow these examples verbatim without error. This tutorial also assumes you are smart enough to make it this far so if finding out whether or not a port is NAT'ed means nothing to you then prepare for a serious learning curve with the program's more robust functions.

## Starting Inguma ##

Unless you have created a symlink for inguma, we will assume that it will be executed as a python script from the working directory.

```
user@host:~/inguma$ sudo ./inguma.py
Inguma Version 0.0.6
Copyright (c) 2006, 2007 Joxean Koret <joxeankoret(AT)yahoo(DOT)es>

inguma>
```

As with any application, referring to the program's help manual always eases learning. When working with Inguma, the help option can be accessed from almost any prompt. As we move through the tutorial you will see that our prompts may change depending on which module we are using.

## Using Inguma ##

Inguma's module layout can be thought of as sequential with regard to execution. It is for this reason that we will first work with the discover modules. Before continuing it must be stressed that various modules _should only be exercised on systems **you have permission** to target_. Auditing systems that you are not authorized to work on most likely breaks quite a few laws and could land you in an unfortunate predicament. With that out of the way, let's continue our tutorial.

While the importance of the discover modules is not to be diminished, it is safe to assume that you most likely have a target as well as some prerequisite information about that target. With that in mind, we will move to the gather modules.

The gather modules serve to collect information about your target so that you can better evaluate its security. One of the most basic and useful gather modules is portscan. Let's run a **portscan** on the machine we wish to check.

```
inguma> target = "uberserver.com" 
inguma> show options
inguma> scanType = "S" 
Options

Target:               uberserver.com
Port:                 0
Covert level:         0
Timeout:              1
Wait time:            0.1
Wizard mode:          False
```

Note the use of the **show options** command. This is helpful in case you somehow manage to forget what the hell it was you were doing or to verify your target parameters. We also set **scanType = "S"**. This sets our portscan as a SYN scan as opposed to ACK, XMAS, TCP, etc.

```
inguma> portscan
Portscan results

Port 80/www is opened at uberserver.com
Port 7777 is opened at uberserver.com
Port 8080/webcache is opened at uberserver.com
Port 21/ftp is opened at uberserver.com
Port 9090 is opened at uberserver.com
```

Now that we know what ports are open on our target, we may want to refer to a discover module, **isnated**. Isnated does what the name implies, finds out whether or not the specified port is NATed.

```
inguma> port = 80
inguma> isnated
Port 80 is NOT NATed
inguma>
```

We have now established that port 80 is not nated, the next thing we want to do is to gather information about the service running on port 80. For this we will utilize the gather module, identify.

```
inguma> port = 80
inguma> identify
Port 80 :  Apache/2.2.4 (Ubuntu) DAV/2 SVN/1.4.4 mod_perl/2.0.2 Perl/v5.8.8
```

This is currently where the tutorial ends. It does not delve into the program's exploitative capabilities and payloads. This is done under the assumption that if you have made it this far, you know what to do next. In the event that you find yourself stuck, you can always refer to the source code or the help command. As noted above, whenever your Inguma prompt changes, i.e. **inguma>** to **SNIFFER>**, there will be a help command displaying any/all available options.

Thank you for using Inguma!