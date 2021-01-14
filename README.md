## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://github.com/sheaC7/Homework12/blob/main/Diagrams/Homework12%20screenshot.png

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - https://github.com/sheaC7/Homework12/blob/main/Ansible/playbook.yaml

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- Load Balancers protect against DDOS attacks and eliminate single points of failure. The advantage of a jump box is that it is a singular point of access for the specific network it is tied to. This allows for secure access to the network, while maintaining all access secruity in one place.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system traffic.
- Filebeat watches for log files and events
- Metricbeat monitors and records your systems and services running on the server. 

The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.1.0.4   | Linux            |
| Web-1    | Server   | 10.1.0.5   | Linux            |
| Web-2    | Server   | 10.1.0.6   | Linux            |
| Elk-VM   | Server   | 10.2.0.4   | Linux            |                  

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the JumpBox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 10.1.0.4
- 98.38.19.141
- Virtual Network 
- Azure LoadBalancer

Machines within the network can only be accessed by passing through the JumpBox.
- The machine that can access the elk VM is the JumpBox, with the IP of 10.1.0.4

A summary of the access policies in place can be found in the table below.

| Name                             | Publicly Accessible | Allowed IP Addresses |
|----------------------------------|---------------------|----------------------|
| SSH-From-JumpBox                 | No                  | 10.1.0.4             |
| SSH                              | Yes                 | 98.38.19.141         |
| Port_80                          | Yes                 | 98.38.19.141         |
| Allow-VNet-Inbound               | No                  | 10.1.0.0/16          |
| Allow-Azure-LoadBalancer-Inbound | Yes                 | 13.65.179.66         |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- It saves a lot of time setting things up.

The playbook implements the following tasks:
- Install Docker.io
- Install Pip3
- Install Docker Python Module
- Expand Available memory
- Download and launch a docker elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

https://github.com/sheaC7/Homework12/blob/main/Assets/Docker%20PS%20output.png

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.1.0.5
- 10.1.0.6

We have installed the following Beats on these machines:
- Filebeat--10.2.0.4

These Beats allow us to collect the following information from each machine:
- Filebeat collects log events which allows them to be indexed by elasticsearch. For example filebeat would collect the var logs so we know what failed. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat config file to ansible container.
- Update the config file to include...the IP address of your Elk machine
- Run the playbook, and navigate to Filebeat installation page on the Elk server GUI to check that the installation worked as expected.

: Answer the following questions to fill in the blanks:_
- You copy the filebeat-playbook.yml to the ansilbe container
- Update the filebeat-config.yml The Web-1 VM needs to included the file with the Elk server IP address.
- http://10.2.0.4:5601/app/kibana.
