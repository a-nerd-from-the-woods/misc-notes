
# Redundant DHCP Servers

In the same directory as this file, there are 2 DHCP configuration files, `master-dhcp.conf` and `slave-dhcp.conf`.They were created inorder to have 2 DHCP servers on the same network without them both giving IP address to clients.This was done by having one be a master node and the other a slave node, the master will reply to clients while able to, and the slave node will only reply to clients when the master cannot. In addition, the will give clients IP Address in different ranges, this was done in order to prevent the nodes from serving the same IP Address to multiple clients by mistake.


