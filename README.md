## Ex. No: 5  VLAN Configuration Using a Managed Switch
Date:
________________________________________
# Objective
To configure Virtual Local Area Networks (VLANs) on a managed switch and verify that hosts within the same VLAN can communicate while others cannot.
________________________________________
# Apparatus/Tools Required
•	Cisco Packet Tracer<br>
•	1 Managed Switch (e.g., 2960)<br>
•	4 PCs<br>
•	Straight-through Ethernet cables<br>
________________________________________
# Network Topology Diagram
Description:<br>
•	PC0 and PC1 are assigned to VLAN 10.<br>
•	PC2 and PC3 are assigned to VLAN 20.<br>
•	All PCs are connected to different ports on the same switch.<br>
(Insert screenshot of your Packet Tracer setup here)<br>
________________________________________
# IP Addressing Table
Device	VLAN	IP Address	Subnet Mask	Port<br>
PC0	10	192.168.10.1	255.255.255.0	FastEthernet0/1<br>
PC1	10	192.168.10.2	255.255.255.0	FastEthernet0/2<br>
PC2	20	192.168.20.1	255.255.255.0	FastEthernet0/3<br>
PC3	20	192.168.20.2	255.255.255.0	FastEthernet0/4<br>
________________________________________
# Procedure
1.	Open Cisco Packet Tracer and add 4 PCs and 1 Switch.<br>
2.	Connect PC0–PC3 to switch ports FastEthernet0/1 to FastEthernet0/4 respectively.<br>
3.	Assign static IP addresses to each PC as per the IP table.<br>
4.	Enter the Switch CLI and create two VLANs:<br>
o	VLAN 10 for PC0 and PC1<br>
o	VLAN 20 for PC2 and PC3<br>
5.	Assign the respective switch ports to their VLANs.<br>
6.	Use the ping command from PC0 to PC1 (should succeed).<br>
7.	Try pinging from PC0 to PC2 (should fail — different VLANs).<br>
________________________________________
# Commands Used (Switch CLI)
bash<br>
CopyEdit<br>
Switch> enable<br>
Switch# configure terminal<br>

Switch(config)# vlan 10<br>
Switch(config-vlan)# name STAFF<br>
Switch(config-vlan)# exit<br>

Switch(config)# vlan 20<br>
Switch(config-vlan)# name STUDENTS<br>
Switch(config-vlan)# exit<br>

Switch(config)# interface range fastethernet0/1 - 2<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 10<br>
Switch(config-if-range)# exit<br>

Switch(config)# interface range fastethernet0/3 - 4<br>
Switch(config-if-range)# switchport mode access<br>
Switch(config-if-range)# switchport access vlan 20<br>
Switch(config-if-range)# exit<br>
________________________________________
# Output (Screenshots)
# VLAN configuration on switch<br>
<img width="872" height="777" alt="Screenshot 2026-10-28 185200" src="https://github.com/user-attachments/assets/3150fcf0-6789-4b83-914f-b709e07d02b8" />
<img width="880" height="780" alt="Screenshot 2026-10-28 185238" src="https://github.com/user-attachments/assets/36b3316d-e566-41a0-b314-3b5616c8ca76" />

# PC IP settings<br>
<img width="796" height="190" alt="Screenshot 2026-10-28 184320" src="https://github.com/user-attachments/assets/f707eb72-5dfd-4f04-9928-2db3a5fd9a4a" />
<img width="792" height="177" alt="Screenshot 2026-10-28 184236" src="https://github.com/user-attachments/assets/1a9fa097-ec17-410f-ae4c-76ed929a74a3" />
<img width="792" height="177" alt="Screenshot 2026-10-28 184206" src="https://github.com/user-attachments/assets/81456eec-c799-4e2c-aa03-531477767e1a" />
<img width="792" height="177" alt="Screenshot 2026-10-28 184130" src="https://github.com/user-attachments/assets/5f486375-a4ef-4b24-9a6d-6fe6deaec80e" />

# Successful ping between PCs in the same VLAN<br>
<img width="1916" height="1017" alt="Screenshot 2026-10-28 184004" src="https://github.com/user-attachments/assets/2e35f5ba-90c1-4010-b23e-318e46034a2f" />
•	Failed ping between PCs in different VLANs<br>
<img width="702" height="629" alt="image" src="https://github.com/user-attachments/assets/b147e54b-50bd-464c-8ef2-fad19cee6527" />
________________________________________

# Result
Successfully created and configured VLANs on a managed switch. Verified that only PCs within the same VLAN could communicate with each other.

