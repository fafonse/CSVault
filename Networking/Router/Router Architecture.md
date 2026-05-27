The way the router moves data inside it's structure.

## I/O Ports
Key parts of the network layer here.

- Wireless
- Ethernet
- Wired options
- Fiber

> When going from *input* $\rightarrow$ *output* ports, the router incorporates a *high-speed switching fabric* that can correctly forward the data. This is managed by a *routing processor*.

### Input Port

The port has a *physical layer*, *link layer*, and lookup/forwarding/queuing functions.

- Physical layer
	- Bit-level reception; line termination
- Link layer
	- e.g, Ethernet recieving

**Decentralized Switching**
- Using header field values, this finds the output port using a forwarding table in input port memory
- *Goal: complete input port processing at line speed*
- *input port queueing*: if datagrams arrive faster than the switch fabric can handle.
## Routing Processor

The main controller for the components. Also the only component using software for I/O forwarding instead of hardware.