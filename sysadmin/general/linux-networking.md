# Linux Networking

## Ubuntu Server (No GUI) Network Configuration

File location: `/etc/netplan/00-installer-config.yaml`

File Contents For Static IP (example file in Github directory):

```
network:
	version: 2
	ethernets:
		ADAPTER_NAME:
			addresses:
			- DESIRED_IP/IP_SUBNET
			gateway4: DEFAULT_GATEWAY
			nameservers:
				search: [DOMAIN_TO_SEARCH]
				addresses: [PRIM_DNS_SERVER, ALT_DNS_SERVER]
```

* Test the config file using: `sudo netplan try`

* Hit `Enter` when prompted

