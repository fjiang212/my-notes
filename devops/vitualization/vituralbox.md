# Architecture and 
![alt text](images/virtualbox_architecture.PNG)

# Key concepts

# Components
## Virtual Machine network
https://www.virtualbox.org/manual/ch06.html
 
| | VM <--> Host | VM1 <--> VM2 | VM --> Internet | VM <-- Internet |
| :---: | :---: | :---: | :---: | :---: |
| Host-only | + | + | - | - |
| Internal | - | + | - | - |
| Bridged | + | + | + | + |
| NAT | - | - | + | [Port forwarding](https://www.virtualbox.org/manual/ch06.html#natforward) |
| NAT Network | - | + | + | [Port forwarding](https://www.virtualbox.org/manual/ch06.html#network_nat_service) |

ake a look: http://www.fixedbyvonnie.com/2014/11/virtualbox-showing-32-bit-guest-versions-64-bit-host-os/

If VirtualBox is only showing 32-bit versions in the Version list make sure:

You have an x64 CPU installed. (Optimally, a 64-bit OS should also be installed to receive acceptable virtualization performance.)
Hardware virtualization is enabled in the BIOS. (Your CPU must support it.)
For Intel x64: VT-x (Intel Virtualization Technology) and VT-d are both enabled
For AMD x64: AMD SVM (Secure Virtual Machine) is enabled
Hyper-V (or any other form of bare-metal hypervisor) is not installed

# Virtual machines

## Base Virtual machine (CentOS_Base)
* Install Oracle Virtual Box (Repair with "Run as Administration" if 64bit os not found)
* [Install CentOS 7(User: vagrant/vagrant)](http://www.jeramysingleton.com/install-centos-7-minimal-in-virtualbox)
* Install additional software

```

```


# Q & A
* How to Change the hot key?
input -> keyboard -> keyboard settings

# References
* https://www.tecmint.com/fdisk-commands-to-manage-linux-disk-partitions
* http://software-engineer.gatsbylee.com/how-to-format-and-partition-disk-on-centos-7
