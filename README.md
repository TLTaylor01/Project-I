
### CyberSecurity Project 1 ###
#Microsoft ELK Stack Design and Linux Server Deployment #

## Automated ELK Stack Deployment

The files in this repository were used to configure the network depicted below.

![Lab Layout Diagram for EKL Stack:](https://github.com/TLTaylor01/Project-I/blob/main/DIAGRAMS/Project_12_and_P1.jpg)

These files have been tested and used to generate a live ELK deployment on Azure. They can be used to either recreate the entire deployment pictured above. Alternatively, select portions of the Ansible file may be used to install only certain pieces of it, such as Filebeat.

[Ansible Playbook Located Here](Ansible/file-playbook.yml)

This document contains the following details:
- Description of the Topology
- Access Policies
- ELK Configuration
  - Beats in Use
  - Machines Being Monitored
- How to Use the Ansible Build


### Description of the Topology

The main purpose of this network is to expose a load-balanced and monitored instance of DVWA, the D*mn Vulnerable Web Application.

Load balancing ensures that the application will be highly available, in addition to restricting denial of services to the network.

A jump box advantage is that you have one location that can used to access multiple locations, which allows for added security for additional locations. _
Load Balancers offers protections against DDoS attacks due to its ability to spliet the work between two different servers.  This prevents losing system shut down as you're working off two servers. If one goes down the other one keeps runninig.
Integrating an ELK server allows users to easily monitor the vulnerable VMs for changes to the system status and system logs 
Filebeat is watching for specific logs and specific sets of files as set._

   Metricbeat is recording the statics of the files and/or logs as specified in the search filter.
The configuration details of each machine may be found below.
_Note: Use the [Markdown Table Generator](http://www.tablesgenerator.com/markdown_tables) to add/remove values from the table_.

| Name       | Function | IP Address | Operating System |
|------------|----------|------------|------------------|
| Jump Box   | Gateway  | 10.0.0.4   |    Linux         |
| Web VM SR I| DVWA     | 10.0.0.5   |    Linux         |
| Web VM SR I| DVWA     | 10.0.0.6   |    Linux         |
| ELK VM     | Ingest   | 10.0.0.7   |    Linux         |

### Access Policies

The machines on the internal network are not exposed to the public Internet. 

Only the Jumb box machine can accept connections from the Internet. Access to this machine is only allowed from the following IP addresses:
  

Machines within the network can only be accessed by The Jumpbox Provisioner.

The ELK machine is access from the container located in the ansible-playbook.

 The ELK machine digest information, the machine that sends the informaiton to the ELK machine is the Jump Boxs IP address?10:0.0.4

A summary of the access policies in place can be found in the table below.

| Name     | Publicly Accessible | Allowed IP Addresses |
|----------|---------------------|----------------------|
| Jump Box | Yes                 | 10.0.0.1 10.0.0.2    |
| Web I    | No                  | 10.0.0.5             |
| Web II   | No                  | 10.0.0.6             |

### Elk Configuration

Ansible was used to automate configuration of the ELK machine. No configuration was performed manually, which is advantageous because...
- The primary configuration is automation.  The system is able to duplicate the master file, then copying the files into the containers, automating task repetive tasks.  What is the main advantage of automating configuration with Ansible?_

The playbook implements the following tasks:
- The playbook first installs docker.io on all the webservers that have been underlined in the hosts file. Afterwards it will follow and install the rest of python3-pip and docker modules,
--The second task in the playbook is to run systemctl commands to insure that the memory is being is withing required limited.
The final task will be used as systemd command to ensures that the service has been propery installed and configured and running without error.

The following screenshot displays the result of running `docker ps` after successfully configuring the ELK instance.

![Diagrams](docker-project I.png)

### Target Machines & Beats
This ELK server is configured to monitor the following machines:
Web I IP 10.0.0.5
Web II Ip 10.0.0.6


We have installed the following Beats on these machines:
Metricbeat
Filebeat

These Beats allow us to collect the following information from each machine:
The beats allow us to collect collect data and system log information that's readable in Kibana logs.
### Using the Playbook

In order to use the playbook, you will need to have an Ansible control node already configured. Assuming you have such a control node provisioned: 
Copy the ansible file to the designated container.

Update the host file to include all webservers that you are Answer the following questions to fill in the blanks:
Which file is the playbook? Where do you copy it?

The playbook to set up elk is elk.yml and you copy this file into the /etc/ansible/directory.
__Which URL do you navigate to in order to check that the ELK server is running?__
In order to check if your elk server is up and running, you need to connect to the public IP address of the elk machine in a browser with the open port. Thus, your url should read something similar to this http://13.77.219.27:5601/app/kibana#/home.
requesting as well as uncommenting [webservers] and adding underneath your webservers ip addresses you will be adding a [elk] and the elks IP address. Next to all IP addresses you need to include ansible_python_interpreter=/usr/bin/python3.
Run the playbook, and navigate to Kibana<also the public ip address of the elk server:port address that you opened((5601))> to check that the installation worked as expected.

SSH into the control node and follow the steps below:
 Copy the  file to the designated contain.



Playbook_ansiblefile-playbook.yml 

Where do you copy it?
The playbook is set up in elk.yml and you copy the file into /etc/ansible/directory
The playbook is set to the elk stack in elk.yml and you would copthin file into the /etc/ansible/directory
_
 _Which file do you update to make Ansible run the playbook on a specific machine?

 How do I specify which machine to install the ELK server on versus which to install Filebeat on?

- _Which URL do you navigate to in order to check that the ELK server is running?_
You would verify that the ELK server is running,requires connecting to the Public IP address of the elk machine in a browser with the open Port info. The required URL for reference is 13.77.291.27:5601/app/kibana#home.


##Step by Step from Downloading Docker to Setting up a Playbook##

In order to run this set of dockers you will want to run the commands as follows. Note: This can only work if you already have set up a Azure VMs.
udo apt install docker.io
systemctl status docker (run this command to ensure that your docker.io was installed and running)
After installation, if your process is not running please run sudo systemctl status docker to start your process.
sudo docker pull cyberxsecurity/ansible (this will pull the container((you must know the container/image name exactly)) and download the container for you to access)
sudo docker run -ti cyberxsecurity/ansible:latest bash (please only run this once, if you run it more than once you will have one or more container)
sudo docker container list -a (this will show all available containers that you have after running ((run -ti)) this will also give you the name of the container for you to start)
sudo docker start (for instance mine is quirky_herschel). This will start your container and make it available to attach too.
sudo docker attach
sudo docker run -it cyberxsecurity/ansible /bin/bash (This command will set up a host and config file within your container allowing you to set up the files how you want).
Once you have done that you will want to locate the files.
cd /etc/ansible once you have moved into the directory /etc/ and moved into ansible you will want to run a ls to confirm your files are there.
Now that you have done all previous steps, you will be able to adjust the playbook files here. This will allow you to overwrite your playbooks, update your config files into include new webservers, or even new elk servers.
The first file we should look at is the hosts file. In here you will want to remove the # next to [webservers] and underneath a couple of lines that are already added there you will want to add the IP addresses that you want for your webservers for example mine being 10.0.0.6. Once you have added that you will want to hit tab and add the following line next to it. ansible_python_interpreter=/usr/bin/python3 this will allow for your python-pip3 that you installed in your playbooks to work with out an issue.
After we are done with the our changes to the hosts file we are going to save and exit and go into our configure file for ansible.
Once we are in the ansbile.cfg file, we are going to page down to the remote_user section of this file and change the remote_user= sysadmin to the username that you used to set up your VM. This will also be commented. You will want to uncomment the line after changing the username to your username.
Now that we have set up both of our hosts and configure files we are now going to create a play book.
Start your container (if it already is not started) and make sure on your command like is comming directly from your root. For example, check your screen to see if you see something like root@5e4b8f36e048:~#.
When you are in here you are more than welcome to create a playboook, for this exercise we are creating a DVWA (Damn Vulnerable Website App) so this playbook will be for that.
Our first step will be to write the command nano pentest.yml this will create the playbook.
The top of your playbook should read something like this:

This is declaring what you want the playbook to do. So we are Configuring a Web Virtual Machine using Docker.
Our host for this is going to be webservers hence why we uncommented and added the IP addresses.
Last but not least, we have become true. Allowing for this entire playbook to come true.

This segment is saying we want docker.io to install, so go ahead and force it to go through if we do not have it, update the cache to yes, name of the process we want and the state of the process.
In the next segment we are installing pip3 which is pulling from a index of python libary that is unable to be carried with python when we install python.

The next step should look like this...

The next step in the playbook is going to start the webserver and open the desired ports you want. This is also where you want to include the most important piece in all of the ansible-playbook in my opinion. That would be the restart_policy: always. If you do not include this, you will have to always restart the playbook in order for the webserver to start up instead of starting up when you start up your machine.

The final step in a playbook is making sure that the service is up and running. The first line in this is the name of the service we are running. The second line is the command we are running. The third line is the name of service we are running. Lastly, the fourth line is what we want to do with the service, do we want it enabled or disbaled.

Now that we have completed that we are going to run this command ansible-playbook pentest.yml.
You should get this read:

If you would like to test that the webserver is up an running you can ssh into your PRIVATE Ip address of your webserver using ssh @.
Now you have successfully set up a webserver, playbook, configure file, and a host file.

