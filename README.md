## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

# ![~/Project-13/diagrams/Elk-diagram.png]

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

 # - [metricbeat.yml] (etc/ansible/files/metricbeat.playbook.yml)
 # - [pentest.yml] (etc/ansible/pentest.yml)
 # - [elk.yml] (etc/ansible/elk.yml)  
 # - [filebeat.yml] (etc/ansible/files/metricbeat.playbook.yml)

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly __availablity___, in addition to restricting __access___ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

# The aspect of security that the load balancer protects is the systems by shifting traffic to metigate DDoS attacks.
# The advantage of a jumpbox is that it gives secure access to different recourses throgh SSH and private shared keys.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the __data___ and system _logs____.
- _TODO: What does Filebeat watch for?_

# Filebeat forwards, centraliza log data and monitors the log files or location that is specified to collect logs events and sends them either to elasticsearch or logstash for indexing 

- _TODO: What does Metricbeat record?_

# Metricbeat takes the metric and statistics that it collects and sends them to the output that is specified such as eleasticsearch or logstash. metricbeat helps monitor servers by recieveing metrics from the system and services runing in the server such as Apache.  

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.1.0.4   | Linux            |
| Web 1    | Webserver| 10.1.0.5   | Linux            |
| Web 2    | Webserver| 10.1.0.6   | Linux            |
| Elk      | logging server | 10.3.0.4   | Linux      |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the __Elk___ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _TODO: Add whitelisted IP addresses_

# 20.92.242.106

Machines within the network can only be accessed by jumpbox_____.
- _TODO: Which machine did you allow to access your ELK VM? What was its IP address?_

# Jumpbox Public IP (13.90.78.82)

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes       SSH-22    |10.1.0.4              | 
| Web 1    | Yes       SSH       |10.1.0.5              |
| Web 2    | Yes       SSH       |10.1.0.6
 ELK server  Yes    Kibana -5601  10.3.0.4            |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _TODO: What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- _TODO: In 3-5 bullets, explain the steps of the ELK installation play. E.g., install Docker; download image; etc._
 
# - ansible-playbook pentest.yml
# - ansible-playbook filebeat-playbook.yml
# - ansible-playbook metricbeat-playbook.yml
# - ansible-playbook install-elk.yml

# - Check for docker (install/Update)
# - Check for python3-pip (install/Update)
# - install Docker module
# - Download and lauch docker elk container 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](~/Project-13/diagram/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

 # - Web 1: 10.1.0.5
 # - Web 2: 10.1.0.6
 # - jumpbox: 10.1.0.4

We have installed the following Beats on these machines:
- _TODO: Specify which Beats you successfully installed_
 # - Web 1
 # - Web 2
 # - Elk server
 # - Metricbeat
 # - Filebeat

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

# Filebeat allows us to collect system logs such as tracking user logins and activities.

# Metricbeat allows us to collect Machine health and performance data such as CPU Usage, RAM usage and network usage

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the ___Filebeat__ file to __filebeat-config,yml___.
- Update the __filebeat.yml___ file to include...
- Run the playbook, and navigate to http://20.92.242.106:5601/app/kibana#/home___ to check that the installation worked as expected.

_TODO: Answer the following questions to fill in the blanks:_
- _Which file is the playbook? Where do you copy it?_

# Metricbeat-playbook.yml and Filebeat-playbook.yml copied to (etc/ansible/files). 

- _Which file do you update to make Ansible run the playbook on a specific machine? 

# /etc/ansible/host and add the server and IP addresses 

How do I specify which machine to install the ELK server on versus which to install Filebeat on?_

# In order to specify which machine to install the elk sercer vs to istall filebeat on is by seperating the groups such as the webervers and the IPs which will be used to create filebeat. Elk servers has the IP address of the VM which will install ELK. 

- _Which URL do you navigate to in order to check that the ELK server is running?

# SSH sysadmin@10.3.0.4
# http://20.92.242.106:5601/app/kibana#/home

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
