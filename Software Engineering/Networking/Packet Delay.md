There are *4 major sources* of packet delay in networking.

- (Nodal) Processing
	- The time it takes for the control plane to think
	- Table lookups, encapsulation, reading, etc.
- Transmission
	- Time it takes to move the bits from input to output
	- $d_{\text{trans}} = L/R$
		- $L$ = packet length (bits)
		- $R$ = transmission rate (bps)
- Queueing
	- Time that the packets are waiting to be transmitted
- Propagation
	- Physical delay (on the wire)
	- $d_{\text{prop}} = d/s$
		- $d$ = length of the physical link
		- $s$ = propagation speed ($~2*10^8$ m/sec)