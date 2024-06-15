<h1>Microsoft Azure - Mapping RDP Brute Force Attacks</h1>

 ### [YouTube Demonstration](https://youtu.be/aEHL0QrV0SE)

<h2>Description</h2>
This project utilizes multiple custom resources within Microsoft Azure. These resources include a Virtual Machine, Log Analytics Workspace, and Microsoft Sentinel Workbook. The settings within the virtual machine are changed to have all firewalls disabled, making it more appealing to hackers. A custom script is run in the VM PowerShell that looks for Event ID 4625 (Failed Logon) within Windows Event Viewer. The script will pull the IP from each event with the correct ID and send it to a third-party API. The API will then return logs to the Log Analytics Workspace containing geographic information. The raw data in the logs will then be parsed through with a custom query into custom fields (latitude, longitude, state/province, and country). These custom fields are then used to create a workbook within Microsoft Sentinel that will plot the latitude and longitude onto a world map. I also create an alert that detects each failed login attempt and generates incidents when they occur.



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

