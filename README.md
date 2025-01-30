# Building-an-Elastic-SIEM-Lab
# Obective
This project simulates a Security Information and Event Management (SIEM) lab with Elastic SIEM and a Kali Linux VM for security monitoring. Logs will be forwarded using Elastic Beats, and Nmap scans will generate security events. Logs are queried and analyzed in the Elastic web interface, visualized in a dashboard, and monitored with an alert to detect specific security events.
 
<h2>Languages and Utilities Used</h2>

- <b>Oracle Virtualbox</b> 
- <b>Kali Linux</b>
- <b>Elastic</b>

<h2>Environments Used </h2>

- <b>Windows 10 Enterprise</b>  

<h2>Program walk-through:</h2>

- Create a free Elastic account (14day free trial)
- Set up the Elastic Agent on Kali to collect and send logs to the SIEM.
- Generate security events on the Kali VM.
- Search for security events using queries in Elastic SIEM.
- Build a dashboard to visualize security events.
- Configure alerts to detect security events.  Oracle VirtualBox is a type 2 software-based hypervisor

<h2>Phase 1</h2>
<p align="center"> 
  <br/>
  
  Create a free Elastic account [https://cloud.elastic.co/registration] <br/>
  Once you have an Elastic account, log in to the Elastic Cloud console at [https://cloud.elastic.co.] <br/>
  Click on the “Create Deployment” button and select “Elasticsearch” as the deployment type:  
<img src="https://imgur.com/jKZhUIs.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
 Click on the “Create Deployment” button and select “Elasticsearch” as the deployment type:  <br/>
<img src="https://imgur.com/LHbVGjb.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Select the ISO download 64-bit edition : <br/>
<img src="https://imgur.com/NhooXIz.png height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Downloaded file:  <br/>
<img src="https://imgur.com/Nv8WwV6.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Dowload Windows 10 Enterprise: Select the ISO file <br/>
<img src="https://imgur.com/i2MDWIB.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Select the corresponding ISO Enterprise download:  <br/>
<img src="https://imgur.com/6zsawvN.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Downloaded file:  <br/>
<img src="https://imgur.com/87n7ILy.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Download Metasploitable (may take some time):  <br/>
<img src="https://imgur.com/FE7MeBz.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Downloaded file:  <br/>
<img src="https://imgur.com/DrlaREc.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Download Kali-Linux and unzip (may take some time):  <br/>
<img src="https://imgur.com/0ihBrGt.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Downloaded file (7 Zip): <br/>
<img src="https://imgur.com/87ER2eJ.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
 
 # Setup and Installation
 <p align="center">
 <br/>
 Install and open VirtualBox:  <br/>
<img src="https://imgur.com/pN8fwY0.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Set-up Kali-linux in the virtual environment; Click "Add" in VirtualBox, select the extracted file <br/>
<img src="https://imgur.com/YBWUdi8.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<img src="https://imgur.com/GLFy3Ad.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Log-in: username: kali, password: kali  <br/>
<img src="https://imgur.com/muQ5CkL.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<img src="https://imgur.com/6TJOoJS.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Step"/>
<br />
<br />
Setup Windows Server 2022; Click New in VirtualBox, fill name: Windows Server 2022,  add a destination folder, Type: Microsoft Windows, Version: Windows 10 (64-bit<br/>
<img src="https://imgur.com/u9mvILb.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
For the hardware, we selected 4MB and 1 CPU:  <br/>
<img src="https://i.imgur.com/0rOXxin.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Select the file location, choose VirtualBox Disk Image (VDI) as it can only be used by VirtualBox. Finish setup :  <br/>
<img src="https://i.imgur.com/5PK7F5k.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Start Windows Server 2022 on VirtualBox:  <br/>
<img src="https://imgur.com/gCvUJJy.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
 Select the downloaded Windows Server 2022 file (SERVER_EVAL_x64FRE_en-us.iso) when prompted. Click "Mount and Retry Boot"  <br/>
<img src="https://imgur.com/bLFxPla.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
 Complete installation and Setup process:  <br/>
<img src="https://i.imgur.com/kXoYssq.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
 Windows Server 2022 installation complete:  <br/>
<img src="https://i.imgur.com/470ghIM.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<img src="https://i.imgur.com/G43rDJ1.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Set-up Kali-linux; Click New in VirtualBox, fill name: Windows 10 2025,  add a destination folder, Type: Microsoft Windows, Version: Windows 10 (64-bit) :  <br/>
<img src="https://i.imgur.com/pqgcl6Q.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
For the hardware, we selected 2MB and 1 CPU:  <br/>
<img src="https://i.imgur.com/PHwrE6Q.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Select the file location, choose VirtualBox Disk Image (VDI) as it can only be used by VirtualBox. Finish setup :  <br/>
<img src="https://i.imgur.com/5PK7F5k.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Start Windows 10 2025 on VirtualBox:  <br/>
<img src="https://imgur.com/AMPeSQ9.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Select the downloaded Windows 10 file (19045.2006.220908-0225.22h2_release_svc_refresh_CLIENTENTERPRISEEVAL_OEMRET_x64FRE_en-us.iso) when prompted. Click "Mount and Retry Boot"  <br/>
<img src="https://imgur.com/GKX43gN.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Complete installation and Setup process:  <br/>
<img src="https://i.imgur.com/4bxraNc.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
 Select "Domain join instead" for Windows 10 2025 and complete installation :  <br/>
<img src="https://i.imgur.com/wci3Jgk.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
Window 10 Enterprise Running:  <br/>
<img src="https://i.imgur.com/vkrmAvn.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />

<br />:  <br/>
<
</p>

<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@
```
--!>
