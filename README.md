<!-- Repository: azure-network-protocols -->
<h1>Azure Network Protocols — Traffic Analysis with Wireshark</h1>

<h2>🔎 Overview</h2>
<p>
This lab demonstrates how different network protocols communicate between Azure Virtual Machines using <strong>Wireshark</strong>. 
It covers capturing and analyzing traffic (ICMP, SSH, DHCP, DNS, RDP) and testing <strong>Network Security Group (NSG)</strong> rules to manage inbound and outbound connections.
</p>

<h2>🧰 Environments and Technologies Used</h2>
<ul>
  <li><strong>Microsoft Azure</strong> (Virtual Machines / Network Security Groups)</li>
  <li><strong>Wireshark</strong> (Protocol Analyzer)</li>
  <li><strong>Remote Desktop (RDP)</strong> and <strong>PowerShell</strong></li>
  <li><strong>Windows 10</strong> (21H2) and <strong>Ubuntu Server 20.04</strong></li>
</ul>

<h2>⚙️ High-Level Steps</h2>
<ol>
  <li>Deployed Windows and Ubuntu VMs within the same Azure Virtual Network.</li>
  <li>Installed and ran Wireshark on the Windows VM to capture live traffic.</li>
  <li>Observed and filtered traffic for <code>ICMP</code>, <code>SSH</code>, <code>DHCP</code>, <code>DNS</code>, and <code>RDP</code>.</li>
  <li>Configured NSG rules to block and re-enable ICMP traffic, observing changes in connectivity and packet flow.</li>
</ol>

<h2>🧠 Actions and Observations</h2>
<ul>
  <li>Disabling ICMP in the NSG immediately stopped ping replies, confirming proper firewall enforcement.</li>
  <li>Observed encrypted SSH and continuous RDP packet streams, demonstrating secure and persistent connections.</li>
  <li>Verified DHCP renewals and DNS resolutions directly through captured network packets.</li>
  <li>Highlighted how NSG rules control traffic at the Azure network layer, not just within the OS firewall.</li>
</ul>
