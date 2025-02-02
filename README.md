# AL-project-1
Ash Leavitt's first Cybersecurity Bootcamp project.

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Diagrams/redteamvnetdiagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible/ files may be used to install only certain pieces of it, such as Filebeat.

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly availabile, in addition to restricting Denial of Service attacks to the network.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the metrics and system logs.

The configuration details of each machine may be found below:

| Name     | Function  | IP Address | Operating System |
|----------|-----------|------------|------------------|
| Jump Box | Gateway   | 10.0.0.4   | Linux            |
| Web 1    | DVWA host | 10.0.0.5   | Linux            |
| Web 2    | DVWA host | 10.0.0.6   | Linux            |
| Valerian | ELK Stack | 10.1.0.4   | Linux            |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:

Machines within the network can only be accessed by 71.62.219.95.

A summary of the access policies in place can be found in the table below:

| Name     | Publically Accessible | Allowed IP Addresses   |
|----------|-----------------------|------------------------|
| Jump Box | No                    | 71.62.219.95           |
| Web 1    | No                    | 71.62.219.95, 10.0.0.4 |
| Web 2    | No                    | 71.62.219.95, 10.0.0.4 |
| Valerian | No                    | 71.62.219.95, 10.0.0.4 |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because using playbooks allows for new machines to be built efficiently and with consistency. 

The playbook implements the following tasks:
- Install Docker
- Download the ELK Stack container image
- Start the ELK Stack with its associated ports
- Configure Systemd to launch Docker and the ELK Stack container on boot

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

(Images/docker_ps_output.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
  -10.0.0.4
  -10.0.0.5
  -10.0.0.6

We have installed the following Beats on these machines:
  -Filebeat
  
These Beats allow us to collect the following information from each machine:
  -Filebeat collects log data from the machines, which allows us to analyze, for instance, changes to system files.


### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the install-elk.yml file to the /etc/ansible directory.
- Update the hosts file to include the target machine's IP under the "elk" group.
- Run the playbook, and navigate to localhost:5601/app/kibana to check that the installation worked as expected.
