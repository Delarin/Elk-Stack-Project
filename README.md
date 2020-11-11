# Elk-Stack-Project
### This project creates infrastructure behind SIEM - Kibana, using Linux Scripts and Ansible Scripts to configure cloud servers with different docker containers.
### The final setup consisted of 2 webservers running DVWA containers, Jump-Box running an ansible provisional and an Elk server running ELK stack.

#### Cloud-Infrastructure:
![alt text](./Diagrams/Project.png)

#### Instructions

1. Creating a New vNet
Make sure that you are logged into your personal Azure account, where your cloud security unit VMs are located.


Create a new vNet located in the same resource group you have been using.


Make sure this vNet is located in a new region and not the same region as your other VM's.


Leave the rest of the settings at default.

Notice that the IP Addressing has automatically created a new network space of 10.1.0.0/16 which is exactly what you want.





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
