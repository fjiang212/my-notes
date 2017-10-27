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

