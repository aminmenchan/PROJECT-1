# PROJECT-1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![PROJECT-1/Diagrams/Project 1 -Network Topology.docx]

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Pentest.ym file may be used to install only certain pieces of it, such as Filebeat.

  -PROJECT-1/Ansible/Project 1_Pentest.yml.docx

This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available and redundant, in addition to restricting traffic to the network.
-The aspect of security that load balancers protect is Availability. A jump box ensures that only those with access can view data in the virtual machines attached to it and do not have public exposure thereby increasing redundancy.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the server and system logs.
-Filebeats watch for changes in the file system
-Metricbeats records system information such as the CPU, RAM, etc. 

The configuration details of each machine may be found below.
| Name     | Function | IP Address     | Operating System |
|----------|----------|----------------|------------------|
| Jump Box | Gateway  | 137.117.110.42 | Linux            |
| Web-1    | DVWA     | 10.0.0.7       | Linux            |
| Web-2    | DVWA     | 10.0.0.8       | Linux            |
| Elk      | Monitor  | 40.77.103.82   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet.

Machines within the network can only be accessed by Jump Box.
-The Jump Box is the machine that is allowed to access ELK VM. Its IP address is 10.0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses       |
|----------|---------------------|----------------------------|
| Jump Box | Yes                 | 137.117.110.42 / 10.0.04   |
| Web-1    | No                  | 10.0.0.7 /10.0.0.4         |
| Web-2    | No                  | 10.0.0.8 / 10.0.0.4        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because
-the main advantage of automating configuration with Ansible is decerasing cognitive load

The playbook implements the following tasks:
-Install Docker
-Install Python
-download and launch DVWA
-Enable DVWA

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

PROJECT-1/Diagrams/ELK Container.docx

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
-Web-1: 10.0.0.7
Web-2: 10.0.0.8

We have installed the following Beats on these machines:
-Filebeat
-Metricbeat

These Beats allow us to collect the following information from each machine:
-Filebeats watch for changes in the file system such as logs, locations, and permissions to access files
-Metricbeats records system information such as the CPU, RAM, etc. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Pentest.yml file to Ansible directory.
- Update the Hosts file to include VMs and their private addresses
- Run the playbook, and navigate to VMs to check that the installation worked as expected.

-The Pentest.yml is the playbook and it is located at PROJECT-1/Ansible/Project 1_Pentest.yml.docx
-The Hosts file runs the playbook on a specific machine. The Hosts file installs the ELK server on versus which to install Filebeat on.
http://(ELK external IP):5601/app/kibana#/home is the URL to navigate to in order to check that the ELK server is running.

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
