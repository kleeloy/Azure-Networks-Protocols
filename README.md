<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />


<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, RDP, ICMP, DHCP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1 Observe ICMP Traffic
- Step 2 Observe SSH Traffic (tcp.port ==22)
- Step 3 Observe DHCP Traffic
- Step 4 Observe DNS Traffic
- Step 6 Observe RDP Traffic (tcp.port ==3389)

<h2>Actions and Observations</h2>

<p>
<img src="https://github.com/kleeloy/Azure-Networks-Protocols/blob/main/Diagrams/ICMP%20TRAFFIC%20OBSERVED%20AZ-LAB2.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://github.com/kleeloy/Azure-Networks-Protocols/blob/main/Diagrams/Network%20Security%20Group%20AZ-Lab2.png " height="70%" width="70%" alt="Disk Sanitization Steps"/>
<img src="https://github.com/kleeloy/Azure-Networks-Protocols/blob/main/Diagrams/DENY_ICMP_PING_FROM_ANYWHERE%20AZ-LAB2.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<p>
Opened wireshark on my Windows 10 VM, filtered for ICMP traffic only and observed ping requests and replies within wireshark from the private IP address of the Unbuntu VM. In Powershell we observed a public website (such as www.google.com) and observed the same ping requests and replies within wireshark. When I initiated a perpetual/non-stop ping from my Windows 10 VM to my Ubuntu VM, wireshark was showing non-stop ping requests and replies. I then created an inbound rule in Azure Ubuntu VM to DENY_ICMP_PING_FROM_ANYWHERE_ and observed from wireshark ping activity denying requests.
</p>
<br />

<p>
<img src="https://github.com/kleeloy/Azure-Networks-Protocols/blob/main/Diagrams/SSH%20OBSERVATIONS%20AZ-LAB2.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<p>
Filtered wireshark on my Windows 10 VM to SSH. From my Windows 10 VM, I "SSH into" my Ubuntu VM (via its private IP address). Once logged into Ubuntu from my Windows 10 VM I typed commands in such as:

```
$ uname -a 
pwd
touch hello.txt
ls -lasth
```

To observe SSH traffic spam in wireshark. 

</p>
<br />

<p>
<img src="https://github.com/kleeloy/Azure-Networks-Protocols/blob/main/Diagrams/DHCP%20OBSERVATION%20AZ-LAB2.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<p>
Filtered wireshark on my Windoes 10 VM to DHCP. DHCP use is to automatically assign IP addresses. From Windows 10 VM I attemot to issue my VM a new IP address with command line:

```
$ ipconfig /renew
```

From there a new IP address was issued and traffic spammed on wireshark. 

</p>
<br />

<p>
<img src="https://github.com/kleeloy/Azure-Networks-Protocols/blob/main/Diagrams/DNS%20OBSERVATION%20AZ-LAB2.png" height="70%" width="70%" alt="Disk Sanitization Steps"/>
</p>
<p>
Filtered wireshark on my Windows 10 VM to DNS (udp.port ==53), from my Windows 10 VM within the command line:

```
$ nslookup www.google.com
nslookup www.disney.com
```
To spam traffic within wireshark, watching the DNS server lookup what the IP address were for www.google.com and www.disney.com
