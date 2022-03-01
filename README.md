# Elk-Project

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

Elk-Project/Project-1.drawio.png at main · jskeens5/Elk-Project (github.com)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.


This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting access to the network.
- This protects against DDoS attacks by preventing servers from being overloaded. The jump box has the advantages of allowing access to the user from a single node, and this means it can be more easily secured and monitored.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
- Filebeat will monitor log files, collect those events and forward them to the ELK stack.
- Metricbeat periodically records metric data, including operating system metrics like CPU or memory data related to the services running on the servers.

The configuration details of each machine may be found below.

| Name    | Function | IP Address | OS    |
|---------|----------|------------|-------|
| Jumpbox | Gateway  | 10.0.0.4   | Linux |
| VM1     | DVWA     | 10.0.0.5   | Linux |
| VM2     | DVWA     | 10.0.0.9   | Linux |
| ELK     | Server   | 10.1.0.4   | Linux |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Ansible jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My personal address via SSH.

Machines within the network can only be accessed by SSH.
- The Elk server is accessible from the Ansible jumpbox machine.

A summary of the access policies in place can be found in the table below.

| Name    | Publicly Accessible | Allowed IP Addresses |
|---------|---------------------|----------------------|
| Jumpbox | No                  | My Personal IP       |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because the automation is less vulnerable to human error and more efficient, scalable and repeatable.

The playbook implements the following tasks:
- Install Docker.
- Install Python.
- Install virtual memory.
- Download and launch ELK container.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.



### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.0.0.5 and 10.0.0.9

We have installed the following Beats on these machines:
- Filebeat
- Metricbeat These Beats allow us to collect the following information from each machine:
- Filebeat collects webserver logs and any changes to system files while Metricbeat collects metrics of the operating system including CPU and memory.

These Beats allow us to collect the following information from each machine:
- One example of a Metricbeat log would include any SSH attempts to login while Filebeat would include Apache server logs.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the YAML playbook file to Ansible control node.
- Update the YAML file to include IP addresses, ports, and services.
- Run the playbook and navigate to container to check that the installation worked as expected.

- Filebeat will run on the DVWAs, both Virtual machine 1 and virtual machine 2, as will Metricbeat. -To check that the ELK server is running, navigate to the URL 70.37.162.50:5601, as it runs on that port.
