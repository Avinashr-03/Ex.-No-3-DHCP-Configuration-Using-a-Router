## Ex. No: 3  DHCP Configuration Using a Router
Date:27/10/2026
________________________________________
# Objective
To configure a router to automatically assign IP addresses to client PCs using the Dynamic Host Configuration Protocol (DHCP).
________________________________________
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Router<br>
•	1 Switch<br>
•	2 PCs<br>
•	Straight-through Ethernet cables<br>
________________________________________
# Network Topology Diagram
Description:<br>
•	PC0 and PC1 are connected to Switch0.<br>
•	Switch0 is connected to Router0 on FastEthernet0/0.<br>
•	The router acts as a DHCP server for the connected LAN.<br>
(Insert screenshot of your Packet Tracer setup here)<br>
________________________________________
# IP Addressing Table
Device	Interface	IP Address	Subnet Mask<br>
Router0	FastEthernet0/0	192.168.50.1	255.255.255.0<br>
PC0	NIC	DHCP (Auto)	Assigned by DHCP<br>
PC1	NIC	DHCP (Auto)	Assigned by DHCP<br>
DHCP Pool:<br>
•	Network Address: 192.168.50.0<br>
•	Subnet Mask: 255.255.255.0<br>
•	Default Gateway: 192.168.50.1<br>
•	DNS Server: 8.8.8.8<br>
•	Excluded IP Range: 192.168.50.1 to 192.168.50.9<br>
________________________________________
# Procedure
1.	Open Cisco Packet Tracer and add 2 PCs, 1 Switch, and 1 Router.<br>
2.	Connect both PCs to the Switch using straight-through cables.<br>
3.	Connect the Switch to Router0’s FastEthernet0/0.<br>
4.	Assign the IP address 192.168.50.1 to the router’s FastEthernet0/0 interface.<br>
5.	Enable the interface using the no shutdown command.<br>
6.	Configure the router as a DHCP server:<br>
o	Define the DHCP pool with network address, default gateway, and DNS.<br>
o	Exclude gateway and reserved addresses from the pool.<br>
7.	Set both PC0 and PC1 to obtain their IP address via DHCP (auto).<br>
8.	Verify that each PC receives an IP address dynamically.<br>
9.	Use the ping command to test connectivity between the two PCs.<br>
________________________________________
# Commands Used (Router CLI)
bash<br>
CopyEdit<br>
Router> enable<br>
Router# configure terminal<br>
Router(config)# interface fastethernet0/0<br>
Router(config-if)# ip address 192.168.50.1 255.255.255.0<br>
Router(config-if)# no shutdown<br>
Router(config-if)# exit<br>

Router(config)# ip dhcp excluded-address 192.168.50.1 192.168.50.9<br>

Router(config)# ip dhcp pool MYPOOL<br>
Router(dhcp-config)# network 192.168.50.0 255.255.255.0<br>
Router(dhcp-config)# default-router 192.168.50.1<br>
Router(dhcp-config)# dns-server 8.8.8.8<br>
Router(dhcp-config)# exit<br>
________________________________________
# Output (Screenshots)
<img width="1600" height="1000" alt="image" src="https://github.com/user-attachments/assets/4a921e21-1123-457f-8e52-cbcefa62ed75" />
<img width="1600" height="1000" alt="image" src="https://github.com/user-attachments/assets/4c2d2e11-0da5-4d36-b684-3b1d8c656fa5" />
<img width="1600" height="1000" alt="image" src="https://github.com/user-attachments/assets/6a388da8-55fa-4af4-96ea-84da3348b62c" />
<img width="1600" height="1000" alt="image" src="https://github.com/user-attachments/assets/7cafe93d-fe35-4c95-b89f-3d9ce3ddc462" />
<img width="1600" height="1000" alt="image" src="https://github.com/user-attachments/assets/4273f252-59c1-467a-bc06-ea2d2688ca1a" />
<img width="1600" height="1000" alt="image" src="https://github.com/user-attachments/assets/0f7a6aa8-30b6-4349-bad7-64e24f5d56c9" />
<img width="1600" height="1000" alt="image" src="https://github.com/user-attachments/assets/2c066004-77a9-43a2-8247-577710a881bf" />
<img width="1600" height="1000" alt="image" src="https://github.com/user-attachments/assets/e3a19bcc-1350-4aba-9fc5-459f15a05120" />
<img width="1600" height="1000" alt="image" src="https://github.com/user-attachments/assets/71ce9382-cb73-43ba-bf1a-ac83513139ce" />
<img width="1600" height="1000" alt="image" src="https://github.com/user-attachments/assets/af07cf88-0215-4b95-bb04-899bdf822d6f" />
<img width="1600" height="1000" alt="image" src="https://github.com/user-attachments/assets/249f7475-69ea-4de6-94a8-36cc87a66e89" />
![Uploading image.png…]()

________________________________________
# Result
Successfully configured a DHCP server on the router. PCs were dynamically assigned IP addresses and were able to communicate over the network.
