<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Video Demonstration</h2>

- ### [YouTube: Azure Virtual Machines, Wireshark, and Network Security Groups](https://www.youtube.com)

<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, RDP, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1 Observe ICMP Traffic
- Step 2 Observe DNS Traffic
- Step 3 Observe DHCP Traffic
- Step 4 Observe SSH Traffic (tcp.port ==22)
- Step 6 Observe RDP Traffic (tcp.port ==3389)

<h2>Actions and Observations</h2>

<p>
<img src="https://github.com/kleeloy/Azure-Networks-Protocols/blob/main/Diagrams/ICMP%20TRAFFIC%20OBSERVED%20AZ-LAB2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://github.com/kleeloy/Azure-Networks-Protocols/blob/main/Diagrams/Network%20Security%20Group%20AZ-Lab2.png " height="80%" width="80%" alt="Disk Sanitization Steps"/>
<img src="https://github.com/kleeloy/Azure-Networks-Protocols/blob/main/Diagrams/DENY_ICMP_PING_FROM_ANYWHERE%20AZ-LAB2.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Opened wireshark on my Windows 10 VM, filtered for ICMP traffic only and observed ping requests and replies within wireshark from the private IP address of the Unbuntu VM. In Powershell we observed a public website (such as www.google.com) and observed the same ping requests and replies within wireshark. When I initiated a perpetual/non-stop ping from my Windows 10 VM to my Ubuntu VM, wireshark was showing non-stop ping requests and replies. I then created an inbound rule in Azure Ubuntu VM to DENY_ICMP_PING_FROM_ANYWHERE_ and observed from wireshark ping activity denying requests.
</p>
<br />

<p>
<img src=" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />

<p>
<img src="https://i.imgur.com/DJmEXEB.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur.
</p>
<br />
