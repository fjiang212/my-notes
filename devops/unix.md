# Unix Basic
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