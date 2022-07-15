# Project1
## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![image](https://github.com/powelga/Project1/blob/main/Project1%20Diagram.drawio.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook file may be used to install only certain pieces of it, such as Filebeat.

(https://github.com/powelga/Project1/blob/main/install-elk.yml)

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
Load balancers are meant to serve as an access point for multiple machines, it is in place to provide high availability to the machines by managing traffic load.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the log files and system resources.
- Filebeat watch system logs and forwards any changes to the Elasticsearch server. 
- Metricbeat gathers metrics and system resources usage for Elasticsearch. 
The configuration details of each machine may be found below.

| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.0.0.4   | Linux            |
| VM1      | DVWA     | 10.0.0.5   | Linux            |
| VM2      | DVWA     | 10.0.0.6   | Linux            |
| ELKSserve| ELK stack| 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the jumpbox machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
192.168.1.164

Machines within the network can only be accessed by jumpbox
Jump-Box-Provisioner - 10.0.0.4 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 192.168.1.164        |
|   VM1    | No                  | 10.0.0.4 10.0.0.6    |
|   VM2    | No                  | 10.0.0.4 10.0.0.5    |
| Elkserver| No                  | 10.0.0.4             |
### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because Ansible allows automation of server deployment and configuration. 

The playbook implements the following tasks:
- Install Docker on server
- Install Python3-pip installation code 
- Launch ELK container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.
![image](https://user-images.githubusercontent.com/98720098/179145041-23359e49-205a-4470-8976-bdb18177dbd0.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
10.0.0.5
10.0.0.6

We have installed the following Beats on these machines:
FileBeat
MetricBeat

These Beats allow us to collect the following information from each machine:
MetricBeat collects system usage information and memory, allowing you to monitor system resources. FileBeat collects system events like failed login attempts and user locations.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install_elk.yml file to /etc/ansible/roles/install_elk.yml
- Update the hosts file to include ELK hosts machine and IP address. 
- Run the playbook, and navigate to http://20.70.199.248:5601/app/kibana to check that the installation worked as expected.
