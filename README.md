# Elk-Stack-Project
### This project creates infrastructure behind SIEM - Kibana, using Linux Scripts and Ansible Scripts to configure cloud servers with different docker containers.
### The final setup consisted of 2 webservers running DVWA containers, Jump-Box running an ansible provisional and an Elk server running ELK stack.

#### Cloud-Infrastructure:
![alt text](./Diagrams/Project.png)

#### Instructions
Make sure that you are logged into your personal Azure account

#### Creating an Environment
In Azure, resource groups allow engineers to sort related resources into different groups, each of which can be easily located by name.

* Open your Azure portal and search for "resource group" to demonstrate.

* Select Resource groups in the search results and note the + Add button at the top.

* Select a region, In this project we are using West US 2

* Every resource that you create will have this button at the top.

Now that we have a resource group, we can add a virtual network.


####  Create a New vNet
Create a new vNet located in the same resource group.

Make sure this vNet is located in same region as the Resource Group.

Leave the rest of the settings at default.

Notice that the IP Addressing has automatically created a new network space of 10.0.0.0/16 as expected.

#### Setup Network Security Group (firewall) to protect the virtual network

* Open your Azure portal and search for "Network security group."


* Use the + Add button to add a network security group.


* Name the group something memorable.


* Once the group is created, click Go to resource.


* Click Inbound rules on the left side to set the rules that allow inflow of traffics.

#### Create a Virtual Machine, name it Jump-Box-Provisioner

* Navigate to your Azure portal, search for "Virtual" and select Virtual machines.


* Click + Add to create a new VM.

* Name this VM "Jump-Box-Provisioner."

* Under 'Availability Options' set it to No Infrastructure Redundancy

* set image to Ubuntu Server 18.04 LTS

* Size to Standard B1s

#### SSH SETUP
Accessing a server using a password is the weakest form of authorization: many programs can brute force an SSH password. Instead, so we will use an SSH key pair to access our new machine.

* Open a terminal and run ssh-keygen.


* You will be prompted to save the SSH key into the default directory ~/.ssh/id_rsa. DO NOT CHANGE THIS LOCATION. Press the Enter key.


* You will be prompted to enter a password for our new SSH key.

DO NOT ENTER A PASSWORD. Press the enter key twice to enter a blank password

* Run cat ~/.ssh/id_rsa.pub to show your id_rsa.pub key:

* Copy the SSH key string and paste it into the Administrator Account section on the Basics page for the VM in Azure.

For SSH public key source select Use existing public key from the drop down.
You will use the same SSH key for every machine you create today. Later we will change the key on a few machines.



The username can be any name, but it must be something the students will not forget. The SSH public key must be copied from the machine.

Create a Peer connection between your vNets. This will allow traffic to pass between your vNets and regions. This peer connection will make both a connection from your first vNet to your Second vNet And a reverse connection from your second vNet back to your first vNet. This will allow traffic to pass in both directions.


Navigate to 'Virtual Network' in the Azure Portal.


Select your new vNet to view it's details.


Under 'Settings' on the left side, select 'Peerings'.


Click the + Add button to create a new Peering.


Make sure your new Peering has the following settings:


A unique name of the connection from your new vNet to your old vNet.

Elk-to-Red would make sense



Choose your original RedTeam vNet in the dropdown labeled 'Virtual Network'. This is the network you are connecting to your new vNet and you should only have one option.


Name the resulting connection from your RedTeam Vnet to your Elk vNet.

Red-to-Elk would make sense





Leave all other settings at their defaults.
