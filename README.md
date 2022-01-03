# Project13-Elk-Stack
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![image](https://user-images.githubusercontent.com/89866159/147961841-e73dd6da-f35d-4cf8-8243-a399cda4ed5f.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the elk.yml file may be used to install only certain pieces of it, such as Filebeat.

root@ansible$: elk.yml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly _____, in addition to restricting _____ to the network.
- _TODO: What aspect of security do load balancers protect? What is the advantage of a jump box?_

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the _____ and system _____.
- _TODO: What does Filebeat watch for?_
- _TODO: What does Metricbeat record?_

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.1.4  | Linux                 |
| Web 1    | Gateway  | 10.0.0.8  | Linux                 |
| Web 2    | Gateway  | 10.0.0.6  | Linux                 |
| Web 3    | Gateway  | 10.0.0.7  | Linux                 |
| ELK-SERVER1| Gateway| 10.3.0.4  | Linux                 |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Machines within the network can only be accessed by Jumpbox.

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box  | Yes                |99.82.228.92/98.154.33.226|
|ELK-SERVER1| no                |99.82.228.92/98.154.33.226|
| Web 1     | no                |99.82.228.92/98.154.33.226|
| Web 2     | no                |99.82.228.92/98.154.33.226|
| Web 3     | no                |99.82.228.92/98.154.33.226|

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
It is more time efficient and you are allowed to configure more than one machine at once using root privilages from Ansible. 
The playbook implements the following tasks:
 - Installation of Pip3 
 - Docker.io
 - Configures the machine in order to use Docker as a command that linux understands. 
 - Increase the machine's memory using : Command: sysctl -w vm.max_map_count=262144


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![image](https://user-images.githubusercontent.com/89866159/147965359-df54d464-5735-4892-8fa1-1b9776bf6470.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
| Web 1     | 10.0.0.8    |
| Web 2     | 10.0.0.6    |
| Web 3     | 10.0.0.7        |
We have installed the following Beats on these machines:

Filebeat & Metricbeat have been installed on to the Webservers hosts which contains machines WEB1, WEB2, & WEB3. 

These Beats allow us to collect the following information from each machine:
- Filebeat allows us to collect system log data which allows us to collect log data from a specific locations which then transfers the informaiton to Elasticsearch. 
- Metricbeat gathers information and services from operating systems as well as servers. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the playbook file to our /etc/ansible directory.
- Update the config file to include the applicable servers either WEBSERVERS OR ELK
- Run the playbook, and navigate to ELK-SERVER1 to check that the installation worked as expected.

root@ansible:~#filebeat-playbook.yml you will copy the config file to /etc/ansible/file/filebeat-configuration.yml
In order to specify a machine to Install the elk server you will need to edit the etc/ansible/hosts file and add the machine to either [Webservers] or [ELK] you will also need to edit your playbook and specify which of the two servers you'd like to run the playbook on. 
in order to check that Kibana is functioning you will need to enter your ip address:5601/app/kibana#/home
http://104.40.35.10:5601/app/kibana#/home

ansible-playbook elk.yml
ansible-playbook filebeat-playbook.yml. 

Please see screenshots* :) 
