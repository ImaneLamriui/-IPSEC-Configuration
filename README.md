# IPSEC-Configuration
## part 1: https://github.com/ImaneLamriui/Optimizing-Virtual-Networks-with-pfSense-Firewall
## part 2: A company has opened two new branches in other cities and wants us to connect them to the main headquarters through a secure channel. These branches also use pfSense as a firewall to manage their internal networks. The details of the new branches are as follows:

###### Branch 1:
LAN IP Addressing: 192.168.4.0/24

Public IP Address: unknown

###### Branch 2:
LAN IP Addressing: 192.168.3.0/24

Public IP Address: unknown

We need to ensure that both branches can use the accounting program and have access to the NAS.

#### Prerequisites: 
We need another pfSense machine for Branch 1, and We need to configure an additional network interface on this second pfSense machine. Additionally, the pfSense machine we configured previously will be used as the main headquarters 
