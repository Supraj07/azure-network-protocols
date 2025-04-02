<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1> Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark. <br />

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

- Step 1 Microsoft Account creation and resource group creation.
- Step 2 Container/ Network creation.
- Step 3 VM prep for RDP access.
- Step 4 RDP execution and detail.
- step 5 Wireshark Download into Windows VM.
- step 6 Wireshark sniff/ Packet trace from WindowsVM to LinuxVM.

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/SKFAVNj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Before we can execute a traffic examination in Microsoft Azure, we must create a virtual network along with both a Linux and Windows Virtual Machine each. For this we must create our first resource group (Lab-Test-1) in Microsoft Azure as illustrated above. In this example we are using the free 200$ incentative Azure credits for First time users which is an awesome perk for anyone getting started.
</p>
<br />

<p>
<img src="https://i.imgur.com/UHtW98t.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Projects we do in Azure will live inside a resource group which we have created here in the first step. Our next step is to create a Resource Group name (RG-Network-Activities) this identifies more to the kind of work we will be doing. This project will be stored and available for edit under this name. Now we create a container a virtual network (Lab2-Vnet) where Both Virtual Machines from earlier (Linux-VM, MyLowCostVM as shown above) were created under the same network.
</p>
<br />

<p>
<img src="https://i.imgur.com/v2fac3x.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now that we have created a small network with two Virtual Machines we can start prepping for a Traffic examination. For this we will have to take note of the Public IP address of atleast one of the Virtual machines, which in this example i chose the windows machine (20.3.253.44) and we will use the linux machine's private IP address that we will later ping in Powershell to test connection.
</p>
<br />

<p>
<img src="https://i.imgur.com/emyVpLH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this ilustration we have accessed the Windows Virtual Machine by means of the RDP (Remote Desktop Protocol). You will notice the Public IP address on the top left (20.3.253.44) which determines from which in which virtual machine we are on. It is Important to note that in Microsoft azure the login name and password we set for each VM are important to store safely to log in when RDP is used.
</p>
<br />

<p>
<img src="https://i.imgur.com/PFKKGoA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To see Packet Traffic between our VMs we will need to download Wireshark in our Windows VM, after download and agreeing to default settings it should look as screen shot above.
</p>
<br />

<p>
<img src="https://i.imgur.com/3k24I58.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In the last step Wireshark is opened along with powershell to start looking at traffic when we start pinging addreses. As you can see we find the Linux VM's private IP Address (10.0.0.5) to ping, while in the wireshark Analyser we specifically look for only ICMP traffic, ICMP stands for Internet Control Message Protocol. This traffic is an essential part of network management and troubleshooting. Understanding and looking into ICMP traffic can help network administrators, security professionals, and anyone managing a network system identify potential issues or threats . In powershell we see how successfully all the request and replies with 0% packet loss appears which is what you want to see when asking for feedback from your Virtual Machines.
</p>
<br />








