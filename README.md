# Project-13-Submission

### Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Project 1_ Network Security drawio](https://user-images.githubusercontent.com/93627049/157155867-2d547155-ddd4-4166-b28b-e1b378c1eada.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the YAML file may be used to install only certain pieces of it, such as Filebeat.

- [Ansible Playbook](/Ansible/pentest)
- [Filebeat Playbook](/Ansible/filebeat-playbook)
- [Metricbeat Playbook](/Ansible/metricbeat-playbook)
- [Elk Playbook](/Ansible/install-elk)

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
  - ???
- What is the advantage of a jump box?
  - ???

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the files and system monitoring.
- What does Filebeat watch for?
  - ???
- What does Metricbeat record?
  - ???

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
- ???

Machines within the network can only be accessed by Jump-Box-Provisioner through SSH.
- Which machine did you allow to access your ELK VM?
  - ???
- What was its IP address?


A summary of the access policies in place can be found in the table below.

| Name                 | Publicly Accessible | Allowed IP Addresses         |
|----------------------|---------------------|------------------------------|
| ELK                  | Yes;???             | vNet, 10.0.0.4, My Public IP |
| Jump-Box-Provisioner | Yes;???             | vNet, My Public IP           |
| Web-1                | No                  | vNet, 10.0.0.5               |
| Web-2                | No                  | vNet, 10.0.0.6               |
| Web-3                | No                  | vNet, 10.0.0.8               |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- What is the main advantage of automating configuration with Ansible?
  - ???

The playbook implements the following tasks:
- ???
- ???
- ???

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![TODO: Update the path with the name of your screenshot of docker ps output](Images/docker_ps_output.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- Web-1
- Web-2
- Web-3

We have installed the following Beats on these machines:
- Filebeats
- Metricbeats

These Beats allow us to collect the following information from each machine:
- _TODO: In 1-2 sentences, explain what kind of data each beat collects, and provide 1 example of what you expect to see. E.g., `Winlogbeat` collects Windows logs, which we use to track user logon events, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Ansible file to '/etc/ansible/'.
- Update the 'ansible.cfg' file to include remote user name.
- Run the playbook, and navigate to 'http://ELK-Public-IP/app/kibana' to check that the installation worked as expected.

Answer the following questions to fill in the blanks:
- Which file is the playbook?
  - ???
- Where do you copy it?
  - ???
- Which file do you update to make Ansible run the playbook on a specific machine?
  - ???
- How do I specify which machine to install the ELK server on versus which to install Filebeat on?
  - ???
- Which URL do you navigate to in order to check that the ELK server is running?
  - ???

 _As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
