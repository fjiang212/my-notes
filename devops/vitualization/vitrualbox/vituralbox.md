# Create virtual Machine
* http://www.jeramysingleton.com/install-centos-7-minimal-in-virtualbox
* http://isoredirect.centos.org/centos/7/isos/x86_64/CentOS-7-x86_64-Minimal-1708.iso
* https://www.tecmint.com/fdisk-commands-to-manage-linux-disk-partitions
* http://software-engineer.gatsbylee.com/how-to-format-and-partition-disk-on-centos-7


# Virtual Machine network
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