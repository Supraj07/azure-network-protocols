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
Before conducting a traffic examination in Microsoft Azure, it’s important to first set up the necessary environment. The process begins by creating a resource group named "Lab-Test-1", which acts as a container to organize and manage all related resources for the lab. Within this resource group, you’ll need to create a virtual network (VNet) that allows communication between different resources, along with one Linux Virtual Machine and one Windows Virtual Machine. These virtual machines will serve as the endpoints for testing and analyzing traffic. This setup uses the $200 in free Azure credits available to first-time users—a valuable perk that allows beginners to explore and experiment within the Azure platform at no cost.
</p>
<br />

<p>
<img src="https://i.imgur.com/UHtW98t.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Projects we create in Azure are organized within resource groups, which act as logical containers for related resources. In this step, we create a new resource group named "RG-Network-Activities" to better reflect the type of work involved in this project. This name helps keep our activities clearly labeled and organized, making future management and edits easier. Once the resource group is created, we set up a virtual network (Lab2-Vnet) to serve as a shared network environment. Both virtual machines from the earlier step—Linux-VM and MyLowCostVM—are placed within this same network, allowing them to communicate with each other and participate in the traffic examination under a unified infrastructure
</p>
<br />

<p>
<img src="https://i.imgur.com/v2fac3x.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
Now that we’ve created a small network with two virtual machines, we can begin preparing for a traffic examination. To do this, we need to identify the public IP address of at least one of the virtual machines. In this example, we’ll use the Windows virtual machine’s public IP address: 20.3.253.44. Additionally, we’ll locate the private IP address of the Linux virtual machine. This private IP will be used later to test the connection by sending a ping from the Windows machine using PowerShell. This setup allows us to verify network communication between the two machines within our Azure environment.
</p>
<br />

<p>
<img src="https://i.imgur.com/emyVpLH.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In this illustration, we have accessed the Windows Virtual Machine using RDP (Remote Desktop Protocol). You can confirm that you are connected to the correct virtual machine by checking the public IP address displayed in the top left corner—in this case, 20.3.253.44. This helps verify which machine you are working on. It’s important to remember that in Microsoft Azure, the username and password you set during the creation of each virtual machine are essential for accessing them via RDP. Be sure to store these credentials securely, as they are required each time you connect to the virtual machine remotely.
</p>
<br />

<p>
<img src="https://i.imgur.com/PFKKGoA.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
To capture and analyze packet traffic between our virtual machines, the first step is to install Wireshark on the Windows VM. After logging in via RDP, open your browser, download the latest Wireshark installer from the official website, and run it. When prompted, accept the default installation options these include the WinPcap or Npcap network driver necessary for packet capture. Once the installation completes, launch Wireshark: you should see the familiar interface (as shown in the screenshot above), listing all network adapters available for monitoring. From here, you’re ready to begin capturing live traffic between your Linux and Windows VMs.
</p>
<br />

<p>
<img src="https://i.imgur.com/3k24I58.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
In the final step, we open both Wireshark and PowerShell on the Windows Virtual Machine to begin observing network traffic in real time. Using PowerShell, we ping the Linux VM’s private IP address (10.0.0.5) to generate network activity. In Wireshark, we apply a filter to display only ICMP traffic, which stands for Internet Control Message Protocol. ICMP is a crucial protocol used for network diagnostics and troubleshooting—it helps administrators and security professionals monitor connectivity and detect potential issues. As the pings are sent, we can see in PowerShell that all requests receive successful replies with 0% packet loss, which indicates strong and reliable communication between the virtual machines. This confirms that our network setup is functioning correctly.
</p>
<br />








