<h1>Microsoft Azure - Mapping RDP Brute Force Attacks</h1>

 ### [YouTube Demonstration](https://youtu.be/7eJexJVCqJo)

<h2>Description</h2>
Project consists of multiple resources being created within Microsoft Azure. These include a Virtual Machine, Log Analytics Workspace, and Microsoft Sentinel. The settings within the virtual machine are edited to have all firewalls disabled making it more appealing to hackers. A custom script is run in the VM Powershell that looks for Event ID 4625 (Failed Logon) within Windows Event Viewer. The script will pull the IP from each event with the correct ID and send it to a third party API. The API will then return logs to the Log Analytics Workspace containing geographic information. The raw data in the logs will then be parsed through using a custom query into custom fields (latitude, longitude, state/province, and country). These custom fields are then used to create a workbook within Microsoft Sentinel that will plot the latitude and longitude onto a world map. 



<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b> 


<h2>Environments Used </h2>

- <b>Microsoft Azure</b> (21H2)

<h2>Program walk-through:</h2>

<p align="center">
Create the VM: <br/><br />
<img src="https://i.imgur.com/XL5RxwD_d.jpg?maxwidth=520&shape=thumb&fidelity=high" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Turn off Firewall within the VM: <br/><br />
<img src="https://i.imgur.com/qoGqOhh.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Create the Log Analytics Workspace: <br/><br />
<img src="https://i.imgur.com/QjkVCXc.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Configure Log Settings: <br/><br />
<img src="https://i.imgur.com/lzIxhgX.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
<img src="https://i.imgur.com/hcMc6ON.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Connect VM to the Log Analytics Workspace: <br/><br />
<img src="https://i.imgur.com/3M8NQZw.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Setup Microsoft Sentinel: <br/><br />
<img src="https://i.imgur.com/whBR9Ex.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Run Script in Powershell to collect logs: <br/><br />
<img src="https://i.imgur.com/puDYACr.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Ensure Logs are being collected properly: <br/><br />
<img src="https://i.imgur.com/kq4h60E.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />


