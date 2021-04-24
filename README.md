# Project 1 - Setup systems on Azure cloud

This project is to setup infrastructure on Azure cloud

## Diagram
https://imgur.com/a/d5AZkP1

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

filebeat-playbook.yml

This document contains the following details:

  Description of the Topologu
  Access Policies
  ELK Configuration
    Beats in Use
    Machines Being Monitored
  How to Use the Ansible Build
  
## Description of the Topology
The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.
Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

  Load balancing protects the servers from a DoS attack. A load balancer distributes network or application traffic amongst the servers. One benefit of a jumpbox is that it provides a controlled means of acccess between your virtual machines from attackers.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system performance.
  log files monitored for Filebeat
  
The configuration details of each machine may be found below.
Note: Use the Markdown Table Generator to add/remove values from the table.

| Name        | Function          |  IP address        | Operating System   | 
| ----------- | ----------------- | ------------------ | ------------------ | 
| Jumpbox     | Gateway           | 10.0.1.4           | Linux ubuntu 18.04 | 
| DVWA-VM1    | VM                | 10.0.1.7           | Linux ubuntu 18.04 | 
| DVWA-VM2    | VM                | 10.0.1.8           | Linux ubuntu 18.04 | 
| DVWA-VM3    | VM                | 10.0.1.9           | Linux ubuntu 18.04 | 
| DVWA-VM4    | VM                | 10.0.1.10          | Linux ubuntu 18.04 |  
| ELK VM      | ElkStack          | 10.0.1.12          | Linux ubuntu 18.04 |  

## Access Policies
The machines on the internal network are not exposed to the public Internet.

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

72.84.225.151
Machines within the network can only be accessed by Port 22.

10.0.1.4
A summary of the access policies in place can be found in the table below.

| Name        | Publicly Accessible | Allowed IP Addresses  | 
| ----------- | ------------------  | --------------------- |
| Jumpbox     | No                  | 72.84.225.151         | 
| DVWA-VM1    | No                  | 10.0.1.4              |
| ELK Stack   | No                  | 10.0.1.4              |

## Elk Configuration
Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...

  Ansible can be run from the command line and will ensure our provisioning scripts run identically everywhere.
  
The playbook implements the following tasks:

  Increase/Decrease the memory on the ELK VM
  Install python-pip
  Install docker python module
  Download and launch docker elk stack
  
The following screenshot displays the result of running docker ps after successfully configuring the ELK instance.
  https://imgur.com/a/6wPlKYc
  
## Target Machines & Beats
This ELK server is configured to monitor the following machines:

  DVMA-VM1
  DVMA-VM2
  DVMA-VM3
  DVMA-VM4
  
We have installed the following Beats on these machines:

  filebeat-7.6.1-amd64.deb
  
Filebeats allow us to collect the following information from each machine:

  Filebeat collects and forwards data from these machines and sends it over to Kibana for processing. This information can be viewed and monitored.
  
## Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned:

SSH into the control node and follow the steps below:

Copy the Filebeat-configuration.yml file to the ELK VM.
Update the hosts file to include webservers 10.0.1.7, 10.0.1.8, 10.0.1.9, 10.0.1.10
Run the playbook, and navigate to Kibana to check that the installation worked as expected.

Filebeat

https://imgur.com/a/kZWQQho

Metricbeat

https://imgur.com/a/H81GlPP

## Deployment

Files:
1. elk-playbook.yml: install and launch sebp/elk container on ELK server
2. filebeat-configuration.yml: the pre-defined configuration file of Filebeat which has updated Kibana and Elasticsearch server information
3. filebeat-playbook.yml: ansible playbook file to be run on Ansible container on Jumpbox to install Filebeat on both Web1 and Web2 servers
4. metricbeat-configuration.yml: the pre-defined configuration file of Metricbeat which has updated Kibana and Elasticsearch server information
5. metricbeat-playbook.yml: ansible playbook file to be run on Ansible container on Jumpbox to install Metricbeat on both Web1 and Web2 servers
