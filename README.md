## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the yml and configuration file may be used to install only certain pieces of it, such as Filebeat.

 Ansible root@azureuser:~# nano my-playbook1.yml
 Filebeat : root@azureuser:/etc/ansible/roles# nano filebeat-playbook.yml
 Metricbeat :root@azureuser:/etc/ansible/files# nano metricbeat-config.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
 - Beats in Use
 - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.
-  What aspect of security do load balancers protect? Web Security
-   What is the advantage of a jump box? Automation, Security, Network Segmentation

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- What does Filebeat watch for? Filebeat monitors the log files or locations that you specify, collects log events, and forwards them either to Elasticsearch or Logstash for indexing.
- What does Metricbeat record? Metricbeat takes the metrics and statistics that it collects and ships them to the output that you specify, such as Elasticsearch or Logstas
The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address              | Operating System |
|----------|----------|-------------------------|------------------|
| Jump Box | Gateway  | 10.0.0.1                | Linux            |
| Web 1    |Web Server| 10.0.0.5                | Linux            |
| Web 2    |Web Server| 10.0.0.6                | Linux            |
| Elk vm   |Elk Server| 10.1.0.4/104.209.138.236| Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the ELK Server machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Jump-Box-Provisioner IP: 10.0.0.4 via ssh port 22

Workstation public IP via port TCP 5601 ======= Only the _____ machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Machines within the network can only be accessed by _____.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses             |
|----------|---------------------|----------------------------------|
| Jump Box | No                  | MyPublicIPAddress on SSH 22      |
|  Web 1   | No                  |  10.0.0.4 on SSH 22              |
|  Web 2   | No                  |  10.0.0.4 on SSH 22              |
| Elk      | No                  |MyPublicIPAddress using Port 5601 |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because Ansible lets you quickly and easily deploy multitier apps. You won't need to write custom code to automate your systems; you list the tasks required to be done by writing a playbook, and Ansible will figure out how to get your systems to the state you want them to be in

The playbook implements the following tasks:

 -- Specify a different group of machines as well as a different remote user

  name: Config elk VM with Docker
  hosts: elk
  remote_user: sysadmin
  become: true
  tasks:
  
 -- Install the following services:
  docker, which is Docker python pip module
 'docker .io
  python3-pip
  
 --Launching and Exposing the container with these published ports:
  5601:5601, 9200:9200`
  
The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![image](https://user-images.githubusercontent.com/81271596/112738307-aafeeb00-8f2f-11eb-8fcc-31544de3d350.png)

![image](https://user-images.githubusercontent.com/81271596/112738323-e00b3d80-8f2f-11eb-94e8-a7e846422301.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
 Web1 : 10.0.0.5 
 Web2 : 10.0.0.6

We have installed the following Beats on these machines:
ELK Server, Web1 and Web2
The ELK Stack Installed are: FileBeat and MetricBeat

These Beats allow us to collect the following information from each machine:
Filebeat: log events
Metricbeat: metrics and system statistics

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the _____ file to _____.
- Update the _____ file to include...
- Run the playbook, and navigate to ____ to check that the installation worked as expected.

 Answer the following questions to fill in the blanks:
 
 Which file is the playbook? Where do you copy it?  
 yml /etc/ansible
  
 Which file do you update to make Ansible run the playbook on a specific machine? 
 How do I specify which machine to install the ELK server on versus which to install Filebeat on? 
 config file yml
 
 Which URL do you navigate to in order to check that the ELK server is running?
 http://[your.ELK-VM.External.IP]:5601/app/kibana

As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc
root#: ansible-playbook playbook.yml

