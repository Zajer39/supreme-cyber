# supreme-cyber
Cybersecurity projects and files
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)
  ~/Downloads/Cloud_Network_Diagram.drawio.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - _TODO: install-elk.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly effective, in addition to restricting traffic to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_
	Load balancers protect servers from being overworked and distributing traffic only allowed. The advantage of a jump box it is a gateway of accessing other machines. It only allows connections from specific IP adresses. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the file system and system metrics.
- _TODO: What does Filebeat watch for?
	Filebeat wathces and monitors the log files or locations that users specify.
- _TODO: What does Metricbeat record?_
	Metricbeat records metrics from the os.

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| Elk      | webserver| 10.1.0.4   | Linux            |
| Web 1    | Webserver| 10.0.0.5   | Linux            |
| web 2    | Webserver| 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jump-box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_
	IP:20.106.156.8

Machines within the network can only be accessed by private key (ssh'd).
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_
	The ansible container was allowed acces to the ELK VM. The IP address is 168.61.209.175

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes/No              | 99.34.23.23          |
| Web-1    | No                  | 20.106.156.8         |
| Web-2    | No                  | 20.106.156.8         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_
	The main advantage of automating configuriation with Ansible is it allows the configuration to be predictable and consistent. 
	

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._ 
- Install docker
- Download image
- Start/Attach to ansible container 
- Config playbook with tasks
- Run install-elk.yml (command: ansible-playbook)

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: Web-1 10.0.0.5 
         Web-2 10.0.0.6

We have installed the following Beats on these machines:
- _TODO: Filebeat and Metricbeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._
         Filebeat collects system log and determine which logs have been changed and when in the file system. It organizes them and sends them to Logstash and Elasticsearch.
         Metricbeat collects information about the target servers and how it is performing. It can send analyze and send the data to other places if needed. 
         
### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the config file to the webservers (dvwa) .
- Update the config file to include the server host (private ip address).
- Run the playbook, and navigate to the ip address to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_
	The config file and it is copied to the webservers
- _Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?_
	I update the hosts file to specify where to run the playbooks (be sure to specify in the playbook). I specify which machines by using the private ip address. 	
- _Which URL do you navigate to in order to check that the ELK server is running?
	I used the url http://168.61.209.175:5601/app/kibana to check if the ELK server was running. 

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
	To run the playbook the command is: ansible-playbook <name of playbook>
