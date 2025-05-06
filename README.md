<h1>SIEM Log Analysis with Microsoft Azure</h1>


<h2>Overview</h2>
I used Microsoft Azure to create my own SIEM Dashboard and monitor for certain events. This project aimed to achieve the following goals:
<br><br>
<ul>
 <li>Design and configure a functional SIEM in Microsoft Azure</li>
 <li>Visualize log data in a Microsoft Sentinel Workbook</li>
 <li>Generate custom alerts when incidents are detected</li>
 <li>Automate tasks when alerts are triggered</li>
</ul>

<h2>Summary</h2>
In this project, I used Microsoft Azure to simulate and monitor cyberattacks. I deployed a virtual machine with its firewall disabled to attract malicious login attempts. A custom watchlist was configured to compare known IP addresses against those triggering Event 4625 (Failed Logon). The resulting data was visualized in a Microsoft Sentinel workbook using a world map to display geolocation data. Additionally, I set up an alert rule to generate incidents for each failed login attempt, which were automatically emailed to a designated address.

<h2>Languages and Utilities Used</h2>

- <b>PowerShell</b>

<h2>Environments Used </h2>

- <b>Microsoft Azure</b>

<h2>Project walk-through:</h2>

<p align="center">
<b>Some photos are best viewed in a seperate browser</b><br/><br />
The first thing I did for this project was create a resource group. A resource group is essentially a folder where I can store all of my resources for easier access: <br/><br />
<img src="https://i.imgur.com/xR691To.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
The next step was to create a virtual network. This network allows the resources that I create, such as the Virtual Machine, to communicate amongst each other: <br/><br />
<img src="https://i.imgur.com/uRv9hSe.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Now that I had created the Virtual Network, it was time to create the Virtual Machine. I purposefully chose an important-sounding name so that attackers would be more enticed to try and log in to it. Another thing that I will mention is that I changed the size to the smallest offered since VM storage is not important for this project. Finally, I turned off boot diagnostics since I did not need it: <br/><br />
<img src="https://i.imgur.com/XMBgoih.png" height="80%" width="80%" alt="SIEM Steps"/> <br/><br />
<img src="https://i.imgur.com/MaepeEL.png" height="80%" width="80%" alt="SIEM Steps"/> <br/><br />
<img src="https://i.imgur.com/Hu6o8eO.png" height="80%" width="80%" alt="SIEM Steps"/> <br/><br />
<br />
<br />
<br />
After I created the VM, I navigated back to the Resource Group to ensure that I had properly created everything: <br/><br />
<img src="https://i.imgur.com/5dYHCz8.png" height="150%" width="150%" alt="SIEM Steps"/>
<br />
<br />
<br />
Next, I needed to configure the inbound security rules for the VM. I ended up deleting the RDP inbound rule and replacing it with one that allows all traffic the ability to attempt to access the VM remotely: <br/><br />
<img src="https://i.imgur.com/qlOAc3I.png" height="150%" width="150%" alt="SIEM Steps"/> <br/><br />
<img src="https://i.imgur.com/Sidage4.png" height="150%" width="150%" alt="SIEM Steps"/> <br/><br />
<br />
<br />
<br />
Now that I had properly configured the VM, I needed to set up a Log Analytics Workspace. This workspace essentially allows me to collect log data from the VM: <br/><br />
<img src="https://i.imgur.com/sTlP9tG.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
With both the VM and LAW setup, I needed to create Microsoft Sentinel. Sentinel is Microsoft's version of a Security Information and Event Management system (SIEM). It is essential in analytics and threat visibility. It is also where we will be mapping the data we collect from attackers: <br/><br />
<img src="https://i.imgur.com/XxE063J.png" height="80%" width="80%" alt="SIEM Steps"/> <br/><br />
<br />
<br />
<br />
Once I had set up Sentinal, I had to connect it to the LAW so that Sentinel could use the collected log data: <br/><br />
<img src="https://i.imgur.com/VcWaYTp.png" height="150%" width="150%" alt="SIEM Steps"/>
<br />
<br />
<br />
Next, I went into the Content hub for Microsoft Sentinel and installed the Windows Security Event add-on. Doing this will allow us to connect the LAW to the VM: <br/><br />
<img src="https://i.imgur.com/HCLWhEZ.png" height="150%" width="150%" alt="SIEM Steps"/> <br/><br />
<img src="https://i.imgur.com/yrCpkfB.png" height="150%" width="150%" alt="SIEM Steps"/>
<br />
<br />
<br />
With the Windows Security Event add-on installed, I had to configure it. I do this by opening the connector page: <br/><br />
<img src="https://i.imgur.com/IhEedlN.png" height="150%" width="150%" alt="SIEM Steps"/>
<br />
<br />
<br />
Once I clicked to open the connector page, I clicked to create a data collection rule. Making the rule connects the VM to the LAW and Sentinel instances: <br/><br />
<img src="https://i.imgur.com/WdSVi47.png" height="150%" width="150%" alt="SIEM Steps"/>
<br />
<br />
<br />
Navigating to the page for the VM, I was able to confirm that I had successfully configured the extension: <br/><br />
<img src="https://i.imgur.com/NXlAVDj.png" height="150%" width="150%" alt="SIEM Steps"/>
<br />
<br />
<br />
By this point, I had completed most of the configuration and moved my focus to the VM. I entered the VM through a remote desktop connection and navigated to the Windows Defender Firewall. Here I was able to turn off everything, making the system fully vulnerable to anyone on the internet: <br/><br />
<img src="https://i.imgur.com/FqBKdUS.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
I then navigated to PowerShell on my PC and tried pinging the VM to ensure that it was properly accessible to anyone on the internet: <br/><br />
<img src="https://i.imgur.com/WQEviJs.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Now that the VM was vulnerable, I went to Sentinel to set up a Watchlist. The watchlist allows me to upload an external data source to compare to the data from the logs. The file that I uploaded translates any IP Address from the log data and correlates it to a certain region/latitude/longitude: <br/><br />
<img src="https://i.imgur.com/twWcKLL.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
The file I uploaded is one I found on the internet, and it has over fifty-thousand entries: <br/><br />
<img src="https://i.imgur.com/J8Nn7re.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
I then went to the LAW and wrote a quick KQL query to see the data from the uploaded file. The query helped me to confirm that everything went right: <br/><br />
<img src="https://i.imgur.com/pXejnzQ.png" height="150%" width="150%" alt="SIEM Steps"/>
<br />
<br />
<br />
Next, I went into Sentinel to create a Workbook. The Workbook is where I will be displaying the collected data on a map. The first thing I did was remove the charts it automatically generated and added a query: <br/><br />
<img src="https://i.imgur.com/vnPP7gs.png" height="150%" width="150%" alt="SIEM Steps"/><br/><br />
<img src="https://i.imgur.com/KYtc2ef.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
The KQL query below is quite big, but essentially, what it is doing is pulling failed logon events from Windows Security logs, matching the attacker IP addresses with geographic data from the watchlist, counting how many times each IP appears, and then plotting the results on a heatmap showing where the attacks originate: <br/><br />
<img src="https://i.imgur.com/l5VBIoo.png" height="80%" width="80%" alt="SIEM Steps"/> <br/><br />
<img src="https://i.imgur.com/FTq3UEF.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
With the new query, I could now see the full map. I will be coming back to this at the end of the report to show the final results: <br/><br />
<img src="https://i.imgur.com/Fisexu3.png" height="150%" width="150%" alt="SIEM Steps"/>
<br />
<br />
<br />
The next step was alerts and automation. I started with automation because I will need it when making the alert. I navigated to the automation tab within Sentinel and created a "playbook with incident trigger." A playbook is essentially the automation of selected tasks when a trigger occurs, in this case, an incident: <br/><br />
<img src="https://i.imgur.com/t3YZtvc.png" height="150%" width="150%" alt="SIEM Steps"/>
<br />
<br />
<br />
Creating the playbook was quite simple. The harder part is in the next step: <br/><br />
<img src="https://i.imgur.com/F4h4BJM.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Next, I headed to the logic app designer by clicking on the playbook I just made. The logic app designer allows me to customize the playbook's actions when an incident occurs. I connected my school email to Microsoft Azure to automate emails whenever an incident occurred. Then, I added the email section and added the information I wanted it to send out. In a professional environment, these emails would need to be more formal and detailed, but for the proof of concept, I designed them to be simple: <br/><br />
<img src="https://i.imgur.com/Fisexu3.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
With automation finished, I needed to create an alert that could trigger and use my configured playbook. To start, I navigated to the Analytics section in Sentinel and selected to create a scheduled query rule: <br/><br />
<img src="https://i.imgur.com/J1uQTi1.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Next, I named the rule and gave it a description. In addition, I wrote a simple KQL query that would trigger each time Event 4625 was detected and had it run the query every ten minutes. Finally, I added an automation rule so that Sentinel could execute the playbook every time the alert trigger: <br/><br />
<img src="https://i.imgur.com/7TV7BQj.png" height="80%" width="80%" alt="SIEM Steps"/> <br/><br />
<img src="https://i.imgur.com/xE9ittu.png" height="80%" width="80%" alt="SIEM Steps"/> 
<img src="https://i.imgur.com/q1va0T4.png" height="80%" width="80%" alt="SIEM Steps"/> <br/><br />
<img src="https://i.imgur.com/dlNioCD.png" height="150%" width="150%" alt="SIEM Steps"/>
<br />
<br />
<br />
After creating the rule, I went back to the Analytics Dashboard to see that multiple attackers had already triggered the alert, thus letting me know that it was working: <br/><br />
<img src="https://i.imgur.com/r5Gw5Ng.png" height="150%" width="150%" alt="SIEM Steps"/>
<br />
<br />
<br />
I then took a thirty-minute break and returned to check my email inbox. I was able to confirm that the Sentinel was automatically sending the emails correctly:<br/><br />
<img src="https://i.imgur.com/5abc6vS.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
In addition, I navigated to the Incidents tab to see all of the alerts from the past thirty minutes: <br/><br />
<img src="https://i.imgur.com/0UME359.png" height="150%" width="150%" alt="SIEM Steps"/>
<br />
<br />
<br />
I also decided to create a dashboard. A dashboard allows you to customize your experience and display anything you need. In this case, I wanted to display the attack map, my resource groups for ease of access, and a clock. To do this, I navigated back to the attack map and pinned it to a new dashboard: <br/><br />
<img src="https://i.imgur.com/yg5iMwk.png" height="150%" width="150%" alt="SIEM Steps"/>
<br />
<br />
<br />
I then navigated to my new dashboard and customized it using the available options: <br/><br />
<img src="https://i.imgur.com/irO96Q6.png" height="150%" width="150%" alt="SIEM Steps"/>
<br />
<br />
<br />
In the end, it came out nice. The dashboard would be useful in a professional environment so that you could access everything of importance easily: <br/><br />
<img src="https://i.imgur.com/YAowc4V.png" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
After waiting twenty-four hours, I decided to come back and check on my map. It ended up looking pretty cool!: <br/><br />
<img src="" height="80%" width="80%" alt="SIEM Steps"/>
<br />
<br />
<br />
Thanks for reading this far! I enjoyed learning all about everything Microsoft Azure has to offer, and I hope you did, too!<br/><br />

