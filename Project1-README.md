## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Project 1 Diagram](https://github.com/dfagan91/cat-lady/blob/main/Project%201%20Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the _____ file may be used to install only certain pieces of it, such as Filebeat.

  - https://github.com/dfagan91/cat-lady/blob/main/Install-ELK.yml.txt 

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting traffic to the network.
- Load balancers protect the network from potential DDoS attacks. 
- The Jump Box isolates within the private network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system logs.
- Filebeat monitors for suspicious file changes

The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.1   | Linux            |
| Elk Stack| Target   | 10.1.0.5   | Linux            |
| Web 1    |Web Server| 10.0.0.10  | Linux            |
| Web 2    |Web Server| 10.0.0.11  | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- 70.175.101.168

Machines within the network can only be accessed by the Ansible Container on the Jump Box.
- the Jump Box machine - IP: 10.0.0.12

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.10 10.0.0.11  |
|          |                     |                      |
|          |                     |                      |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- It takes far less time, with less room for error
- Ansible allows for configuration of the network easily, with the use of YAML files - no programming language knowledge is needed to draft.

The playbook implements the following tasks:
- Install Docker
- Increases the memory on the target machine
- Downloads and launches ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![docker ps output](https://github.com/dfagan91/cat-lady/blob/main/docker%20ps%20output.PNG)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _TODO: List the IP addresses of the machines you are monitoring_

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
- syslog data - Syslog events by hostname, syslog log events, syslog hostnames and processes

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible.
- Update the hosts file to include the elkserver details:  [elkservers] 10.1.0.5 ansible_python_interpreter=/usr/bin/python3
- Run the playbook, and navigate to http://52.188.21.255:5601/app/kibana to check that the installation worked as expected.
