Device interfaces that can physically reach each other without passing through an intervening router.

Devices in the same subnet share the same subnet part of their [[IPV4 Address]].

> i.e LANs/ WLANs


## Reserving IP Addresses

> How do *networks* get the subnet part of an IP address?

They're reserved a portion of the provider ISP's address space.
### Hierarchical Addressing
Hierarchical addressing allows efficient advertisement of routing information.
- Makes it really easy for people to find the place to send their data to

### Keeping Addressing when Moving
If a subnet moves over to a different ISP, then how do they keep their range of IP addresses?

1. The old ISP still asks for the range it always has.
2. The new ISP now advertises for a longer prefix, like the exact one it needs
3. All new packets are directed to the more specific address advertisement

This works because [[Forwarding Table|forwarding tables]] in routers use [[Longest Prefix Matching]] to determine which address to send their data to. So the more specific prefix match will be chosen over anything else.