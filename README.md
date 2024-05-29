# SOC-Automation-Project

# Introduction

In the current cybersecurity landscape, the sophistication and frequency of cyber threats are escalating, necessitating robust and efficient security measures. To address this challenge, automating Security Operations Center (SOC) processes has become essential. This project aims to demonstrate a comprehensive SOC automation setup using Wazuh Manager and TheHive, both deployed on Ubuntu 22.04 servers in the cloud https://www.digitalocean.com/. Additionally, a Wazuh agent and Sysmon (System Monitor) are installed on an on-premises Windows 10 client machine to ensure detailed security monitoring. 

Wazuh Manager serves as a robust, open-source security monitoring platform that offers threat detection, integrity monitoring, incident response, and compliance management. It communicates with the Wazuh agent installed on the Windows 10 machine, which collects and sends security event data to the cloud-based Wazuh Manager. It seamlessly integrates with Shuffle, a powerful security orchestration, automation, and response (SOAR) tool that automates repetitive tasks, and TheHive, an incident response platform designed to manage security events efficiently. Sysmon enhances this setup by providing detailed information about process creations, network connections, and file changes. By leveraging the synergy of these tools, the project illustrates how SOC automation can significantly enhance an organization's ability to detect, investigate, and respond to cyber threats swiftly and accurately.

To simulate a real-world scenario, the Windows 10 machine will be subjected to a Mimikatz attack, a well-known tool used for extracting credentials from Windows systems. The Wazuh agent will detect this attack and report it to the Wazuh Manager. This setup will provide a realistic scenario to test and demonstrate the SOC's automated capabilities in handling real-world cyber threats.

Integrating Shuffle, a powerful Security Orchestration, Automation, and Response (SOAR) platform, enhances the SOC's automation capabilities. We registered an accound with Shuffle at https://shuffler.io/ and connected to both Wazuh Manager and TheHive, facilitating seamless data flow and incident management. When the Mimikatz attack is detected, Shuffle will orchestrate the response by sending an alert to TheHive, an incident response platform designed to efficiently manage and investigate security events.

Furthermore, Shuffle will automatically send an email notification about the Mimikatz attack to the SOC analyst. This real-time alert ensures that the SOC team is promptly informed, enabling them to take swift and appropriate action.

Through this project, we aim to highlight the benefits of SOC automation, such as accelerated incident response, enhanced detection accuracy, and optimized resource utilization. By leveraging various security operations and the synergy between Wazuh Manager, TheHive, and Shuffle, organizations can significantly strengthen their cybersecurity defenses, can better protect their assets  and maintain a resilient security posture in the face of evolving cyber threats. 


## Objective
[Brief Objective - Remove this afterwards]

The Detection Lab project aimed to establish a controlled environment for simulating and detecting cyber attacks. The primary focus was to ingest and analyze logs within a Security Information and Event Management (SIEM) system, generating test telemetry to mimic real-world attack scenarios. This hands-on experience was designed to deepen understanding of network security, attack patterns, and defensive strategies.

### Skills Learned
[Bullet Points - Remove this afterwards]

- Advanced understanding of SIEM concepts and practical application.
- Proficiency in analyzing and interpreting network logs.
- Ability to generate and recognize attack signatures and patterns.
- Enhanced knowledge of network protocols and security vulnerabilities.
- Development of critical thinking and problem-solving skills in cybersecurity.

### Tools Used
[Bullet Points - Remove this afterwards]

- Security Information and Event Management (SIEM) system for log ingestion and analysis.
- Network analysis tools (such as Wireshark) for capturing and examining network traffic.
- Telemetry generation tools to create realistic network traffic and attack scenarios.

## Steps
drag & drop screenshots here or use imgur and reference them using imgsrc

Every screenshot should have some text explaining what the screenshot is about.

Example below.

*Ref 1: Network Diagram*
-->
