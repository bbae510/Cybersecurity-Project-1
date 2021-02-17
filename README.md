## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

**Note**: ELK Stack Server Diagram

![network diagram](Diagrams/Cloud_Security(azure).png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Images file may be used to install only certain pieces of it, such as Filebeat.

  - _https://github.com/bbae510/Cybersecurity-Project-1/blob/main/Images/filebeat_playbook.png_

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly reliable, in addition to restricting access to the network.
- Load Balancers protect against DoS attacks. The advantage of the jump box is that it restricts access to one administrator. Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the actual machines and system logs.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
-  Filebeat is a logging agent installed on the machine generating the log files, tailing them, and forwarding the data to either Logstash for more advanced processing or directly into Elasticsearch for indexing. Specifically, it logs information about the file system, including which files have changed and when.
- Metricbeat is a lightweight shipper that you can install on your servers to periodically collect metrics from the operating system and from services running on the server. Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash.

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

|         Name        | Function         | IP Address    | Operating System |
|:-------------------:|------------------|---------------|------------------|
| Jumpbox-Provisioner |      Gateway     | 20.51.104.158 |       Linux      |
|        Web-1        |  DVWA Container  |   10.0.0.10   |       Linux      |
|        Web-2        |  DVWA Container  |   10.0.0.11   |       Linux      |
|        Web-3        |  DVWA Container  |   10.0.0.12   |       Linux      |
|        ELK-VM       | Configuration VM |    10.1.0.4   |       Linux      |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box (provisioner) machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Whitelisted IP Addresses:
- 76.172.68.15 (personal Public IP address)

Machines within the network can only be accessed by accessing the DVWA containers in the *Jumpbox-Provisioner* Virutal Machine.
- The only machines that can access the ELK server are personal machine (Public IP-76.172.68.15) and the Jumpbox-Provisioner VM (Public IP-20.51.104.158) through a peering connection

A summary of the access policies in place can be found in the table below.

|         Name        | Publicly Accessible |         Allowed IPs         |
|:-------------------:|:-------------------:|:---------------------------:|
| Jumpbox-Provisioner |         yes         | 20.51.104.158, 76.172.68.15 |
|        Web-1        |          no         |        20.51.104.158        |
|        Web-2        |          no         |        20.51.104.158        |
|        Web-3        |          no         |        20.51.104.158        |
|        ELK-VM       |          no         | 20.51.104.158, 76.172.68.15 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- servcies running can be limited, system installation and update can be streamlined, and processes become more replicable.

The playbook implements the following tasks:
- Install Docker
- Download Image
- Configure container
- Create playbook to install container with docker and Filebeat and Metricbeat.
- Run playbook to launch the container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance. 

![docker ps -a](Images/elkserver_docker.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 (Private IP: 10.0.0.10)
- Web-2 (Private IP: 10.0.0.11)
- Web-3 (Private IP: 10.0.0.12)

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing. When Filebeat starts logging, it will represent data such as system log events in a dashboard:
![filebeat](Images/filebeat_ss.png)

- Metricbeat periodically collect metrics from the operating system and from services running on the server. Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstash. Metricbeat will display information such as container CPU usage as follows:
![metricbeat](Images/metricbeat_ss.png)

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
- _Which URL do you navigate to in order to check that the ELK server is running?

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._

