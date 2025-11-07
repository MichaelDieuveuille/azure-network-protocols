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

<p>
<img width="2559" height="1011" alt="Screenshot 2025-11-06 231337" src="https://github.com/user-attachments/assets/aaa967ec-9b99-4aa6-956f-a0165169e0d5" />

</p>
<p>
After blocking ICMP in the NSG, the ping request from the client VM timed out, confirming that ICMP traffic was successfully restricted by the firewall rule.
</p>
<br />

<p>
<img width="2559" height="875" alt="Screenshot 2025-11-06 231415" src="https://github.com/user-attachments/assets/5b2eaae7-c27a-46bd-8029-85e68993d427" />

</p>
<p>
When HTTP and HTTPS ports were opened, the client VM could access the web server hosted on the Windows Server VM. RDP access was tested and confirmed through port 3389.
</p>
<br />

<p>
<img width="2559" height="1170" alt="Screenshot 2025-11-06 231510" src="https://github.com/user-attachments/assets/f4225242-3623-4efc-b575-c8a6a458cdb3" />

</p>
<p>
Using <code>nslookup</code>, we verified that DNS resolution functioned properly within the network, and name-to-IP translation succeeded for internal and external domains.
</p>
<br />
