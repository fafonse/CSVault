Hosts break application-layer messages into [[Data Packet|packets]]. Breaking the data up into chunks that can be transmitted through a network.

*Packet transmission delay*: Size/Transmission rate
*Store and forward*: Entire packet must arrive at router before it can be transmitted on next link

## Queueing
Usually your router has a much higher input rate compared to a output rate (ethernet -> cable).
A solution is to just create a *packet queue*. This occurs when work arrives faster than it can be serviced.
- Packets will queue, waiting to be transmitted on the output link
- Packets can be *dropped* if memory (buffer) in router fills up

## Pros/Cons
Why do we use packet switching over [[Circuit Switching|circuit switching]]?
- Great for "bursty" data
	- Resource sharing
	- Simpler, no "call" setups
- *excessive congestion possible*: possible packet loss due to buffer overflow
	- protocols needed for reliable data transfer, congestion control

>[!question] How can we get "circuits" with packet switching?
> It's complicated. There's a lot of methods we can use to get *close* to circuit switching, but not quite all the way.