## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below. 

![NetworkDiagram](Diagrams/Diagram.png)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the install-elk.yml file may be used to install only certain pieces of it, such as Filebeat.

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
- What aspect of security do load balancers protect? What is the advantage of a jump box?

 _Load balancers protect organizations from DDoS attacks._

 _The advantage of a jump box is allowing only one path to connect._

Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the event logs and system metrics.
- What does Filebeat watch for?

  _Filebeat monitors log files and log events._

- What does Metricbeat record?

  _Metricbeat records metrics and statistics it collects._

The configuration details of each machine may be found below.

| Name                 | Function      | IP Address | Operating System |
|----------------------|---------------|------------|------------------|
| Jump-Box-Provisioner | Gateway       | 10.0.0.4   | Linux            |
| Web-1                | Web Server    | 10.0.0.5   | Linux            |
| Web-2                | Web Server    | 10.0.0.6   | Linux            |
| ELK-VM               | ELK Dashboard | 10.1.0.4   | Linux            |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jump-Box-Provisioner machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
- _47.221.226.237_

Machines within the network can only be accessed by Jump-Box.
- Which machine did you allow to access your ELK VM?

  _The Jump-Box-Provisioner VM_

- What was its IP address?

  _10.0.0.4_

A summary of the access policies in place can be found in the table below.

| Name                 | Publically Accessible | Allowed IP Addresses |
|----------------------|-----------------------|----------------------|
| Jump-Box-Provisioner | Yes                   | 47.221.226.237       |
| Web-1                | No                    | 10.0.0.4             |
| Web-2                | No                    | 10.0.0.4             |
| ELK-VM               | No                    | 10.0.0.4             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- _Ansible allows setup of multiple identical machines to run simultameously with just one command._

The playbook implements the following tasks:
- _Installs docker.io_
- _Installs Python_
- _Installs Docker Module_
- _Increase virtual memory_
- _Download & launch a docker elk container
- _Enable server docker on boot_

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance. 

![Docker](Diamgrams/Images/docker_ps.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
- _10.0.0.4_
- _10.0.0.5_

We have installed the following Beats on these machines:
- _Filebeat_
- _Metricbeat_

These Beats allow us to collect the following information from each machine:
- _Filebeat monitors logs and locations and can handle audit logs, server logs, and depreciation logs._
- _Metricbeat monitors metrics and statistics and monitors services such as Apache, MySQL, Nginx, etc._

### Using the Playbook
In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 

SSH into the control node and follow the steps below:
- Copy the `Filebeat-config.yml` file to Web VM's using `etc/filebeat/filebeat-playbook.yml.`
- Update the `Filebeat-config.yml` file to include IP Address of the ELK Machine.
- Run the playbook, and navigate to the Filebeat installation page on the ELK Server GUI to check that the   installation worked as expected.

- Which file is the playbook? Where do you copy it?
  _`Filebeat-playbook.yml.` needs to be copied `/etc/ansible/roles/`_
  
- Which file do you update to make Ansible run the playbook on a specific machine? How do I specify which machine to install the ELK server on versus which to install Filebeat on?

  _Update the `hosts` option near the top of the `filebeat-playbook.yml` as either `web servers` or `elk`.

- Which URL do you navigate to in order to check that the ELK server is running?

  _Navigate to http://{ELK Public IP]:5601/app/kibana._

_As a **Bonus**, provide the specific commands the user will need to run to download the playbook, update the files, etc._
