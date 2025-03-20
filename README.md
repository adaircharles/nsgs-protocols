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

<h2>Actions and Observations</h2>

<p>
  I started off by creating a Windows VM and a Linux VM in Azure, making sure that they were on the same Vnet and in the same Resource Group. Next, I installed Wireshark on the Windows VM, started packet capture and filtered for ICMP traffic only. While this was happening, I attempted to ping our Linux VM, as well as www.google.com from the Windows VM to observe ping requests and replies within WireShark.
</p>

![Screenshot 2025-03-20 122515](https://github.com/user-attachments/assets/0eb0aa03-2a6d-4e29-b029-f77d6c756d0c)
![Annotation 2025-03-20 193245](https://github.com/user-attachments/assets/d7bc8cd5-d228-45ac-b368-9e28fb714ed3)

<br />

<p>
  Next, I initiated a perpetual ping in powershell to the Linux-VM, and observed the traffic through WireShark. After, I created a rule in the linux-vm NSG on Azure, and set it up to disable inbound ICMP traffic. After applying the rule, I made sure that traffic was not coming through in WireShark after pinging the machine again. Afterwards, I deleted the rule and tested that ICMP traffic was allowed once again.
</p>

![Annotation 2025-03-20 193947](https://github.com/user-attachments/assets/1e7414a0-dfe3-4aa1-b180-1844c863aa6b)
![Annotation 2025-03-20 193932](https://github.com/user-attachments/assets/d3e3e069-8873-43a5-b629-7fea0394f41f)
![Screenshot 2025-03-20 123737](https://github.com/user-attachments/assets/5eeb5c9a-71de-4152-a355-a311215cba0d)

<br />

<p>
  My next step, I used Powershell to SSH into my Linux-VM, and then observed SSH traffic in WireShark. I then ran Powershell as an Administrator and used ipconfig /renew to issue the VM a new IP, and used WireShark to take note of the changes. 
</p>

![Screenshot 2025-03-20 125419](https://github.com/user-attachments/assets/35154f6a-bc4d-4e29-9fba-a1a3c7fbeb8f)
![Screenshot 2025-03-20 125740](https://github.com/user-attachments/assets/c6f2c5f5-7d7e-4841-b327-18e3ce658271)

<br />

<p>
My last action was to use WireShark to observe the traffic after using nslookup to find the IP addresses of www.google.com and www.disney.com. 
  
</p>

![Annotation 2025-03-20 200636](https://github.com/user-attachments/assets/97b7ce12-7829-4ce9-908d-125d05d92a7a)
