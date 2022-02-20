# Cyber-Security-Project-1
Microsoft Azure Elk Stack Design &amp; Deployment

The files in this repository were used to configure the network depicted
below.

![image](https://user-images.githubusercontent.com/99157857/154829697-4c7e2bf9-6a16-4651-9d17-14c3407534a7.png)











These files have been tested and used to generate a live ELK deployment
on Azure. They can be used to either recreate the entire deployment
pictured above. Alternatively, select portions of the playbook file
may be used to install only certain pieces of it, such as FileBeat.















This document contains the following details: - Description of the
Topologu - Access Policies - ELK Configuration - Beats in Use - Machines
Being Monitored - How to Use the Ansible Build

### Description of the Topology

The main purpose of this network is to expose a load-balanced and
monitored instance of DVWA, the D\*mn Vulnerable Web Application.


Load balancing ensures that the application will be highly accessible ,
in addition to restricting traffic to the network. - 







*TODO: What aspect of security do load balancers protect? load balancers protect against DDos attacks. 





What is the advantage of a jump box?* the advantage of the JumpBox file is that it's a single point of entry that can be monitored and protected. 


 


Integrating an ELK server allows users to easily monitor the vulnerable
VMs for changes to the  LOGS  and system TRAFFIC.





*TODO: What does Filebeat watch for?* - FileBeat monitors changes to the log files. 


*TODO: What does Metricbeat record?* MetricBeat analyzes metrics and statistics of the file data. 



The configuration details of each machine may be found below. *Note: Use
the [Markdown Table
Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove
values from the table*.

| NAME    |   FUNCTION |  IP ADDRESS |  OS |   

 JUMP BOX     GATEWAY     10.0.0.4     LINUX  

 WEB VM 1     SERVER      10.0.0.9     LINUX 

 WEB VM 2     SERVER      10.0.0.10    LINUX 

 ELK SERVER   SERVER      10.2.0.4     LINUX 



### Access Policies

The machines on the internal network are not exposed to the public
Internet.

Only the JUMP BOX machine can accept connections from the Internet.
Access to this machine is only allowed from the following IP addresses: 172.117.57.160 (LOCAL MACHINE)


- *TODO: Add whitelisted IP addresses* 40.112.187.28 (LOAD BALANCER)

Machines within the network can only be accessed by PRIVATE IP ADDRESSES


*TODO:Which machine did you allow to access your ELK VM? What was its IP
address?* The JumpBox has access to the Elk Server. Public IP = 20.211.8.125 / Private IP 10.2.0.4


A summary of the access policies in place can be found in the table
below.


 | NAME    |  PUBLICLY ACCESSIBLE    |    ALLOWED IP ADDRESSES  | 
    
  JUMP BOX        YES                   172.117.57.160 (LOCAL MACHINE)  

  WEB VM 1         NO                   10.0.0.4

  WEB VM 2         NO                   10.0.0.4

  ELK SERVER       NO                   10.0.0.4 & 172.117.57.160 


               
 
                      
                                   

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No
configuration was performed manually, which is advantageous because... it eliminates the possibility of human error, and conserves resources by auto-populating large numbers of files.   


*TODO: What is the main advantage of automating configuration with
Ansible?* The main benefit is the continuity of data 

The playbook implements the following tasks: - *TODO: In 3-5 bullets,
explain the steps of the ELK installation play. E.g., install Docker;
download image; etc.* - ... - ...

	*INSTALL PYTHON3-PIP
  	*INSTALL DOCKER MODULE
	*INCREASE VIRTUAL MEMORY
	*USE MORE MEMORY
	*DOWNLOAD AND LAUNCH A DOCKER ELK CONTAINER








The following screenshot displays the result of running `docker ps`
after successfully configuring the ELK instance.


![TODO: Update the path with the name of your screenshot of docker ps
output:            images/docker_ps_output.png






### Target Machines & Beats

This ELK server is configured to monitor the following machines: -
*TODO: List the IP addresses of the machines you are monitoring* 10.0.0.9 (WebVM1), 10.0.0.10 (WebVM2), 10.0.0.4 (JumpBox)




We have installed the following Beats on these machines: - 

*TODO:Specify which Beats you successfully installed* FileBeat and MetricBeat were successfully installed.

These Beats allow us to collect the following information from each
machine: - 


*TODO: In 1-2 sentences, explain what kind of data each beat
collects, and provide 1 example of what you expect to see. E.g.,
`Winlogbeat` collects Windows logs, which we use to track user logon
events, etc.*    FileBeat collects changes to the log files, and MetricBeat collects statistics from the operating system.   



### Using the Playbook

In order to use the playbook, you will need to have an Ansible control
node already configured. Assuming you have such a control node
provisioned:

SSH into the control node and follow the steps below: - Copy the
elk_install.yml file to etc/ansible/roles/elk_install.yml . - Update the host file file to
include attributes - Run the playbook, and navigate to http:20.211.8.125:5601/app/kibana to check that
the installation worked as expected.

Which file is the playbook? 

filebeat-configuration.yml 


Where do you copy it? 

/etc/ansible/hosts/files


*Which file do you update
to make Ansible run the playbook on a specific machine? 

filebeat-playbook.yml 






How do I specify
which machine to install the ELK server on versus which to install
Filebeat on?* - the install-elk.yml file dictates installment directions. 



\_Which URL do you navigate to in order to check that
the ELK server is running? http://20.211.8.125 


*As a **Bonus**, provide the specific commands the user will need to run
to download the playbook, update the files, etc.*
