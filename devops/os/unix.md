# Table of Contents
1. [Unix Basic](#unix-basic)
2. [Unix Commands](#unix-commands)
3. [Solaris](#solaris)


# Unix Basic
## The Difference Between Fedora, Redhat, and CentOS
* **Fedora** is the main project, and it’s a communitity-based, free distro focused on quick releases of new features and functionality.
* **Redhat** is the corporate version based on the progress of that project, and it has slower releases, comes with support, and isn’t free.
* **CentOS** is basically the community version of Redhat. So it’s pretty much identical, but it is free and support comes from the community as opposed to Redhat itself.

## EPEL
EPEL (Extra Packages for Enterprise Linux) is open source and free community based repository project from Fedora team which provides 100% high quality add-on software packages for Linux distribution including RHEL (Red Hat Enterprise Linux), CentOS, and Scientific Linux. 
https://www.tecmint.com/how-to-enable-epel-repository-for-rhel-centos-6-5/

## How to set environment variable for everyone under my linux system?
When bash is invoked as an interactive login shell, or as a non-interactive shell with the --login option, it first reads and executes commands from the file /etc/profile, if that file exists. After reading that file, it looks for ~/.bash_profile, ~/.bash_login, and ~/.profile, in that order, and reads and executes commands from the first one that exists and is readable. The --noprofile option may be used when the shell is started to inhibit this behavior.
...
When an interactive shell that is not a login shell is started, bash reads and executes commands from /etc/bash.bashrc and ~/.bashrc, if these files exist. This may be inhibited by using the --norc option. The --rcfile file option will force bash to read and execute commands from file instead of /etc/bash.bashrc and ~/.bashrc.

## How to change default jdk in unix
[root@localhost ~]# /usr/sbin/alternatives  --config java
There are 3 programs which provide 'java'.

```
  Selection    Command
-----------------------------------------------
*+ 1           /usr/lib/jvm/jre-1.7.0-openjdk.x86_64/bin/java
   2           /usr/lib/jvm/jre-1.6.0-openjdk.x86_64/bin/java
   3           /usr/java/jdk1.8.0_92/jre/bin/java
  
Enter to keep the current selection[+], or type selection number: 3
```

```
[root@localhost ~]# java -version
java version "1.8.0_92"
Java(TM) SE Runtime Environment (build 1.8.0_92-b14)
Java HotSpot(TM) 64-Bit Server VM (build 25.92-b14, mixed mode)
```

## Unix File descriptor
2>&1
 
File descriptor 0 is the standard input (stdin).
File descriptor 1 is the standard output (stdout).
File descriptor 2 is the standard error (stderr).
 
 
Here is one way to remember this construct (although it is not entirely accurate): at first, 2>1 may look like a good way to redirect stderr to stdout. However, it will actually be interpreted as "redirect stderr to a file named 1". & indicates that what follows is a file descriptor and not a filename. So the construct becomes: 2>&1.

# Unix Commands
## How to check java default option
```
java -XX:+PrintFlagsFinal –version
```
How to check Unix version
```
cat /etc/*lease
```

## How to check what process has open linux port
http://www.cyberciti.biz/faq/what-process-has-open-linux-port/

## How to use tee command
```
ls -al 2>&1 |tee output.log
```
tee program will send its standard input to its standard output (like cat) and also to the file

## Use the chkconfig Utility
*	To display a list of system services (services from the /etc/rc.d/init.d/ directory, as well as the services controlled by xinetd), either type chkconfig --list, or use chkconfig with no additional arguments.
  
*	To enable a service in runlevels 2, 3, 4, and 5, type the following at a shell prompt as root:
```
chkconfig service_name on
chkconfig service_name off
chkconfig service_name --del
```

## How to setup rsyslog forward
*	Find out the location of syslog config
```
ls -d /etc/*syslog* 
```

*	Edit syslog config forward
* Restart service
```
sudo service rsyslog restart
```

## How to check rsyslog version
```
rsyslogd -c5 -N6 | head -10
```

## How to change max open files
https://www.ibm.com/support/knowledgecenter/en/SSPT3X_2.1.2/com.ibm.swg.im.iis.productization.iisinfsv.install.doc/topics/t_configuring_nprocnofiles.html
*	Change /etc/security/limits.conf
*	Change /etc/security/limits.d/90-nproc.conf/90-nproc.conf 

## How to create multiple directories or files

```
mkdir -p {network, compute, storage}
touch {network, compute, storage}/{main.tf, variables.tf, output.tf}
```
# Solaris
## Commands
* Solaris management console
	```
  Smc &
	```
* SMF Commands: SMF has a limited yet powerful set of commands. Each command has several options which cover the tasks required to manage Solaris systems. The following table lists the SMF commands.
http://www.oracle.com/technetwork/server-storage/solaris/overview/servicemgmthowto-jsp-135655.html

```
svcs -l rsyslogd
svcs -a
Svcadm enable  
```

## Solaris syslogd limitation	
* Syslogd can only forward to remote host with default port 514 (check man syslog.conf in solaris 10)
* Syslogd can only forward to remote host with UDP(check man syslog.conf in solaris 10)
* Syslogd can not forward non-syslog files

## Install rsyslog in solaris
* Check service
```
svcs -a|grep log
```
* Installation
    * Solaris 10: https://www.opencsw.org/package/rsyslog/
    * Solaris 11: http://www.c0t0d0s0.org/archives/7631-Less-known-Solaris-11.1-features-rsyslog.html
* Disable default syslog:    svcadm disable svc:/system/system-log:default
* Enable rsyslog
```
Check if rsyslog is running or not: ps -ef|grep rsyslog, if it is running 
    $ kill it
    $ syslog: svcadm disable svc:/network/csw/rsyslogd:default
Enable  rsyslog: svcadm enable  svc:/network/csw/rsyslogd:default
Check service again: svcs -a|grep log to make sure rsyslog is online and rsyslog process is running
```	
* Config rsyslog
```	
mkidr /etc/rsyslog.d
Edit /etc/opt/csw/rsyslog.conf
$IncludeConfig /etc/rsyslog.d/
```
