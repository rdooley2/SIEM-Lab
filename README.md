<h1>SIEM Log Analysis with Microsoft Azure</h1>


<h2>Overview</h2>
I used Microsoft Azure to create my own SIEM Dashboard and monitor for certain events. This project aimed to achieve the following goals:
<br><br>
<ul>
 <li>Design and configure a functional SIEM in Microsoft Azure</li>
 <li>Automate the detection of incident</li>
 <li>Visualize log data in a Microsoft Sentinel Workbook</li>
 <li>Generate custom alerts when incidents are detected</li>
</ul>

<h2>Summary</h2>
In this project, I use Microsoft Azure to simulate and monitor cyberattacks. I create a virtual machine with the firewalls disabled to attract attackers. In addition, a custom PowerShell script is run on the VM to detect failed login attempts (Event ID 4625) and extract the attacker’s IP addresses to send to a third-party API. The API returns geographic data to store in a Log Analytics Workspace. The stored data is parsed into custom fields and visualized in a Microsoft Sentinel workbook on a world map. Additionally, an alert is configured to generate incidents for each failed login attempt. These alerts are then automatically emailed to a set email address. 

<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b>

<h2>Environments Used </h2>

- <b>Microsoft Azure</b>

<h2>Project walk-through:</h2>

<p align="center">
The first thing that I did for this project was create a resource group. This is essentially a folder where all of my resources will be stored for easier access: <br/><br />
<img src="https://i.imgur.com/xR691To.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
The next step was to create a virtual network. This network allows the resources that I create, such as the Virtual Machine, to communicate amongst each other: <br/><br />
<img src="https://i.imgur.com/uRv9hSe.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Now that I had created the Virtual Network, it was time to create the Virtual Machine. I purposulfully chose an important sounding name so that attackers would be more enticed to try and login to it. Another thing that I will mention is that I changed the size to the smallest offered since VM storage is not important for this project. Finally, I disabled boot diagnostics since I did not need it: <br/><br />
<img src="https://i.imgur.com/XMBgoih.png" height="80%" width="80%" alt="SIEM Steps"/> <br/><br />
<img src="https://i.imgur.com/MaepeEL.png" height="80%" width="80%" alt="SIEM Steps"/> <br/><br />
<img src="https://i.imgur.com/Hu6o8eO.png" height="80%" width="80%" alt="SIEM Steps"/> <br/><br />
<br />
<br />
<br />
After the VM was created, I navigated back to the Resource Group to ensure that everything was properly created: <br/><br />
<img src="https://i.imgur.com/5dYHCz8.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Next I needed to configure the inbound security rules for the VM. I ended up deleting the RDP inbound rule and replacing it with one that allows all traffic to remotloy attempt to access the VM: <br/><br />
<img src="https://i.imgur.com/qlOAc3I.png" height="80%" width="80%" alt="SIEM Steps"/> <br/><br />
<img src="https://i.imgur.com/Sidage4.png" height="80%" width="80%" alt="SIEM Steps"/> <br/><br />
<br />
<br />
<br />
Now that the VM was properly configured, I needed to setup a Log Analytics Workspace. This workspace essentially allows me to collect log data from the VM: <br/><br />
<img src="https://i.imgur.com/sTlP9tG.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
With both the VM and LAW setup, I needed to create Microsoft Sentinel. Sentinel is Microsoft's version of a Security Information and Event Management system (SIEM). It is essential in analytics and threat visibility. It is also where we will be mapping the data we collect from attackers: <br/><br />
<img src="https://i.imgur.com/XxE063J.png" height="80%" width="80%" alt="SIEM Steps"/> <br/><br />
<br />
<br />
<br />
Once Sentinal was setup, I had to connect it to the LAW so that the collected log data could be used by Sentinel: <br/><br />
<img src="https://i.imgur.com/VcWaYTp.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Next I went into the Content hub for Microsoft Sentinel and installed the Windows Security Event add-on. Doing this will allow us to connect the LAW to the VM: <br/><br />
<img src="https://i.imgur.com/HCLWhEZ.png" height="80%" width="80%" alt="SIEM Steps"/> <br/><br />
<img src="https://i.imgur.com/yrCpkfB.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
With the Windows Security Event add-on installed, I next had to configure it. I do this by opening the connector page: <br/><br />
<img src="https://i.imgur.com/IhEedlN.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Once I clicked to open the connector page, I clicked to create a data collection rule. Making the rule connects the VM to the LAW and Sentinel instances: <br/><br />
<img src="https://i.imgur.com/WdSVi47.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Navigating to the page for the VM, I was able to confirm that the extension was successfully configured: <br/><br />
<img src="https://i.imgur.com/NXlAVDj.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Most of the configuring was done at this point so I decided to enter the VM through Remote Desktop Connection. Once inside, I navigated to the Windows Defender Firewall and disabled everything making the system fully vulnerable to anyone on the internet: <br/><br />
<img src="https://i.imgur.com/FqBKdUS.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
I then navigated to PowerShell on my PC and tried pinging the VM to ensure that it was properly accessible to anyone on the internet: <br/><br />
<img src="https://i.imgur.com/WQEviJs.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Now that the VM was vulnerable, : <br/><br />
<img src="https://i.imgur.com/ylE9BXp.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
And we're done <br/><br />

