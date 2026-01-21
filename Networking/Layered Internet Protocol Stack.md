Made up of 5 [[Architectural Layering|layers]].

1. *Application*: supporting network applications
	- HTTP, IMAP, SMTP, DNS
	- Sends *messages* between applications
2. *Transport*: process-process data transfer
	- TCP, UDP
	- [[Encapsulation|Encapsulates]] *messages* with a transport-layer header to create a *segment*
		- Implements many things, usually information to help with transportation
3. *Network*: routing of datagrams from source to destination
	- [[Internet Protocol|IP]], routing protocols
	- Encapsulates a *segment* to create a *datagram*
4. *Link*: data transfer between neighboring network elements
	- Ethernet, 802.11 (WiFi), PPP
	- Encapsulates a *datagram* to create a *frame*
5. *Physical*: bits "on the wire"

> Data will typically flow down a stack, then back up. This adds on headers continually and peels them off one by one as the data moves back up layers.