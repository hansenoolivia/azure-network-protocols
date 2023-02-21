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

- Observe ICMP Traffic
- Obersve SSH Traffic
- Observe DHCP Traffic
- Observe DNS Traffic 
- Observe RDP Traffic

<h2>Actions and Observations</h2>

<h3>Oberserve ICMP Traffic</h3>

<p>
<img src="https://i.imgur.com/etSDpoh.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p> 
  
Use Remote Desktop to connect to your Windows 10 Virtual Machine -> Within your Windows 10 Virtual Machine -> Install Wireshark ->
Open Wireshark and filter for ICMP traffic only.
  
<p>
<img src="https://i.imgur.com/cQqUzJw.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p> 
 
 <p>
<img src="https://i.imgur.com/HPvWURu.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>   

Retrieve the private IP address of the Ubuntu VM and attempt to ping it from within the Windows 10 VM ->
Observe ping requests and replies within WireShark.
  
<p>
<img src="https://i.imgur.com/2PvBLsj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p> 

From The Windows 10 VM, open command line or PowerShell and attempt to ping a public website (such as www.google.com) -> observe the traffic in WireShark ->
Initiate a perpetual/non-stop ping from your Windows 10 VM to your Ubuntu VM.
  
 <p>
<img src="https://i.imgur.com/c8hhOa3.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

Open the Network Security Group your Ubuntu VM is using and disable incoming (inbound) ICMP traffic ->
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity.
  
<p>
<img src="https://i.imgur.com/yE8oNuz.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

Re-enable ICMP traffic for the Network Security Group your Ubuntu VM is using ->
Back in the Windows 10 VM, observe the ICMP traffic in WireShark and the command line Ping activity (should start working) -> 
Then stop the ping activity.

<p>
<img src="https://i.imgur.com/SK6tIDZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

<br />
  
  

