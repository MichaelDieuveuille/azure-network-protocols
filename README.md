<h1>Configuring Network Protocols in Azure</h1>

<h2>Overview</h2>
<p>
In this lab, we explored core network protocols such as ICMP, RDP, DNS, and HTTP/HTTPS within Azure virtual networks. We tested connectivity, configured Network Security Groups (NSGs), and verified how different protocol rules affect communication between virtual machines.
</p>

<h2>Environments and Technologies Used</h2>
<ul>
  <li>Microsoft Azure (Virtual Machines, NSGs)</li>
  <li>Windows Server 2022</li>
  <li>Windows 10 (Client)</li>
  <li>Remote Desktop</li>
  <li>Command Prompt / PowerShell</li>
</ul>

<h2>High-Level Steps</h2>
<ol>
  <li>Create two VMs in the same virtual network (Windows 10 client and Server 2022).</li>
  <li>Configure NSGs to allow or block specific protocols (ICMP, RDP, DNS, HTTP/HTTPS).</li>
  <li>Test connectivity between VMs using <code>ping</code>, <code>nslookup</code>, and browser access.</li>
  <li>Observe the effect of enabling/disabling protocol access in NSG rules.</li>
</ol>

<h2>Actions and Observations</h2>

<img width="1591" height="852" alt="NSG 1" src="https://github.com/user-attachments/assets/401bad82-2d32-4519-87e5-7d6484cf630d" />

<img width="1904" height="874" alt="NSG 2" src="https://github.com/user-attachments/assets/b9f354e9-baba-4215-b472-df7ae1f2e5f9" />

Create two VMs in the Azure portal: one using a Windows 10 Pro image and the other using a Linux image, each with 2 vCPUs. Ensure both VMs are attached to the same virtual network during setup. Use RDP to access the Windows machine.

<img width="358" height="479" alt="NSG 3" src="https://github.com/user-attachments/assets/18f0dd58-4490-4eb9-bbd5-a0ec5fcab573" />

Download and install Wireshark from https://www.wireshark.org. This tool will be used to observe network traffic.

<img width="1935" height="550" alt="NSG 4" src="https://github.com/user-attachments/assets/9f98d760-2fa3-4e3a-b50b-9a74f54c24e7" />

After installing Wireshark, open the application and filter for ICMP traffic in the search bar. ICMP is used by network devices to send error messages and check connectivity.

<img width="1911" height="945" alt="NSG 5" src="https://github.com/user-attachments/assets/14617f1f-05db-401d-9f7a-89bf4f11058f" />


Open PowerShell and use the ping command to test the connectivity to the private IP address of the Linux machine, which is on the same network. You can find the Linux machine's private IP address in the Azure portal under the VM's network settings.

<img width="1917" height="471" alt="NSG 6" src="https://github.com/user-attachments/assets/5ef5c693-1347-4f2b-bb21-edca107f5155" />

You can view each packet sent while pinging the machine in Wireshark, displaying the ICMP traffic for analysis.

<img width="1919" height="567" alt="NSG 7" src="https://github.com/user-attachments/assets/0366d877-e3bf-43ff-9c39-7f31e5f2f424" />


Next, use the ping -t command to continuously ping the Linux machine. Then, go to the Linux VM in Azure, navigate to Network Settings, and create an inbound port rule to deny ICMP traffic, effectively blocking it on the firewall.


<img width="1917" height="915" alt="NSG 8" src="https://github.com/user-attachments/assets/84d9a3a3-d56a-4948-b0ec-8d214df6ac68" />

After blocking ICMP traffic on the Linux machine’s firewall, check Wireshark to see that the pings no longer receive replies. In PowerShell, you’ll see a message saying "Request Timed Out."

<img width="1917" height="915" alt="NSG 9" src="https://github.com/user-attachments/assets/f6983b44-75c9-4d5a-a06c-1fb271324aee" />


Afterward, delete the inbound port rule to allow ICMP traffic again. To stop the continuous pinging, press Ctrl + C in PowerShell.

<img width="856" height="761" alt="NSG 10" src="https://github.com/user-attachments/assets/b5b847cb-1525-41f8-bca5-c16aa202564e" />


Next, we will filter SSH traffic using Wireshark. By now, you should have a basic understanding of how to navigate Wireshark. To proceed, open the command prompt on your Windows machine and establish an SSH connection to the Linux machine using the command: ssh labuser2@10.0.0.5. Once this command is executed, Wireshark will display the SSH traffic, allowing you to observe and analyze it in real time.You can type "exit" to end the linux SSH connection when you're done.

<img width="1819" height="785" alt="NSG 11" src="https://github.com/user-attachments/assets/a29a7e78-85e2-443e-8c8f-1deea43f0f3e" />


Next, we'll filter DNS traffic in Wireshark. Start by setting Wireshark to display only DNS traffic. To generate DNS activity, use the command nslookup www.yahoo.com, which queries the DNS server for Yahoo's IP address.


<img width="1289" height="388" alt="NSG 12" src="https://github.com/user-attachments/assets/a3287e8f-77ef-458a-a8d4-58430e83e33d" />

Now, we'll use Wireshark to filter DHCP traffic. DHCP, or Dynamic Host Configuration Protocol, assigns IP addresses to devices. To generate DHCP traffic, enter the command ipconfig /renew in PowerShell, which requests a new IP address. Wireshark will capture this DHCP activity for analysis.

<img width="1347" height="487" alt="NSG 13" src="https://github.com/user-attachments/assets/f974eb7a-87c9-4ca6-98e9-5f7f1c308b43" />


Lastly, we'll filter for RDP traffic in Wireshark. Since we're using Remote Desktop Protocol to connect to our virtual machine, RDP traffic will appear continuously, providing ample data for analysis.
