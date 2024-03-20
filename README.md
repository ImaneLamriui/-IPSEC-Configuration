## IPsec-_Configuration_
### part 1: https://github.com/ImaneLamriui/Optimizing-Virtual-Networks-with-pfSense-Firewall  IP-Firewall: 192.168.3.129 (the main headquarters)
### part 2: The company has opened two new branches in other cities and wants us to connect them to the main headquarters through a secure channel. These branches also use pfSense as a firewall to manage their internal networks. The details of the new branches are as follows:

<p align="center">
<img src="https-IP.png" align="center"  width="400">

###### Branch 1:
__LAN__ IP Addressing: __192.168.4.0/24__

Public IP Address: unknown

###### Branch 2:
__LAN__ IP Addressing: __192.168.3.0/24__

Public IP Address: unknown

###### My sOurce address setted automatically by DHCP (WAN):
 __192.168.1.118__
 
We need to configure the network in such a way that both branches can use __the accounting program__ and have access to __the Network Attached Storage (NAS)__ to meet the operational requirements of the company.
<p align="center">
<img src="WAN-and-LAN-branch1-Network-4-firwall-config.png" align="center"  width="400">


##### Prerequisites: 
We need additional pfSense appliances for each branch. Each branch would typically require its own pfSense firewall to manage its network and establish secure connections back to the main headquarters or other branches. 
Each pfSense device would then be configured to connect securely to the central location or other branches using VPN technologies like IPsec or OpenVPN. This allows for secure communication between all branches while providing __centralized management__ and security policies from __the main headquarters__,so,  We need to configure an additional network interfaces on those pfSense machines. 
Additionally, the pfSense machine we configured previously will be used as __the main headquarters__ on __part1__(Mentioned at the top of the document)

##### For a secure connection between pfSense machines using IPsec:
They typically need to share the same pre-shared key (PSK) or utilize a certificate-based authentication method. This key or certificate is used to establish a secure communication channel between the two devices. It ensures that only authorized devices can communicate securely with each other. So, both pfSense machines would indeed need to share the same key or have compatible certificates for IPsec to function correctly between them.

<p align="center">
<img src="remote-network-and-encryption-algorithms.png" align="center" width="400" height="300">

pfSense can generate strong pre-shared keys (PSKs) automatically, which simplifies the configuration process and ensures security. 
In this case I have used ths method to establish a secure IPsec connection __successfully__:
##### Press the 'Connect' button in the pfSense status section.:

<p align="center">
<img src="connect-firewall.png"  width="400">

##### estabilished connection successfully:

<p align="center">
<img src="Established-connection.png" align="center"  width="400">

##### Then, we will see one activated tunnel displayed on the dashboard status
<p align="center">
<img src="Status-Dashboard-active-tunnels.png.png" width="400">

##### pfsence Configuration
When the initial installation is complete, reboot the machine, immediately halt the process, and proceed to delete the ISO file from the SATA. Additionally, disconnect the ISO from the controller in the VirtualBox configuration. This will prevent the ISO from reinstalling every time the pfSense machine starts.

<p align="center">
<img src="prevent the ISO from reinstalling every time the pfSense machine starts.png"width="400">

#### _Conclusion_:

#### -In this task, we have proceeded to:
###### -Create network interfaces (configure WAN and LAN).
###### -Define security policies.
###### -Configure firewall rules.
###### -Testing the connection functionality after completing the configurations: verifying connectivity between the branches, ensuring that security policies are functioning as expected, and confirming that services such as access to the local network and shared resources are available from remote branches.

<p align="center">
<img src="pfsense-group.png" width="400">

On __part 3__ I will configure the other LAN 192.168.3.0, we have it on the same red of the firewall 192.168.3.129, this will generate conflits, we must do some configuration changes to establish this remote LAN : 192.168.3.0
The main issue here is that both the IP address of __the main firewall__ (192.168.3.129) and __the network address of Branch 2's LAN__ (192.168.3.0/24) share __the same network prefix__ (192.168.3). This can lead to addressing conflicts and network confusion.
When a device in the 192.168.3.0/24 network needs to communicate with the main firewall (whose IP address is 192.168.3.129), it may encounter conflicts because it won't know whether the IP address belongs to a host in the network or to the firewall itself.

To avoid this problem, __one solution__ would be to change the IP address of the main firewall to an address that is outside the range of addresses used in my network, as mentioned earlier. This ensures that there is no overlap in network prefixes and prevents __ addressing conflicts__.
Additionally, ensuring that any firewall rules or routing configurations on the main firewall are updated to reflect the new IP address.
