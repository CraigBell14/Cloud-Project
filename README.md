## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

https://drive.google.com/file/d/1x1YGiKS4CYcxrLF1BGWNASGD0Tl9eQTH/view?usp=sharing

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the .yml file may be used to install only certain pieces of it, such as Filebeat.

my-playbook.yml
elk-playbook.yml
filebeat-playbook.yml
metricbeat-playbook.yml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly secure, in addition to restricting traffic to the network.
- Load balancers protect from DDoS attacks. The advantage of the jump-box is that it is the only access point to the other virtual machines on the network reducing the attack surface of the network. 

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the logs and system files.
- Filebeat watches log data. 
- Metricbeat records system files.

The configuration details of each machine may be found below.

| Name       | Function | IP Address | Operating System |
|------------|----------|------------|------------------|
| Jump-box   | Gateway  | 10.0.0.4   | Linux            |
| Web-1      | Docker   | 10.0.0.5   | Linux            |
| Web-2      | Docker   | 10.0.0.6   | Linux            |
| Web-3      | Docker   | 10.0.0.7   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- Public IP

Machines within the network can only be accessed by the Jump-box.

A summary of the access policies in place can be found in the table below.

| Name       | Publicly Accessible | Allowed IP Addresses |
|------------|---------------------|----------------------|
| Jump Box   | No                  | Public IP            |
| Elk-VM     | No                  | 10.0.0.4             |
| Web-1      | No                  | 10.0.0.4             |
| Web-2      | No                  | 10.0.0.4             |
| Web-3      | No                  | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate the configuration of the ELK machine. No configuration was performed manually, which is advantageous because it makes it much easier to replicate on another machine. 

The playbook implements the following tasks:
- Increase Memory 
- Install docker.io
- Install python3
- Install docker
- Download and run elk container

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1 IP: 10.0.0.5
- Web-2 IP: 10.0.0.6
- Web-3 IP: 10.0.0.7

We have installed the following Beats on these machines:
- Filebeat 
- Metricbeat

These Beats allow us to collect the following information from each machine:
- Filebeat collects log files and you should expect to see login attempts. Metricbeat collects system logs and you should expect to see any changes to system files. 

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Filebeat configuration file to /etc/filebeat/filebeat.yml.
- Update the Filebeat configuration file to include the elk-VM IP address.
- Run the playbook, and navigate to the Elk server GUI to check that the installation worked as expected.

- The user edits the .config file to specify which machines one would like to run the playbook on.   
- Navigate to http://20.55.205.125:5601/app/kibana in order to check that the ELK server is running.
