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
	- if ACK, give a 