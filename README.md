<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Create our Resources
- Create our Virtual Machines
- Use Wireshark to Observe Traffic between the Two VMs

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/X4eEgoS.png" height="80%" width="80%" alt="Creating Resource Groups"/>
</p>
<p>
<b>- Search for Resource Groups in the Search Bar
</p>- Create a new Resource Group for the networking lab
</p>
<br />

<p>
<img src="https://i.imgur.com/QbR1hQm.png" height="80%" width="80%" alt="Creating Virtual Machines"/>
</p>
<p>
<b>- Search for Virtual Machines in the Search Bar
</p>- Create Two Virtual Machines. The first one should run on Windows 10 and the other is Ubuntu
</p>
<br />

<p>
<img src="https://i.imgur.com/Vb09xdp.png" height="80%" width="80%" alt="Network Watcher Topology"/>
</p>
<p>
<b>- Search up Network Watcher and open the corresponding network watcher and observe the Topology
</p>
<br />

<p>
<img src="https://i.imgur.com/x6sE9Cb.png" height="80%" width="80%" alt="Connect to Virtual Machine"/>
</p>
<p>
<b>- Copy the Public IP Address of VM1 and use Remote Desktop to remote into the Virtual Machine
</p>
<br />
  
<p>
<img src="https://i.imgur.com/I7Umut8.png" height="80%" width="80%" alt="Downloading Wireshark"/>
</p>
<p>
<b>- Open the Internet Browser and install <a href="https://2.na.dl.wireshark.org/win64/Wireshark-win64-4.0.3.exe">WireShark 
</p>
<br />
  
<p>
<img src="https://i.imgur.com/6kmpr5Z.png" height="80%" width="80%" alt="Using Wireshark"/>
</p>
<p>
<b>- Open Wireshark and double click the ethernet to select it
</p>- Type in "icmp" to filter only icmp traffic
</p>- Ping the Private IP of VM2 thorugh powershell
</p>- Observe as icmp traffic begins to fill the screen of Wireshark
</p>
<br />

<p>
<img src="https://i.imgur.com/ZnYwGZk.png" height="80%" width="80%" alt="Firewalls and Wireshark"/>
</p>
<p>
<b>- Ping the Private IP of VM2 (ping -t)
</p>- Navigate to Network Security Groups in the Azure Portal 
</p>- Click and Select VM2-nsg
</p>- Select Inbound Security Rules under Settings
</p>- Click Add to create another rule
</p>- Select the ICMP protocol, and Select Deny for Actions
</p>- Set Priority to 200
</p>
<br />

<p>
<img src="https://i.imgur.com/0LS8fjG.png" height="80%" width="80%" alt="SSH and Wireshark"/>
</p>
<p>
<b>- Type in and enter "ssh" into the filters
</p>- SSH into the VM2 with the Command Line (ssh labuser@10.1.0.5)
</p>- Type in the password and press Enter 
</p>- You are now SSH into VM2
</p>
<br />

<p>
<img src="https://i.imgur.com/8HSDNSv.png" height="80%" width="80%" alt="DHCP and Wireshark"/>
</p>
<p>
<b>- Type in and enter "dhcp" in the filters
</p>- Type in the command line "ipconfig /renew"
</p>- Observe the DHCP traffic that occurs after the new IP Address is leased
</p>
<br />


