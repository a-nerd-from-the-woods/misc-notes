# Automation With Ansible

## The Hosts/Inventory File

The `hosts.txt`/`inventory.txt` file is where you will store the IP addresses of the target machines to be manage. In addition you can also define roles and varibles within the hosts file.

An example of a host file with a role called `linux` would be defined as such:

```
[linux] 
0.0.0.0 # IP Address server 0
1.1.1.1 # IP Address server 1

[linux:vars]
ansible_user=deployer
ansible_password=your-password
```
## Playbooks

Playbooks are written tasks for Ansible to push to specified targets. Here is an example of a playbook that installs the `httpd` package, and makes sure that it is running. This example assumes that the target machines use the `yum` package manager.

```
- name: Playbook
    hosts: linux
    become: yes
    tasks:
      - name: ensure apache is at the latest version
        yum:
          name: httpd
          state: present
      - name: ensure apache is running
        service:
          name: httpd
          state: started
```
