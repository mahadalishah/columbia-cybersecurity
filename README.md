# Project 1 - Setup systems on Azure cloud

This project is to setup infrastructure on Azure cloud

## Diagram
https://imgur.com/a/d5AZkP1

## Deployment

Files:
1. elk-playbook.yml: install and launch sebp/elk container on ELK server
2. filebeat-configuration.yml: the pre-defined configuration file of Filebeat which has updated Kibana and Elasticsearch server information
3. filebeat-playbook.yml: ansible playbook file to be run on Ansible container on Jumpbox to install Filebeat on both Web1 and Web2 servers
4. metricbeat-configuration.yml: the pre-defined configuration file of Metricbeat which has updated Kibana and Elasticsearch server information
5. metricbeat-playbook.yml: ansible playbook file to be run on Ansible container on Jumpbox to install Metricbeat on both Web1 and Web2 servers

## Virtual machines

| Machine     | Public IP address | Private IP address | Security group       | Allowed incoming IPs : Ports     |
| ----------- | ----------------- | ------------------ | -------------------- | -------------------------------- |
| Jumpbox     | 104.214.27.180    | 192.168.1.10       | Learning_nsg         | Any 22                           |
| Web1        |                   | 192.168.1.11       | Learning_nsg_private | 192.168.1.10 : 22; LoadBalancer : 80 |
| Web2        |                   | 192.168.1.12       | Learning_nsg_private | 192.168.1.10 : 22; LoadBalancer : 80 |
| ELK         | 13.66.32.109      | 192.168.1.50       | elk_nsg              | 192.168.1.10 : 22; IP_of_workstation, 192.168.1.11, 192.168.1.12 : 5044, 5601, 9200, 9300 |

## Result

### Filebeat

https://imgur.com/a/kZWQQho

### Metricbeat

https://imgur.com/a/H81GlPP

