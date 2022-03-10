# Project-13-Submission

### Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Project 1_ Network Security drawio](https://user-images.githubusercontent.com/93627049/157345218-66c875d7-8efe-4412-98b5-ef9b20eb0dad.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

- [Ansible Playbook](/Ansible/pentest.yml)
- [Filebeat Playbook](/Ansible/filebeat-playbook.yml)
- [Metricbeat Playbook](/Ansible/metricbeat-playbook.yml)
- [Elk Playbook](/Ansible/install-elk.yml)

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
- What aspect of security do load balancers protect?
  - Distributed Denial of Service (DDoS) attacks.
- What is the advantage of a jump box?
  - It's a security layer that minimizes attacks.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system monitoring.
- What does Filebeat watch for?
  - It monitors log files and collects log events.
- What does Metricbeat record?
  - It monitors servers and collects metrics from the system.

The configuration details of each machine may be found below.

| Name                 | Function  | IP Address | Operating System |
|----------------------|-----------|------------|------------------|
| ELK                  | ELK Stack | 10.1.0.4   | Ubuntu LTS 20.04 |
| Jump-Box-Provisioner | Gateway   | 10.0.0.4   | Ubuntu LTS 20.04 |
| Web-1                | Server    | 10.0.0.5   | Ubuntu LTS 20.04 |
| Web-2                | Server    | 10.0.0.6   | Ubuntu LTS 20.04 |
| Web-3                | Server    | 10.0.0.8   | Ubuntu LTS 20.04 |


### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner and ELK machines can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- My public IP and internal web servers.

Machines within the network can only be accessed by Jump-Box-Provisioner through SSH.
- Which machine did you allow to access your ELK VM?
  - My personal computer with Public IP whitelisted.
- What was its IP address?
  - 13.64.146.37

A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses         |
|----------------------|---------------------|------------------------------|
| ELK                  | Yes; 13.64.146.37   | vNet, 10.0.0.4, My Public IP |
| Jump-Box-Provisioner | Yes; 20.39.52.189   | vNet, My Public IP           |
| Web-1                | No                  | vNet, 10.0.0.5               |
| Web-2                | No                  | vNet, 10.0.0.6               |
| Web-3                | No                  | vNet, 10.0.0.8               |


### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?
  - A fast, easy to use open source IT configuration and automation tool that uses readable YAML templates.

The playbook implements the following tasks:
- Configures Web Virtual Machine with Docker
- Updates docker.io
- Installs Python-3-pip
- Installs Python Docker Module
- Downloads and launches a docker web container
- Enables Docker Service

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![sudo docker ps](https://user-images.githubusercontent.com/93627049/157364894-78bb76e5-ed66-4ecb-b6b4-3d5e5032bc00.PNG)


### Target Machines & Beats

This ELK server is configured to monitor the following machines:
- Web-1
- Web-2
- Web-3

We have installed the following Beats on these machines:
- Filebeats
- Metricbeats

These Beats allow us to collect the following information from each machine:

- In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc.
  - Filebeats: Forwards and centralizes logging data.
  - Metricbeats: Metric data from target servers.


### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Ansible file to `/etc/ansible/`.
- Update the 'ansible.cfg' file to include remote user name.
- Run the playbook, and navigate to 'http://ELK-Public-IP/app/kibana' to check that the installation worked as expected.

Answer the following questions to fill in the blanks:
- Which file is the playbook?
  - filebeat-playbook.yml
- Where do you copy it?
  - `/etc/ansible/`
- Which file do you update to make Ansible run the playbook on a specific machine?
  - `/etc/ansible/hosts/`
- How do I specify which machine to install the ELK server on versus which to install Filebeat on?
  - By using the ansible group. There is a webservers group and an elkserver.
- Which URL do you navigate to in order to check that the ELK server is running?
  - http://13.64.146.37:5602/app/kibana

 _As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
 
 | Command                             | Purpose                        |
 |-------------------------------------|--------------------------------|
 | systemctl status docker             | Docker application status      |
 | sudo docker container ps -a         | Active/Enactive container list |
 | sudo docker start <container name>  | Starts docker application      |
 | sudo docker attach <container name> | Ansible container access       |

