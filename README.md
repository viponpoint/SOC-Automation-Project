# SOC-Automation-Project

# Introduction

In the current cybersecurity landscape, the sophistication and frequency of cyber threats are escalating, necessitating robust and efficient security measures. To address this challenge, automating Security Operations Center (SOC) processes has become essential. This project aims to demonstrate a comprehensive SOC automation setup using Wazuh Manager and TheHive, both deployed on Ubuntu 22.04 servers in the cloud https://www.digitalocean.com/. Additionally, a Wazuh agent and Sysmon (System Monitor) are installed on an on-premises Windows 10 client machine to ensure detailed security monitoring. 

Wazuh Manager serves as a robust, open-source security monitoring platform that offers threat detection, integrity monitoring, incident response, and compliance management. It communicates with the Wazuh agent installed on the Windows 10 machine, which collects and sends security event data to the cloud-based Wazuh Manager. It seamlessly integrates with Shuffle, a powerful security orchestration, automation, and response (SOAR) tool that automates repetitive tasks, and TheHive, an incident response platform designed to manage security events efficiently. Sysmon enhances this setup by providing detailed information about process creations, network connections, and file changes. By leveraging the synergy of these tools, the project illustrates how SOC automation can significantly enhance an organization's ability to detect, investigate, and respond to cyber threats swiftly and accurately.

To simulate a real-world scenario, the Windows 10 machine will be subjected to a Mimikatz attack, a well-known tool used for extracting credentials from Windows systems. The Wazuh agent will detect this attack and report it to the Wazuh Manager. This setup will provide a realistic scenario to test and demonstrate the SOC's automated capabilities in handling real-world cyber threats.

Integrating Shuffle, a powerful Security Orchestration, Automation, and Response (SOAR) platform, enhances the SOC's automation capabilities. We registered an accound with Shuffle at https://shuffler.io/ and connected to both Wazuh Manager and TheHive, facilitating seamless data flow and incident management. When the Mimikatz attack is detected, Shuffle will orchestrate the response by sending an alert to TheHive, an incident response platform designed to efficiently manage and investigate security events.

Furthermore, Shuffle will automatically send an email notification about the Mimikatz attack to the SOC analyst. This real-time alert ensures that the SOC team is promptly informed, enabling them to take swift and appropriate action.

Through this project, we aim to highlight the benefits of SOC automation, such as accelerated incident response, enhanced detection accuracy, and optimized resource utilization. By leveraging various security operations and the synergy between Wazuh Manager, TheHive, and Shuffle, organizations can significantly strengthen their cybersecurity defenses, can better protect their assets  and maintain a resilient security posture in the face of evolving cyber threats. 


## Objective

The objective of this SOC automation project is to enhance the efficiency and effectiveness of security operations by integrating advanced tools and automating incident response. The project involves setting up Wazuh Manager and TheHive servers in the cloud on Ubuntu 22.04, alongside installing a Wazuh agent and Sysmon on Windows 10 client machine which was configured on virtual box. The Wazuh agent reports security events to the cloud-based Wazuh Manager. To demonstrate the system's capabilities, a Mimikatz attack will be executed on the Windows 10 machine. Shuffle, our SOAR platform, will be registered and connected to Wazuh Manager and TheHive. Upon detecting the attack, Shuffle will send an alert to TheHive and automatically email the SOC analyst, ensuring prompt awareness and response. This setup aims to showcase the power of automation in improving incident response times, accuracy, and overall security posture.

### Skills Learned

- Applying real-world cybersecurity practices and tools to protect an organization’s digital assets.
- Gaining practical experience in setting up and managing a SOC environment.
- Ensuring seamless integration and communication between various security tools and platforms.
- Configuration of Shuffle as a SOAR platform and connecting it with Wazuh Manager and TheHive.
- Installing and configuring Wazuh Manager for centralized security monitoring.
- Integrating Sysmon to provide detailed event logging and monitoring capabilities.
- Setting up the Wazuh agent on a Windows 10 client machine to report security events.
- Configuring Wazuh to detect and alert on suspicious activities and potential breaches.
- Simulating a Mimikatz attack on a Windows 10 machine to test the security setup.
- Automating incident response workflows to enhance efficiency and reduce response times.
- Configuring automated email notifications to inform SOC analysts about detected incidents promptly.

### Tools Used

- A comprehensive open-source security monitoring tool (Such as Wazuh Manager) that provides threat detection, integrity     checking,      incidence response, and compliance management.
- An incident response platform designed to efficiently manage and investigate security events (Such as TheHive), integrated with Wazuh     to handle alerts and incidents.
- A post-exploitation tool (such as Mimikatz) used to test the detection capabilities of the SOC setup by simulating an attack that       
  attempts to extract credentials from the Windows 10 machine.
- A Security Orchestration, Automation, and Response (SOAR) platform (such as Shuffle) that automates workflows and integrates with Wazuh   Manager and TheHive to manage and respond to security incidents efficiently.
- The operating system (Ubuntu 22.04) used for setting up the cloud-based Wazuh Manager and TheHive servers, providing a secure and 
  stable environment for hosting these applications.
- A Windows system service and device driver (Sysmon) that logs system activity to the Windows event log, providing detailed information    on process creations, network connections, and file changes.

## Steps
drag & drop screenshots here or use imgur and reference them using imgsrc

Every screenshot should have some text explaining what the screenshot is about.

Example below.

*Ref 1: Network Diagram*
-->
