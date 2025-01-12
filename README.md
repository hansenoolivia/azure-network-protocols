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
  
<h2>Observe SSH Traffic</h2>
<p>
  
<p>
<img src="https://i.imgur.com/8LaXORS.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>

Back in Wireshark, filter for SSH traffic only.


From your Windows 10 VM, “SSH into” your Ubuntu Virtual Machine (via its private IP address) ->
Type commands (username, pwd, etc) into the linux SSH connection and observe SSH traffic spam in WireShark.
  
<p>
<img src="https://i.imgur.com/bkkUWTy.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>  
Exit the SSH connection by typing ‘exit’ and pressing [Enter].
  
<br />
  
<h2>Observe DHCP Traffic</h2>
<p>
  
 <p>
<img src="https://i.imgur.com/8MCZp4Y.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<p>
<img src="https://i.imgur.com/NRSDRL1.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>  

Back in Wireshark, filter for DHCP traffic only.


From your Windows 10 VM, attempt to issue your VM a new IP address from the command line (ipconfig /renew)
Observe the DHCP traffic appearing in WireShark.
<br />
  
<h2>Observe DNS Traffic</h2>
<p> 
   
<p>
<img src="https://i.imgur.com/v0LAtXZ.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>  

Back in Wireshark, filter for DNS traffic only.


From your Windows 10 VM within a command line, use nslookup to see what google.com and disney.com’s IP addresses are ->
Observe the DNS traffic being show in WireShark.
<br />
  
<h2>Observe RDP Traffic</h2> 
<p>
  
<p>
<img src="https://i.imgur.com/s07S72o.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p> 
  
Back in Wireshark, filter for RDP traffic only (tcp.port == 3389)


Oserve the immediate non-stop spam of traffic? Why do you think it’s non-stop spamming vs only showing traffic when you do an activity?
Answer: because the RDP (protocol) is constantly showing you a live stream from one computer to another, therefor traffic is always being transmitted.
  
<br />  
<p>
  
*Lab Cleanup (DON’T FORGET THIS)*
  
- Close your Remote Desktop connection
- Delete the Resource Group(s) created at the beginning of this lab
- Verify Resource Group Deletion
  
  <br />
  
