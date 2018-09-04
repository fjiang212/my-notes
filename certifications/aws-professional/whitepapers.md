# Amazon VPC Connectivity Options
## Network-to-Amazon VPC Connectivity Options
* **Hardware VPN**: Virtual private Gateway->VPN connection->Customer Gateway
* **AWS Direct Connect**:  Virtual private Gateway->VLAN#1->AWS Direct Connect>Customer WAN
* AWS Direct Connect + VPN:
* AWS VPN CloudHub: Virtual private Gateway->VPN connections->Multiple Customer Gateway in different location
* Software VPN: Software VPN appliance->Internet Gateway->VPN connection->Customer VPN endpoint

## Amazon VPC-to-Amazon VPC Connectivity Options
* **VPC Peering**:
* Software VPN: Software VPN appliance->Internet Gateway->VPN connection->Internet Gateway->Software VPN appliance
* Software-to-Hardware VPN:Virtual private Gateway->VPN connections->Software VPN appliance
* Hardware VPN:Virtual private Gateway->VPN connection->Customer Gateway->VPN connection->Virtual private Gateway
* AWS Direct Connect:Virtual private Gateway->VLAN#1->AWS Direct Connect>VLAN#2->Virtual private Gateway

## Internal User-to-Amazon VPC Connectivity Options
* Software Remote-Access VPN: ->Interget Gateway->Remote Access Server(in VPC)

# Using AWS for Disaster Recovery
## Disaster Recovery Scenarios with AWS
* Backup and Restore
* Pilot Light for Quick Recovery into AWSEC2
* Warm Standby Solution in AWS
* Multi-Site Solution Deployed on AWS and On-Site
* AWS Production to an AWS DR Solution Using Multiple AWS Regions


