# Cybersecurity_Repository-

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

(Images/AC_azure_cloud_setup.pdf)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the [AC_azure_cloud_setup] file may be used to install only certain pieces of it, such as Filebeat.

  /Ansible/elk_stack_config_yaml

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly availabe, and additonally restricting access to the network.

Load Balancers protect the availability of a network by optimizing the efficacy of data movement.


Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the network traffic.
Filebeat can be used to monitor logs.

The configuration details of each machine may be found below.

| Name     | Function  | IP Address | Operating System |   
|----------|-----------|------------|------------------|
| Jump Box | Gateway   | 10.0.0.4   | Linux            |
| ELK VM   | Gateway   | 10.1.0.5   | Linux            |
| Web 1    | Container | 10.0.0.5   | Linux            |
| Web 2    | Container | 10.0.0.6   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box machine can accept connections from the Internet. Access to this Jump Box is only allowed from the IP address belonging to the machine used to configure the virtual network

Machines, within the network, can only be accessed by SSH.


A summary of the access policies in place can be found in the table below.

| Name                | Publicly Accessible | Allowed IP Address                     |
|---------------------|---------------------|----------------------------------------|
| Jump Box            | Yes                 | [Machine IP used to configure network] |
| ELK Virtual Machine | No                  | 104.214.63.63                          |
| Web 1               | No                  | 104.214.63.63                          |
| Web 2               | No                  | 104.214.63.63                          |





### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually. This process is advantageous because it is more streamline, efficient, and mitigates the risk of human error.

The playbook implements the following tasks:

.Installs Docker.io
.Installs Python3-pip
.Increases Virtual Memory of the Virtual Machine
.Downloads/Launches elk container 

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

[docker ps output] /Images/docker_ps_output.PNG

### Target Machines & Beats
This ELK server is configured to monitor the following machine IP Addresses:

10.0.0.5 [Web 1]
10.0.0.6 [Web 2]

We have installed the following Beats on these machines:

.Filebeat

Filebeat allow us to collect the log data from the machines.




### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the filebeat-playbook.yml file to your docker container.
- Update the filebeat-config.yml file to include the host IP of the machine you want to use [line 1106 : filebeat-config.yml]
- Update the filebeat-config.yml file to include the Host IP/Kibana port [line 1806 : filebeat-config.yml] 
- Run the playbook, and navigate to http://[ELK-Server-IP]:5601/app/kibana to check that the installation worked as expected.
