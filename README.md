# RMIT-cybersecurity-Design-Implement-network-secuirty
RMIT Cert 4 Cybersecuirty Identify Network Security Threats


# Summary and Purpose of Assessment
This assessment is designed to allow the student to demonstrate their skills and knowledge in the undertaking of a security threat assessment for an existing network architecture. This requires the student to demonstrate the following:

* Examine modern network security threats and attacks
* Investigate wireless security vulnerabilities


# Assessment Instructions
Students are required to review existing network topologies and security solutions and to identify the range of security risks to the organisation, and to design and implement a Wireless Local Area Network (WLAN) proxy server implementing Application Service Redirection (ASR).


# What
The following tasks must be completed in this assessment:

You have recently been employed as a Cyber Security Consultant for IT Assurance Services. IT Assurance Services specialises in the provision of ICT services to a range of small and medium enterprises, including the conduct of cyber security vulnerability assessments and the subsequent design and implementation of risk mitigation solutions to secure client systems.

# Task 1

Your employer has asked you to review the existing network infrastructure for their client Koko Pty Ltd, to identify security issues with their existing network infrastructure.
Koko Pty Ltd have also identified that they have a risk relating to continuity of services during upgrades and device failure. In addition to the detailed threat report, they have requested that you update their network topology to allow for secure fallover and redundancy.

For your submission you will provide the following files:
* CISCO Packet Tracer Files
* Existing Network Topology Threat Report

1.	Review the below network design for Koko Pty Ltd and complete a threat report based on the existing network topology and configuration:
   
![image](https://github.com/Jasmine-108/RMIT-cybersecurity-Design-Implement-network-secuirty/assets/151819725/169074b8-e09d-4b93-b126-a5ff622fda3d)

  a. Identify the network security architecture in place within the existing topology and identify at least 10 security issues associated with the existing network setup. For each of these security issues you must provide a recommended solution for rectifying the security vulnerability. This must include a combination of tools and procedures to mitigate the vulnerabilities.
  
  1. **OSPF**
      - The main office router is advertising to the ISP, there is no encryption between the routers and no passive interface in the internal network, this is an issue because without any encryption the data is open to anyone able to intercept
      - The solution is to create a passive interface for the routers between the switches
      - Remove the ISP connection from the OSPF
      
  2. **No proxy**
      - Without a proxy you cant stop employees from accessing malicious websites if an employee was to use access one of those sites and download malware it can spread on the system affecting the business as a whole
      - create a proxy server for wifi traffic and wired traffic and attatch it to the dns

  3. **Network isn’t segmented**
      - Without proper network segmentation if an attacker was to access just one part of the network that means that they will have access to the whole network and can freely move around systems
      - create a segment using vlans 10 and 20 from the S2 switch

  4. **DHCP needs to be moved**
      - The DHCP is located within servers associated with external activity this is an issue because it leaves the DHCP vulnerable to attacks such as DHCP starvation attack from external devices meaning that legit users in the company won’t be able to access the internet. Also, when a DMZ is established in that area employees won’t be able to reach the DHCP meaning there will be no internet
      - DHCP needs to be relocated to be with active directory and deep inside of the lan network such as the bottom side of the diagram

  5. **DNS is in the wrong spot**
      - The DNS is in the same subnetwork as the guest wifi network making the DNS vulnerable as any guests are able to log into this network, with access the attacker can do a DNS spoofing attack meaning they can alter records to redirect traffic to fraudulent sites
      - Needs to be moved to be with active directory
   
  6. **No TFTP backups**
      - If the router fails and needs to be recreated without a backup you would have to manually redo all the configurations but with a TFTP backup you can quickly upload all the configurations
      - Create a TFTP server in a already secure server space such as the DNS or DHCP

  7. **No AAA authentication**
      - Without AAA authentication anyone will be able to access the routers and change the configuration as they please
      - Configure AAA on the routers with with RADIUS or TACACS+ protocols

  8. **No ips on the main office router**
      - Without an IPS the router is vulnerable to any and all attacks and there is no way for the router to stop them from happening and alert you that they are happening
      - Install IPS to the main office router using SNORT or any other IPS

  9. **No firewall on the main office router**
      - Without the firewall the main office router is basically open from the outside it would be like leaving the wide open for anyone to walk in
      - Configure a demilitarized zone (DMZ) for the FTP, email and web server
      - Configure a Zone based Policy Firewall (ZPF) on the router allowing internal hosts access to external resources and blocking external hosts from accessing internal resources

  10. **Needs a vpn**
      - If an employee is to access sensitive company documents over a public wifi network for example in a cafe then all the data they send over will be unencrypted leaving them susceptible to a man in the middle attack and having information stolen
      - Install a VPN to the main office router

  b. Provide an overview of the following types of security threats and attacks. For each of these threats and attacks provide an explanation of what they are, how they can impact on the organisation, and any vulnerabilities within the existing network infrastructure and configuration that provide a risk exposure to the organisation:

  1. Trojans
     - A type of malware that disguises itself as legitimate software when installed gains remote access to the computer
       - A trojan can have a negative impact on an organization because:
           - Loss of data
           - Network attacks such as a denial of service
           - Disruption to the business

  3. Spoofing
     - When an attacker attempts to impersonate another entity such as a website, email or more to gain access to company systems
       - The same set of threats this holds to an organisation is present, data loss, disruption and damage to the companies reputation
           
  5. Password attacks
     - attempts to crack a user’s password carried out using automated tools or by attempting to trick a user into revealing their password
       - The same impacts to the organisation are the same with the others
         
  7. Ransomware
     - A type of malware that encrypts a user’s data and demands ransom payment to decrypt it
       - Data loss, disruption and financial loss are significant impacts within the organisation

  c. For each of the threats and attacks identified in 1b, provide recommended solutions for how these can be mitigated. These recommendations do not need to be limited to the existing network infrastructure and configuration as you will be redesigning this in future steps. Ensure that you identify the tools and procedures that will need to be implemented to minimise the risk.
    - To mitigate these threats from happening you can:
      - Educate employees about identifying and avoiding malicious websites, or phishing emails
      - Enforce usage of strong passwords and multi factor authentication
      - Regularly keep software and systems updated to protect against known vulnerabilities
      - Implement security controls such as firewalls and IPS/IDS
      - Use monitoring tools to view security logs
      - Use antivirus and keep it up to date
      - Implement web and email filtering
      - Keep regular backups

# Task 2

Your employer has asked you to review the existing network infrastructure for their client Koko Pty Ltd, to identify security issues with their existing network infrastructure.

Koko Pty Ltd have also identified that they have a risk relating to continuity of services during upgrades and device failure. In addition to the detailed threat report, they have requested that you update their network topology to allow for secure fallover and redundancy.


2.	Setup a secure fallover and redundancy system to ensure continuity of services for Koko Pty Ltd’s network.
   
  a.	Setup Hot Standby Router Protocol (HSRP) by adding two 1941 routers in between the main router and the customer network switch as shown in the topology below:

 ![image](https://github.com/Jasmine-108/RMIT-cybersecurity-Design-Implement-network-secuirty/assets/151819725/38c1a79f-42b0-42a6-9bd5-1af60f2c6f59)

On both routers configure a Virtual IP of 192.168.30.1. On HSRP1 configure the HSRP priority value to 110. Ensure that you share new networks under OSPF10. Test failover by using a continuous ping (ping-t) from Customer Web Server to Main Office Router and removing the cable from int G0/0 on HSRP1.

(Refer to assesment HSRP.pkt file REQUIRES PACKET TRACER)

# Task 3

Now that the threat report has been completed, Koko Pty Ltd want to implement a solution to allow for visitors and guests to the site office to connect to a wireless internet service. For security reasons your employer has specified that you are required to set this up using a proxy server implementing Application Service Redirection (ASR).

3.	Build the WLAN proxy server environment incorporating ASR which allows for secure guest access to Koko Pty Ltd’s internet service whilst protecting organisational data.

  a.	Using CISCO Packet tracer, create the WLAN architecture for implementation within the Koko Pty Ltd network environment. Within your WLAN Proxy Server Specifications document provide a description of the WLAN architecture and how it fits within the existing network topology.

![image](https://github.com/Jasmine-108/RMIT-cybersecurity-Design-Implement-network-secuirty/assets/151819725/9e9bb850-a999-46ab-bdd5-e49497d0be6f)

  b. Using the physical equipment in the lab environment, configure a WLAN device to allow for guest access. Within your WLAN Proxy Server Specification document describe the types of authentication and association methods used to secure the WLAN device. Outline the strengths and weaknesses of implemented authentication.
  
  Proxy Server Specification:
  
  - Make sure sites are being blocked Look at what sites people are going too and if they are inappropriate
  - Make sure users have the correct permissions set
  - Block new inappropriate or vulnerable sites

  c. Create a Proxy in a physical lab enviroment
  
  (REFER TO ASSESSMENT DOCUMENT TO SEE SCREENSHOTS)

# TASK 4

Now that the WLAN Proxy Server has been implemented, you are required to conduct a test of a colleague’s setup and configuration. This is comprised of two parts, the development of a WLAN security checklist and the use of tools to discover and interrogate the WLANs implemented by colleagues.

4.	Conduct an evaluation and test of a colleague’s WLAN and proxy configuration.

a.	Create a WLAN security checklist. Use it to check the security of the WLAN and proxy configuration. This will require that you observe the setup and configuration and that you ask questions of your colleague to complete the security assessment.
  
specification document:
  - Check for rouge wireless hotspots
  - Check all potential security attacks
  - Run some tests to see if VLANs are correctly running
  - Check the proxy server

b.	Give a brief description wifi cracking tool

  **Aircrack-ng:**

  Aircrack-ng is a networking software suite of tools to assess WiFi network security, the suite consists of a detector, packet sniffer and  is capable of cracking WEP and WPA/WPA2-PSK keys  as well as monitor and attack wireless networks

