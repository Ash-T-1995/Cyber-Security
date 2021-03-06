### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system metrics.

The configuration details of each machine may be found below.


| Name       | Function               | IP Address | Operating System |
|------------|------------------------|------------|------------------|
| Jump Box   | Gateway                | 10.1.0.150 | Linux            |
| Web 1      | DVWA                   | 10.1.0.160 | Linux            |
| Web 2      | DVWA                   | 10.1.0.170 | Linux            |
| Elk Server | Monitor Logs / Metrics | 10.0.0.4   | Linux            |

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Diagrams/Netowrk Diagram.PNG

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the install-elk.yml file may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 49.180.128.70

Machines within the network can only be accessed by the Jumpbox on 10.1.0.150.

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses      |
|------------|---------------------|---------------------------|
| Jump Box   | No                  | 10.1.0.0.160 & 10.1.0.170 |
| Web 1      | No                  | 10.1.0.150                |
| Web 2      | No                  | 10.1.0.150                |
| Elk Server | No                  | 10.1.0.150                |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because it saves time for IT admins since they do not need to do redundant tedious and repetitive work.

The playbook implements the following tasks:
- install Docker
- download image
- Install Python 3-pip
- Increase virtual memory
- Enable service docker on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

Images/Elk docker ps.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machines:

Web 1
10.1.0.160

Web 2
10.1.0.170



We have installed the following Beats on these machines:
-Filebeat
-Metricbeat

These Beats allow us to collect the following information from each machine:
Filebeat - Generates and organizes log files to send to Logstash and Elasticsearch.
Metricbeat - Collects metrics from the operating system and from services running on the server.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to /etc/ansible/
- Update the /etc/ansible/hosts file to include a group called [elk] and specify the IP address of the Elk Server VM
- Run the playbook, and navigate to http://<ELK.VM.External.IP>:5601/app/kibana to check that the installation worked as expected.

The specific commands the user will need to run to download the playbook, update the files, etc.

Run the yml file
ansible-playbook install-elk.yml

Update ansible
sudo apt-get update
