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
- Set up the Elastic Agent on Linux to collect and send logs to the SIEM.
- Generate security events on the Kali VM.
- Search for security events using queries in Elastic SIEM.
- Build a dashboard to visualize security events.
- Configure alerts to detect security events.  Oracle VirtualBox is a type 2 software-based hypervisor


<h2>Phase 1: Create an Elastic account </h2>
<p align="center"> 
  <br/>
  
  1. Create a free Elastic account [https://cloud.elastic.co/registration] <br/>
  2. Once you have an Elastic account, log in to the Elastic Cloud console at [https://cloud.elastic.co.] <br/>
  3. Click on the “Create Deployment” button and select “Elasticsearch” as the deployment type:  
<img src="https://imgur.com/jKZhUIs.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<img src="https://imgur.com/LHbVGjb.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
  4. Choose a region and deployment size that fits your needs and click on “Create Deployment.”:  <br/>
<img src="https://imgur.com/DfZZ6cS.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
  5. Wait for the configuration to complete, once the deployment is ready, click “continue.”: <br/>
<img src="https://imgur.com/CaDnIw3.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<img src="https://imgur.com/kOtMXUX.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>


<h2>Phase 2: Setting up Kali-linux </h2>
For this setup, we'll be using Kali Linux with Oracle VirtualBox. Setup information can be found from the previous repository:

[https://github.com/Israel-Adeniba/Building-a-Cbersecurity-Lab/blob/main/README.md#building-a-cbersecurity-lab]<br />
<br />


<h2>Phase 3: Setting up the Agent to Collect Logs </h2>
<br /> 
An agent is a software application installed on a device, like a server or endpoint, to gather and transmit data to a central system for analysis and monitoring. In Elastic SIEM, the agent collects and forwards security events from endpoints to the SIEM for further analysis. <br/>

Now we put the agent on Kali linux VM to collect and push audit logs and Telemetry to the Elastic SIEM:

  1. Log in to your Elastic SIEM instance and navigate to the Integrations page by searching and selecting Integrations at the search bar
<img src="https://imgur.com/OLGet8Q.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
  2. Select “Elastic Defend” and click on it to open the integration page: <br/>
<img src="https://imgur.com//lOC6Jxw.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
  3. Click on “Add Elastic Defend”: <br/>
<img src="https://imgur.com/lFr5jHR.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
  4. Click on “Install Elastic Defend”: <br/>
<img src="https://imgur.com/JVfXCWg.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
  5. Follow the instructions provided on the integration page to install the agent on your Kali linux VM.Downloaded file: <br/>
<img src="https://imgur.com/P3pxnxp.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
  6. Paste the copied command into the Kali linux Power shell terminal (command line): <br/>
<img src="https://imgur.com/Z9aEY32.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
  7. After the agent is installed, which can take a few minutes, you’ll see a confirmation message: "Successfully enrolled the Elastic Agent" and “Elastic Agent has been successfully installed.” This will automatically start collecting and forwarding logs to your Elastic SIEM instance, although it might take a few minutes for the logs to appear in the SIEM.:  <br/>
<img src="https://imgur.com/CTZy7DB.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
  8. Two ways to verify that the agent has been installed correctly are by
     -Running this command: "sudo systemctl status elastic-agent.service:: <br/>
<img src="https://imgur.com/Lgwm1vk.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
     -The Elastic SIEM website will post a confirmation of Agent enrolment: <br/>
<img src="https://imgur.com/AGkFGcX.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />


<h2>Phase 4: Generating Security Events on the Kali linux Virtual Machine </h2>
<br /> 
To verify that the agent is working correctly, you can generate some security-related events on your Kali VM. To do this, we will use Nmap. <br /> 
Nmap (Network Mapper) is a free and open-source utility that scans networks to identify host, services, and vulnerabilities. It is designed to discover hosts and services on a computer network, thus creating a “map” of the network.  <br />
Nmap can be used to scan hosts for open ports, determine the operating system and software running on the target system, and gather other information about the network.<br>
                                                                                                               Follow these steps; <br />    
  1.  If you’re not specifically using Kali linux, install Nmap on the Linux Virtual Machine.
    Open a new Terminal and run this command to install it: sudo apt-get install nmap. 
    Nmap already comes preinstalled in Kali. <br />    
  2.  Run a scan on Kali machine by running the command: sudo nmap <vm-ip>. 
     You can also run a scan of your host machine if you place your Kali VM on a “bridged” network.
<img src="https://imgur.com/rK9Vy1b.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />
  3.  Nmap scan generates several security events, such as the detection of open ports and the identification of services running on those ports. Let run a few more Nmap scans (“nmap -sS <ip address>”, “nmap -sT <ip address>”, “nmap -p- <ip address>”etc..”) and see results
 <img src="https://imgur.com/u6Ko9tr.png" height="80%" width="80%" alt="Building a Cybersecurity Lab Steps"/>
<br />
<br />


<h2>Phase 5: Generating Security Events on the Kali linux Virtual Machine </h2>
<br /> 
We will begin querying and analyzing the logs in the SIEM now that we have forwarded data from the Kali VM to the SIEM  <br/> 
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
