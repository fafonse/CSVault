How does TCP know which process to send it's info to?
How does TCP get encoded with it's delivery data?

> [!example] Highway Analogy
> As a TCP packet you have to get onto the Highway, then you have to merge onto your exit.
> - **Multiplexing** = entrance ramp
> - **Demultiplexing** = exit ramp


## Multiplexing
The packet knows where to go because each [[Layered Internet Protocol Stack|layer]] adds on to the header.

1. The application sets the format of the packet body
2. At the transport layer the packet is given a port number for the application on the other computer, as well as a "from" address.
3. At the network layer the packet is given an [[Internet Protocol|IP]] address for the destination computer
4. The link layer adds on it's own "delivery" data to the header

## Demultiplexing
The packet is delivered, and now the recipient needs to route it to the correct process.

1.  host receives IP datagrams
	- each datagram has a source and destination IP
	- each datagram carries one transport-layer segment
	- each segment has a source + destination port number
2.  Host uses IP addresses and port number to route the packet to the right application