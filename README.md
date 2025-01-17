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

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Actions and Observations</h2>

<p>
<img src="https://i.imgur.com/SKFAVNj.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Before we can execute a traffic examination in Microsoft Azure, we must create a virtual network along with both a Linux and Windows Virtual Machines. For this we must create our first resource group (Lab-Test-1) in Microsoft Azure as illustrated above. In this example we are using the free 200$ incentative Azure credits for First time users which is an awesome perk for anyone getting started.
</p>
<br />

<p>
<img src="https://i.imgur.com/UHtW98t.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Projects we do in Azure will live inside some kind of resource group which is why we created one in the first step. Our next step is to create a Resource Group name (RG-Network-Activities) that identifies closely to the kind of work we are doing, this project will be stored and accesible for edit etc under this name. Now we create a container our virtual network (Lab2-Vnet) where Both Virtual Machines (Linux-VM, MyLowCostVM ,as shown above) are created and stored together to live in the same network.
</p>
<br />

<p>
<img src="https://i.imgur.com/v2fac3x.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now that we have created a small network with two Virtual Machines we can start prepping for a Traffic examination. For this we will have to know the Public IP address of atleast one of the Virtual machines, which in this example i chose the windows machine (20.3.253.44) and the linux machine's private IP address we will later ping in Powershell to test connection.
</p>
<br />

<p>
<img src="https://i.imgur.com/emyVpLH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this ilustration we have accessed the Windows Virtual Machine by means of the RDP (Remote Desktop Protocol). You will notice the Public IP address on the top left (20.3.253.44) which will help you rememeber in which system you are working from. Important to note is that in Microsoft azure you will need to rememeber login name and password you set up for each VM in order for RDP to work.
</p>
<br />










