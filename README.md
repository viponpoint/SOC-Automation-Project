# SOC-Automation-Project

# Introduction

In the current cybersecurity landscape, the sophistication and frequency of cyber threats are escalating, necessitating robust and efficient security measures. To address this challenge, automating Security Operations Center (SOC) processes has become essential. This project aims to demonstrate a comprehensive SOC automation setup using Wazuh Manager and TheHive, both deployed on Ubuntu 22.04 servers in the cloud https://www.digitalocean.com/. Additionally, a Wazuh agent and Sysmon (System Monitor) are installed on an on-premises Windows 10 client machine to ensure detailed security monitoring. 

Wazuh Manager serves as a robust, open-source security monitoring platform that offers threat detection, integrity monitoring, incident response, and compliance management. It communicates with the Wazuh agent installed on the Windows 10 machine, which collects and sends security event data to the cloud-based Wazuh Manager. It seamlessly integrates with Shuffle, a powerful security orchestration, automation, and response (SOAR) tool that automates repetitive tasks, and TheHive, an incident response platform designed to manage security events efficiently. Sysmon enhances this setup by providing detailed information about process creations, network connections, and file changes. By leveraging the synergy of these tools, the project illustrates how SOC automation can significantly enhance an organization's ability to detect, investigate, and respond to cyber threats swiftly and accurately.

To simulate a real-world scenario, the Windows 10 machine will be subjected to a Mimikatz attack, a well-known tool used for extracting credentials from Windows systems. The Wazuh agent will detect this attack and report it to the Wazuh Manager. This setup will provide a realistic scenario to test and demonstrate the SOC's automated capabilities in handling real-world cyber threats.

Integrating Shuffle, a powerful Security Orchestration, Automation, and Response (SOAR) platform, enhances the SOC's automation capabilities. I registered an account with Shuffle at https://shuffler.io/ and connected to both Wazuh Manager and TheHive, facilitating seamless data flow and incident management. When the Mimikatz attack is detected, Shuffle will orchestrate the response by sending an alert to TheHive, an incident response platform designed to efficiently manage and investigate security events.

Furthermore, Shuffle will automatically send an email notification about the Mimikatz attack to the SOC analyst. This real-time alert ensures that the SOC team is promptly informed, enabling them to take swift and appropriate action.

Through this project, my aim was to highlight the benefits of SOC automation, such as accelerated incident response, enhanced detection accuracy, and optimized resource utilization. By leveraging various security operations and the synergy between Wazuh Manager, TheHive, and Shuffle, organizations can significantly strengthen their cybersecurity defenses, can better protect their assets  and maintain a resilient security posture in the face of evolving cyber threats. 


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

1.  The first step in this project was the drawing of the project diagram using
    https://app.diagrams.net/?src=about#Hviponpoint%2FSOC-Automation- Project%2Fmain%2FUntitled%20Diagram.drawio#%7B%22pageId%22%3A%22AONNASwHGbtUYUmjS9xI%22%7D

![Screenshot 2024-05-24 150250](https://github.com/viponpoint/SOC-Automation-Project/blob/main/Screenshot%202024-05-24%20150250.png)

2.  Download and install the virtual box in preparation for the creation of virtual machine to enable me to set up my Windows 10 client.
3.  Download the ISO file image for Windows 10 machine and then install it by following the installation and configuration process.
4.  Download Sysmon from https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon and then install it on Windows 10 client machine. Also, you need to download the Sysmon   
    configuration file (sysmonconfig.xml) from
    https://github.com/olafhartong/sysmon-modular and save it on your Windows 10 machine. Then install the configuration file.
5.  The set up of Wazuh manager using Digital Ocean (https://digitalocean.com/) as my cloud provider. Started with the creation of Wazuh server. End up creating two servers on 
    Digital Ocean, one for my Wazuh Ubuntu server and the other for TheHive Ubuntu server.
6.  Create firewall immediately so as not to get spammed by external scanners. Set your firewall Inbound Rules to such a way that only your public IP can access it for now. Connect the 
    firewall to both the Wazuh and TheHive machines.
7.  Installation of Wazuh through the Terminal. You can SSH into the Wazuh machine using Putty, and when in, you should apt-get update   
    and apt-get upgrade -y Wazuh. Then install Wazuh with the following commands curl -sO https://packages.wazuh.com/4.7/wazuh-install.sh 
    && sudo bash ./wazuh-install.sh -a   
8.  Installation of TheHive through the Terminal. You can SSH into TheHive machine using Putty, and when in, then you start the   
    installations. Before the installation of TheHive, you will have to install 3 difference prerequisite before TheHive installation. 
    First is Jave, Second is Cassandra, and third is ElasticSearch, and then TheHive installation comes in. Below are the installation        code:
    Install Java
    wget -qO- https://apt.corretto.aws/corretto.key | sudo gpg --dearmor  -o /usr/share/keyrings/corretto.gpg
    echo "deb [signed-by=/usr/share/keyrings/corretto.gpg] https://apt.corretto.aws stable main" |  sudo tee -a           
    /etc/apt/sources.list.d/corretto.sources.list
    sudo apt update
    sudo apt install java-common java-11-amazon-corretto-jdk
    echo JAVA_HOME="/usr/lib/jvm/java-11-amazon-corretto" | sudo tee -a /etc/environment 
    export JAVA_HOME="/usr/lib/jvm/java-11-amazon-corretto"
    
    Install Cassandra
    wget -qO -  https://downloads.apache.org/cassandra/KEYS | sudo gpg --dearmor  -o /usr/share/keyrings/cassandra-archive.gpg
    echo "deb [signed-by=/usr/share/keyrings/cassandra-archive.gpg] https://debian.cassandra.apache.org 40x main" |  sudo tee -a     
    /etc/apt/sources.list.d/cassandra.sources.list
    sudo apt update
    sudo apt install cassandra

    Install ElasticSearch
    wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch |  sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg
    sudo apt-get install apt-transport-https
    echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/7.x/apt stable main" |  
    sudo tee /etc/apt/sources.list.d/elastic-7.x.list
    sudo apt update
    sudo apt install elasticsearch

    Install TheHive
    wget -O- https://archives.strangebee.com/keys/strangebee.gpg | sudo gpg --dearmor -o /usr/share/keyrings/strangebee-archive-  
    keyring.gpg
    echo 'deb [signed-by=/usr/share/keyrings/strangebee-archive-keyring.gpg] https://deb.strangebee.com thehive-5.2 main' | sudo tee -a 
    /etc/apt/sources.list.d/strangebee.list
    sudo apt-get update
    sudo apt-get install -y thehive

9.  Configuration of TheHive so it can work smoothly and successfully. Start this by editing Cassandra configuration files through   
    nano/etc/cassandra/cassandra.yaml  ..Change the listen_address, the rpc_address and the seed_provider address to TheHive public IP 
    address. Then stop and start the service... systemctl start cassandra.service
    The next is the set up of Elasticsearch by editing it conf files through nano/etc/elasticsearch/elasticsearch.yml  ..I changed the   
    cluster.name to TheHive, the node.name to node-1, network host IP address changed to TheHive IP address, and the 
    cluster.initial_master_nodes to node-1 ...systemctl start elasticsearch , and then systemctl enable elasticsearch.

    The next is to set up TheHive by editing it configuration file through nano/etc/thehive/application.conf  .. But before that, ensure that TheHive user and group have access to /opt/thp file part.
    Type chown -R thehive:thehive /opt/thp
    The above will change owner to thehive user and group. To configure TheHive configuration file, type
    nano/etc/thehive/application.conf
    Change the hostname to the public IP of TheHive
    Change the Cluster-name = to the same name to changed it to previously
    Change application.baseUrl to the public IP of TheHive
    Save the above and then
    systemctl start thehive
    systemctl enable thehive

    That is the end of the configuration of TheHive
    You can then access TheHive dashboard with the IP of TheHive on port 9000. With the username: admin@thehive.local and the password: secret

10. Configuration of Wazuh. This will be done from Wazuh dashboard. We will Add Agent. Click on Add Agent and follow the steps.
    Copy the command from : Run the following commands to download and install the Wazuh agent
    Go to our Windows machine and open up Powershell, with administrative priviledges and then paste the copied command and press enter.
    You start the services by typing net start wazuhsvc
    Wazuh has been configured successfully.

11. Generation of telemetry containing Mimikatz from my Windows 10 machine and ensure it is being injected into Wazuh. Edit the Ossec.conf file on the Windows 10 machine to allow sysmon 
    to inject/forward events into Wazuh.
12. Download Mimikatz into the Windows 10 machine. But before doing that, disable Windows defender on the Windows 10 machine so as to allow the download of Mimikatz.
13. Run Mimikatz on the Windows 10 machine so as to generate the needed telemetry.
14. Wazuh manager will detect Mimikatz immediately.
15. You can also configure your own custom rule for originalFileName. The essence of this is, if an attacker decided to change the file name, let say, Mimikatz.exe to youaregreat.exe in 
    order to evade detection, the alert will still be triggered and attack detected by Wazuh manager.
16. Create an account in Shuffle at https://shuffler.io/
17. Create a new workflow in Shuffle and give it a name. Insert the webhook from the interface and then start the configuration of Wazuh to communicate with Shuffle from the Wazuh 
    manager CLI.
18. Go to the Windows 10 client machine and regenerate Mimikatz telemetry. Return to Shuffle interface and you will see the generated telemetry in Shuffle.
19. The workflow built on Shuffle in this project start with Mimikatz Alert being sent to Shuffle, then Shuffle receives Mimikatz Alert and extract SHA256 Hash from the file, and then 
    preceed to check 
    the reputation score of the Hash with VirusTotal. Then send the details to TheHive to create an Alert and as well send email to the SOC analyst to begin Investigation.
20. Pass the Hash value for the file by writing Regex then send it to VirusTotal to check the reputation score.


![Screen shot](https://github.com/viponpoint/SOC-Automation-Project/blob/main/Screenshot%20(78).png)
This is the set up of Wazuh manager using Digital Ocean as the cloud provider


![Wazuh Installation](https://github.com/viponpoint/SOC-Automation-Project/blob/main/WazuhInstallation.png)
                            The is the installation of Wazuh from CLI
                            

![TheHive Installation](https://github.com/viponpoint/SOC-Automation-Project/blob/main/TheHiveInstallation.png)
            This is the installation of Cassandra, Elasticsearch, and TheHive
            
            
![TheHive Configuration](https://github.com/viponpoint/SOC-Automation-Project/blob/main/TheHiveConfiguration.png)
        This is the configuration of Cassandra, Elasticsearch, and TheHive


![TheHive Conf2](https://github.com/viponpoint/SOC-Automation-Project/blob/main/TheHiveConf2.png)


![TheHive Status Active](https://github.com/viponpoint/SOC-Automation-Project/blob/main/TheHiveStatusActive.png)
              Elasticsearch, Cassandra and TheHive are all running perfectly on my Ubuntu machine
            
              
![Wazuh Client Add To Manager](https://github.com/viponpoint/SOC-Automation-Project/blob/main/WazuhClientAddToManager.png)
Wazuh client which is my Windows 10 machine is added to the Wazuh manager in the cloud as shown above


![Mimikatz Original Name1](https://github.com/viponpoint/SOC-Automation-Project/blob/main/MimikatzOriginalName1.jpeg)
I ran Mimikatz with the original name on Windows 10 machine so as to generate the needed telemetry


![Mimikatz detected](https://github.com/viponpoint/SOC-Automation-Project/blob/main/Mimikatz%20detected.png)


![Wazuh Disc Mimikatz](https://github.com/viponpoint/SOC-Automation-Project/blob/main/WazuhDiscMimikatz.png)
Mimikatz is detected immediately as shown in the Wazuh dashboard with all the necessary info 


![Original File Name Rule](https://github.com/viponpoint/SOC-Automation-Project/blob/main/OriginalFileNameRule.png)
Customized Wazuh rule to detect mimikatz.exe with the OriginalFileName even if the name is changed to something else


![Mimikatz Changed Name](https://github.com/viponpoint/SOC-Automation-Project/blob/main/MimikatzChangedName.jpeg)
I ran Mimikatz with the changed name on Windows 10 machine so as to generate the needed telemetry


![Wazuh Mimikatz Name Change](https://github.com/viponpoint/SOC-Automation-Project/blob/main/WazuhMimikatzNameChange.png)
Even when the name of the file was changed, Wazuh was still able to detect Mimikatz because I customized the rules to the OriginalFileName


![TheHive Detected Mimikatz1](https://github.com/viponpoint/SOC-Automation-Project/blob/main/TheHiveDetectedMimikatz1.png)
TheHive also detected Mimikatz

![TheHive Detected Mimikatz](https://github.com/viponpoint/SOC-Automation-Project/blob/main/TheHiveDetectedMimikatz.png)
TheHive detected Mimikatz

![ShuffleWorkFlow](https://github.com/viponpoint/SOC-Automation-Project/blob/main/ShuffleWorkFlow.png)
This is my Shuffle work flow



![Email Sent to Analyst](https://github.com/viponpoint/SOC-Automation-Project/blob/main/EmailSenttoAnalyst.png)
Email sent to SOC Analyst from Shuffle


![SOC Analyst Email](https://github.com/viponpoint/SOC-Automation-Project/blob/main/SOCAnalystEmail.png)
SOC analyst received an email with the topic Mimikatz Detected!

