# Installing Ansible in Ubuntu 22.04
This document outlines the steps required to install Ansible on a Ubuntu 22.04 machine, and how to configure SSH keys for passwordless connectivity and add a node to the Ansible master.
1. Installation Steps
Update the package index:
```bash
apt-get update -y
```
2. Upgrade the installed packages to their latest versions:
```bash
apt-get upgrade -y
```
3. Check the version of Python 3 installed:
```bash
python3 -V
```
4. Install Python 3 pip package:
```bash
sudo apt install -y python3-pip
```
5. Check the version of Python 3 again:
```bash
python3 -V
```
6. Update the package index:
```bash
apt-get update -y
```
7. Install the required software properties common package:
```bash
apt-get install software-properties-common
```
8. Add the Ansible PPA repository:
```bash
apt-add-repository ppa:ansible/ansible
```
9. Update the package index:
```bash
apt-get update -y
```
10. Install Ansible:
```bash
apt-get install ansible -y
```
11. Check the installed version of Ansible:
```bash
ansible --version
```
## Configuring SSH Keys for Passwordless Connectivity
1. Open the Ansible configuration file:
```bash
vim /etc/ansible/ansible.cfg
```
2. Open the Ansible hosts file:
```bash
vim /etc/ansible/hosts
```
3. Generate an SSH key pair:
```bash
ssh-keygen -t rsa
```
4. Verify that the keys were generated and saved:
```bash
cd /root/.ssh
ls
```
5. Print the public key:
```bash
cat id_rsa.pub
```
6. Copy the public key to the remote node's authorized keys file to enable passwordless connectivity:
```bash
vim authorized_keys
```
## Adding a Node to the Ansible Master
1. Open the Ansible hosts file:
```bash
vim /etc/ansible/hosts
```
2. Add the following lines below the existing content:
```bash
[<name of server>]
<public ip of node>
```
3. Generate an SSH key pair:
```bash
ssh-keygen -t rsa
```
4. Verify that the keys were generated and saved:
```bash
cd /root/.ssh
ls
```
5. Open the Ansible hosts file:
```bash
vim /etc/ansible/hosts
```
6. Ping all nodes to check connectivity:
```bash
ansible -m ping all
```
## Conclusion
By following these steps, you should now have a working installation of Ansible in Ubuntu 22.04, with SSH keys configured for passwordless connectivity, and a node added to the Ansible master. You can now use Ansible to manage your infrastructure.