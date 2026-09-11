# cdt-charlie-ansible
This repo contains Team Charlie's Ansible and deployment information for Cyber Defense Techniques.

Please create a subdirectory for your service in the ansible>linux/windows directory.

## Samba
Author: Braeden Villano (bcv4079@rit.edu)  
Code for deploying the Samba service is in the Samba role, located in ansible/linux/roles/samba directory  
To deploy, run the linux.yml playbook for the tag samba, using the command:  
```
ansible-playbook linux.yml -i <PATH TO INVENTORY FILE> -t samba
```
In the inventory file, hosts Samba should be deployed to must be under the samba group  
Variables for the role are defined in ansible/linux/roles/samba/vars/main.yml  
Grey team password can be changed, to do so see commented lines in ansible/linux/roles/samba/tasks/main.yml