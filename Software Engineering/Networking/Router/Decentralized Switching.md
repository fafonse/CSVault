 Using header field values, the [[Router Architecture#Input Port|input port]] finds the output port using a forwarding table in input port memory.
 
- **Goal**: complete input port processing at *line speed*
- *input port queueing*: if datagrams arrive faster than the switch fabric can handle.

There are also two types of forwarding used:
- *destination-based forwarding*: forward based only on destination IP address (traditional method)
- *generalized forwarding*: forward based on any set of header field values
	- You can direct packets based off their content type ([[User Datagram Protocol|UDP]], [[Transmission Control Protocol|TCP]])