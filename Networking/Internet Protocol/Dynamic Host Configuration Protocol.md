---
aliases:
  - DHCP
---
Allows the host to *dynamically* obtain an IP address from the network server when it "joins" a network.

The **DHCP** is used to automatically assign:

- IP addresses
- subnet masks
- default gateways
- DNS servers
to devices when they join a network.


- Allows renewal of addresses
- Support for mobile users

## Overview
Typically, DHCP server is co-located in the router, serving all the [[Subnet|subnets]] the router is attached to.

1. Broadcast
	- Host asks if there is a server available for DHCP
		- Runs over UDP, client uses port 68
		- DHCP sends and receives on port 67