32-bit identifier associated with each host or router [[Interface|interface]].

[[IPV4]] uses [[CIDR]] for the address format.

Two pieces:
- [[Subnet]]
	- Devices in the same subnet have common high order bits
- *Host*
	- Remaining lower order bits

## Assignment
Used to be assigned by hand, but now we have a plug and play system now.
It's called [[Dynamic Host Configuration Protocol]], or *DHCP*.