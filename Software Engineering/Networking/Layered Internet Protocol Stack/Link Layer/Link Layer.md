The layer that *links* hosts to the internet.

## Implementation
The link layer is in each-and-every host. It's typically implemented in a *network interface card* (NIC), or on a chip.

> Combination of hardware, software, and firmware


## Terminology
- hosts and routers: nodes
- communication channels that connect adjacent nodes along the communication path : links


## Services
- *Framing*, *link access*:
	- Encapsulate datagram into a *frame*, adding header, trailer
	- Channel access if shared medium
	- MAC addresses in frame headers identify source, destination
		- Different from [[Internet Protocol|IP]]!
- *Error Detection*
	- Receiver detects errors, signals retransmission, or drops frame
- *Error Correction*
- *Half-duplex* and *Full-duplex*
	- With half duplex, nodes at both ends of link can transmit, but not at same time.