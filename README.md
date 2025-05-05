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
Create the VM: <br/><br />
<img src="https://i.imgur.com/XL5RxwD_d.jpg?maxwidth=520&shape=thumb&fidelity=high" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Turn off the Firewall within the VM: <br/><br />
<img src="https://i.imgur.com/qoGqOhh.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Create the Log Analytics Workspace: <br/><br />
<img src="https://i.imgur.com/QjkVCXc.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Configure the Log Settings: <br/><br />
<img src="https://i.imgur.com/lzIxhgX.png" height="80%" width="80%" alt="SIEM Steps"/>
<img src="https://i.imgur.com/hcMc6ON.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Connect the VM to the Log Analytics Workspace: <br/><br />
<img src="https://i.imgur.com/3M8NQZw.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Setup Microsoft Sentinel: <br/><br />
<img src="https://i.imgur.com/whBR9Ex.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Run the custom script in Powershell to collect logs: <br/><br />
<img src="https://i.imgur.com/puDYACr.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Ensure logs are being collected properly: <br/><br />
<img src="https://i.imgur.com/kq4h60E.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Use generic logs from the VM to create custom logs in the Log Analytic Workspace: <br/><br />
<img src="https://i.imgur.com/hUvmWGb.png" height="80%" width="80%" alt="SIEM Steps"/>
<img src="https://i.imgur.com/Q6hwnEF.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Create a new workbook within Microsoft Sentinel: <br/><br />
<img src="https://i.imgur.com/ePasONG.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Insert a custom query to parse raw data into separate fields: <br/><br />
<img src="https://i.imgur.com/OvRZKwP.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Adjust the map settings: <br/><br />
<img src="https://i.imgur.com/bmAgz8B.png" height="80%" width="80%" alt="SIEM Steps"/>
<img src="https://i.imgur.com/EyVUCcd.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Allow people time to attack: <br/><br />
<img src="https://i.imgur.com/uNaFtOM.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Add a custom alert for Event 4625 (Failed Logon): <br/><br />
<img src="https://i.imgur.com/tMXCin5.png" height="80%" width="80%" alt="SIEM Steps"/>
<img src="https://i.imgur.com/FvbH1kD.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Watch as incidents begin to pile in: <br/><br />
<img src="https://i.imgur.com/ylE9BXp.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
And we're done <br/><br />

