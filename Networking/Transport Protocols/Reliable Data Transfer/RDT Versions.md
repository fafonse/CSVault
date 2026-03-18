# RDT 1.0
- Underlying channel perfectly reliable
	- no bit errors
	- no loss of packets
- *serperate* FSMs for sender, receiver:
	- sender sends data into underlying channel
	- receiver reads data from underlying channel

## Sender
1. Make a packet
2. Send the packet

## Receiver
1. Enter a receiving state
2. Extract the packet data
3. Deliver the packet data

# RDT 2.0
- Underlying channel may flip bits in packet
	- checksum to detect bit errors
- How to recover from errors?
	- *Acknowledgements* (ACK): Receiver tells sender that packet is received OK
	- *Negative acknowledgements* (NAK): Receiver tells sender that packet had errors
		- Resend packet when given NAK

## Sender
1. Create packet
2. Send packet
3. Wait for acknowledgement
	- If NAK, resend the packet
	- if ACK, send the next packet

# RDT 2.2
Instead of using NAK for bad packets, we just use the ACK.
Here we use sequence numbers to validate the ACKs.

- If a packet was dropped, send an ACK for the *last packet recieved*
- If it was successful when send the ACK for the *current packet*

# RDT 3.0

*New assumption*: Underlying channel can also *lose* packets
- Checksum, sequence numbers, ACK, retransmission isn't enough
- Retransmit if no ACK was received in time (maybe it got super delayed)
	- Timeout timer

> Restart the time out whenever you send a packet out (ack or data, whatever)