# IPSEC-Configuration
## part 1: https://github.com/ImaneLamriui/Optimizing-Virtual-Networks-with-pfSense-Firewall
## part 2: The company has opened two new branches in other cities and wants us to connect them to the main headquarters through a secure channel. These branches also use pfSense as a firewall to manage their internal networks. The details of the new branches are as follows:

###### Branch 1:
LAN IP Addressing: 192.168.4.0/24

Public IP Address: unknown

###### Branch 2:
LAN IP Addressing: 192.168.3.0/24

Public IP Address: unknown

We need to ensure that both branches can use the accounting program and have access to the NAS.

#### Prerequisites: 
We need anothers pfSense machines for Branch1 and branch2, and We need to configure an additional network interfaces on those pfSense machines. Additionally, the pfSense machine we configured previously will be used as the main headquarters 

### For a secure connection between pfSense machines using IPsec:
They typically need to share the same pre-shared key (PSK) or utilize a certificate-based authentication method. This key or certificate is used to establish a secure communication channel between the two devices. It ensures that only authorized devices can communicate securely with each other. So, both pfSense machines would indeed need to share the same key or have compatible certificates for IPsec to function correctly between them.
