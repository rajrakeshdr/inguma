# Inguma Package Installation Guide #

For the sake of convenience and those unfamiliar with building from source or hacking an install to make it work, we have assembled a quick installation guide. Since this information, as with the rest of the wiki, is aimed at the end-user, please do not hesitate to contact us if you feel this information is not adequately thorough. Before continuing, please be advised that this install is performed on Ubuntu and may vary from platform to platform. If anyone would like to submit a Win32 install guide for the listed packages, it would be much appreciated.

Before we continue, this is far from a universal installation guide. On GNU/Linux type systems especially, every install can be different. If you had to modify the instructions to get it to work for you, please contact us and say how you got it to work, we would love to add it to the guide to make it easier to follow. Thanks.

We will be installing the packages found on [Getting Started](IngumaGettingStarted.md) Guide so the first thing we need to is grab these packages.

```
user@host:~$ wget http://oss.coresecurity.com/repo/Impacket-0.9.6.0.tar.gz 
user@host:~$ wget http://www.lag.net/paramiko/download/paramiko-1.7.2.zip 
user@host:~$ wget http://superb-west.dl.sourceforge.net/sourceforge/pysnmp/pysnmp-2.0.9.tar.gz 
user@host:~$ sudo apt-get install python-crypto python-scapy  
user@host:~$ wget http://prdownloads.sourceforge.net/cx-oracle/cx_Oracle-4.3.1-10g-py25-1.i386.rpm
```

And yes, the last file we downloaded was a .rpm package and yes, we are still using a Debian-based OS. We'll get to that later. Please note that the supplied cx\_Oracle .rpm and the pysnmp tarball are not guaranteed to be the most recent but they should work. If you desire the newest version, please navigate to the appropriate software project sites.

## Installing Impacket ##

We'll assume that you have Impacket-0.9.6.0.tar.gz in your working directory so now we need to unpack it:

```
user@host:~$ tar -zxvf Impacket-0.9.6.0.tar.gz
```

There should now be a directory called Impacket-0.9.6.0 so let's go there and get down to business

```
user@host:~$ cd Impacket-0.9.6.0 
user@host:~$ sudo python setup.py install
```

And that should conclude your Impacket install. Again, in the even that you run into problems, either consult the mailing list/documentation for Impacket or feel free to contact us here at the Inguma Project.

## Installing Paramiko ##

Installing paramiko is about as complicated as the last install we just did (scary eh? =p).

Same as before:

```
user@host:~$ unzip paramiko-1.7.2.zip  
user@host:~$ cd paramiko-1.7.2  
user@host:~$ sudo python setup.py install
```

Assuming all went well, paramiko is now installed and functional on your system. One last time for good measure, in the even that you run into problems, either consult the mailing list/documentation for Paramiko or feel free to contact us here at the Inguma Project.

## Installing Pysnmp ##

We're going to get crazy on this one, fasten your seatbelts. ;-)

```
user@host:~$ tar -zxvf pysnmp-2.0.9.tar.gz
user@host:~$ cd pysnmp-2.0.9  
user@host:~$ sudo python setup.py install
```

Your Pysnmp should now be successfully installed.

## Installing Scapy and Python Cryptography Toolkit ##

If you haven't already:

```
sudo apt-get install python-crypto python-scapy
```

You should be now done with that part.

## Installing CX\_Oracle AND Oracle XE ##

This is the only part of the installation process that gets relatively complicated. And yes, it is a process so go get some coffee. In order to utilize Inguma's Oracle modules, you will need cx\_oracle. Before Cx\_oracle will work, it requires a working Oracle install.

One problem that many users have is getting Cx\_Oracle to recognize the Oracle Express Edition as a valid install, that is the main focus of this entire page. You will see why we grabbed the .rpm Cx\_oracle package in just a moment here but for the time being, just leave it where it is. I would like to again stress that this is install is done on a Debian-based OS. If you are installing on a Red Hat OS, from what I have read, the cx\_Oracle install is much easier.

This install requires Python version 2.5 or one that coincides with the version of the .rpm package you downloaded if you obtained one other than cx\_Oracle-4.2-10g-py25-1.i386.rpm. For more information on this topic, please see the installation note in step 2.

### Step One ###

We need to get Oracle Express Edition installed and thankfully the folks at Oracle have been kind enough to establish a repository for just that purpose, but we will need to add it.

```
user@host:~$ sudo gedit /etc/apt/sources.list
```

Note that you may substitute gedit for any editor you wish, vim, vi, emacs, etc.

Once you have your sources.list open, add the following line to the end of the file: **deb http://oss.oracle.com/debian unstable main non-free**

Save and close your sources.list file.

Next:

```
user@host:~$wget http://oss.oracle.com/el4/RPM-GPG-KEY-oracle -O- | sudo apt-key add -  
user@host:~$sudo apt-get update 
user@host:~$sudo apt-get install oracle-xe
```

In the event that these instructions do not work (may vary from system to system) please head over to this link and download the appropriate version. In most cases it will be Oracle Database 10g Express Edition (Universal) but it shouldn't make too much of a difference (I use that expression lightly). Please be advised that in order to download from that link, you will need to register and accept their license agreement, both of which are relatively quick and painless.

If you need to download the .deb package simply run:

```
sudo dpkg -i oracle-xe-universal_10.2.0.1-1.0_i386.deb
```

And all should be well. Let's move on.

### Step Two ###

We should now have our functional Oracle XE install. Let's begin the fun stuff. Assuming you have Python 2.5, we now need to create a .deb package from the .rpm we downloaded earlier. To do so change to the directory in which you grabbed that .rpm file:

```
user@host:~$ sudo alien cx_Oracle-4.2-10g-py25-1.i386.rpm
```

If all went well, you should see something along the lines of, cx-oracle\_4.2-2\_i386.deb generated.

**Note:** If you navigate to the cx\_oracle [project page](http://cx-oracle.sourceforge.net/), you will see that there are different .rpms for different python versions. For this install, we are working with Python 2.5.1 hence our reason for downloading 'Oracle 10g, Python 2.5.' **DO NOT download** the 9i or 11g based .rpms as this guide is for Oracle XE which is handled as a 10g based install.

To find out what version of Python you have, from the command line, simply run:

```
user@host:~$ python --version
```

That should tell you what version you have installed and you will need to download the appropriate .rpm. If there is no .rpm which coincides with the appropriate Python version, you will need to upgrade your version of Python.

### Step Three ###

With our alien converted .deb package and a functional Oracle XE install, it is now time to continue.

We need to grab up some more stuff (in case you don't have it already)

```
user@host:~$ sudo apt-get install libc6-dev
```

### Step Four ###

In the event that you are compiling from source (which will be covered in future revisions), in your working directory, you will need to change some environmental variables.

```
user@host:~$ export ORACLE_HOME=/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/  
user@host:~$ export LD_LIBRARY_PATH=$ORACLE_HOME/lib  
user@host:~$ export PATH=$ORACLE_HOME/bin:$PATH
```

If you are having a ton of fun, you will be happy to know that we aren't done just yet. =p

### Step Five ###

This is the home stretch. In the event that everything has gone well up until now, you should know that you will be especially pissed off if something fails in these final steps.

```
user@host:~$ sudo gedit /etc/ld.so.conf
```

This should bring up your ld.so.conf file. Add the line: **/usr/lib/oracle/xe/app/oracle/product/10.2.0/server/lib** to the end of the file. Close and save.

### Step Six ###

Lastly, we **should** be able to install that .deb package. So change to the directory where that .deb (converted from .rpm) exists and run:

```
user@host:~$ sudo dpkg -i oracle-xe-universal_10.2.0.1-1.0_i386.deb
```

You can now check Synaptic or search within apt-get to find out of the cx\_oracle package sucessfully installed. Change to your inguma directory and run:

```
sudo ./inguma.py
```

Another great way to verify your Oracle XE/CX\_oracle install well is to import cx\_oracle into Python. To do this:

```
user@host:~$ python
Python 2.5.1 (r251:54863, Mar  7 2008, 04:10:12) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>
```

And from your Python prompt

```
>>> import cx_Oracle
```

If nothing is returned on the below line, all is well (at least it should be). Please be aware that importing cx\_Oracle is case sensetive and it must be called with a capital O. If your cx\_Oracle install was unsuccessful, you will see something like this:

```
>>> import cx_oracle
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named cx_oracle
```

If all went well, you will no longer recieve an error message saying that no module named cx\_oracle could be found.