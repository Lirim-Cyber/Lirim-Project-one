## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![TODO: Update the path with the name of your diagram](Images/diagram_filename.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the playbook (.yml) file may be used to install only certain pieces of it, such as Filebeat.

  ELK PLAYBOOK
  
  root@37b2349d9d8b:/etc/ansible/roles
  
  <img width="418" alt="Screen Shot 2021-06-05 at 7 28 35 PM" src="https://user-images.githubusercontent.com/85391715/120907989-4b5e4380-c634-11eb-98d6-8b4f6233cb9f.png">

  
  FILEBEAT PLAYBOOK
  
  root@37b2349d9d8b:/etc/ansible/roles/filebeat-playbook.yml
  
  <img width="657" alt="Screen Shot 2021-06-05 at 7 27 05 PM" src="https://user-images.githubusercontent.com/85391715/120907964-19e57800-c634-11eb-961b-5c3ad10fe1e7.png">

  
  
This document contains the following details:
- Description of the Topologu
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly responsive, in addition to restricting traffic to the network.

The Jump Box minimises the attack surface by ensuring remote connections to the cloud network come through a single VM which is a huge advantage. Remote connections to the Jump Box can be monitored easily to identify unusual remote connections.

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the data and system logs.
 Filebeat monitors specified log files or locations while metricbeat collects and ships metrics and statistics to specified outputs.

The configuration details of each machine may be found below.


| Name     | Function | IP Address | Operating System |
|----------|----------|------------|------------------|
| Jump Box | Gateway  | 10.1.0.4   | Linux            |
| web-1    | server   | 10.1.0.8   | Linux            |
| web-2    | server   | 10.1.0.9   | Linux            |
| Elk-vm   | server   | 10.2.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump Box Machine machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses: 76.125.211.15


Machines within the network can only be accessed by SSH.
I allowed my jump-box machine to access my elk server and its IP was 76.125.211.15 

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | No                  | 76.125.211.15        | 
|  web-1   | No                  | 76.125.211.15        |
|  web-2   | No                  | 76.125.211.15        |
|  Elk-VM  | No                  | 76.125.211.15        |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
you can consistantly and rapidly configure mutliple machines.


The playbook implements the following tasks:

- step 1: installs docker
- step 2: install python3-pip
- step 3: sets vm map count to 262144
- step 4: installs python docker module
- step 5: downloads elk 761 docker
- step 6: enables docker service


The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Screen Shot 2021-05-22 at 11 28 31 AM](https://user-images.githubusercontent.com/85391715/120907115-0b479280-c62d-11eb-9057-7308fc51e461.png)


### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- 10.1.0.8
- 10.1.0.9

We have installed the following Beats on these machines:
- Filebeat

These Beats allow us to collect the following information from each machine:
- filebeat collects audit logs, deprecation logs, gc logs, server logs, and slow logs from VM's running the filebeat agent.

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the Playbook file to Ansible container.
- Update the ansiblehosts file to include...

<img width="386" alt="Screen Shot 2021-06-05 at 6 51 21 PM" src="https://user-images.githubusercontent.com/85391715/120907405-07b50b00-c62f-11eb-8d2b-70d574e33c9b.png">



- Run the playbook, and navigate to Kibana to check that the installation worked as expected.

Copy the YAML file into the /etc/ansible/ directory Update the /etc/ansible/hosts' file to include 'hosts' group, private IP address, the following line 'ansible_python_interpreter=/usr/bin/python3' specify the machines by creating two different hosts sections and applying the host selection in the playbook. navigate to the browser and type :5601/app/kibana
