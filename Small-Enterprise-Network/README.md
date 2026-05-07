# Small Enterprise Network (GNS3)

## Overview
This project simulates a small enterprise network.

## Objectives
 - VLAN segmentation
 - Inter-VLAN routing
 - Port-security
 - OSPF configuration
 - NTP configuration
 - DHCP configuration
 - Dynamic NAT/PAT configuration
 - SSH access

## Topology
Topology diagram located in '/topology'.

## Network Design
This project simulates a small enterprise network consisting of three departments HR, engineering (Eng), and marketing (Mark).

The design is simplified and allows for scalability:
 - Access layer: Layer 2 switches provide VLAN segmentation
 - Core layer: Default gateway configured as ROAS for inter-VLAN routing; router as DHCP and NTP server; edge router for NAT and internet access 
 - Management access: SSH enabled on all devices (excluding R1 and ISPRouter), via VLAN 100 for switches; R1 used to SSH to network devices, due to vPC limitations

VLAN segmentation for logical seperation of departments:
 - VLAN 10: HR
 - VLAN 20: Engineering (Eng)
 - VLAN 30: Marketing (Mark)
 - VLAN 100: Management (Mgmt)

Additional design elements:

 - Inter-VLAN routing performed using ROAS configuration
 - OSPF implemented for dynamic routing
 - SSH for secure remote device management
 - Port security enabled on switch interfaces connected to end users
 - NTP to synchronize network device clocks
 - DHCP for dynamic IP assignment to end users
 - NAT/PAT for public-to-private (and vice-versa) IP translation

## IP Adressing Scheme
HR - VLAN 10 - subnet 10.10.10.192/29
Eng - VLAN 20 - subnet 10.10.10.128/26
Mark - VLAN 30 - subnet 10.10.10.0/25
Mgmt - VLAN 100 - subnet 10.10.100.0/24
Router interconnections - subnet 10.10.10.200/30, subnet 10.10.10.204/30
Edge to ISP router - subnet 50.50.50.0/29
ISP internet access - IP 8.8.8.8

## Configurations
Configurations are located in '/config'.

## Requirements
GNS3 version 2.2.58.1
GNS3 VM via VMware Workstation

Cisco virtual router (QEMU):
 - Appliance: cisco-iosv
 - Image: vios-adventerprisek9-m.spa.159-3.m6.qcow2
Cisco virtual switch (QEMU):
 - Appliance: cisco-iosvl2
 - Image: vios_l2-adventerprisek9-m.SSA.high_iron_20180619.qcow2

Hardware requirements:
 - 8 GB RAM minimum
 - 4+ CPU cores

## How to run
1. Import 'Small Enterprise Network.gns3'
2. Import appropriate appliances and attach appropriate images
3. Start devices
4. (Optional) Use R1 to SSH to network devices

## Credentials
Credentials for all devices. No credentials needed for ISPRouter. 
 - Priv exec mode secret: cisco
 - Username: admin
 - Secret: cisco