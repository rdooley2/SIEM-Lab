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
Create the VM: <br/>
<img src="https://imgur.com/a/ijuPMUk"/>
<br />
<br />

