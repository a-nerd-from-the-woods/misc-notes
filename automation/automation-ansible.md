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
