---
aliases:
  - TCP
---
An overall secured, highly dressed up protocol. HTTP uses TCP for all of it's safety features, but if you're looking to make your own thing, use [[UDP]].

- *reliable transport* between sending and receiving process
- flow control: sender wont overwhelm receiver
- congestion control: throttle sender when network overloaded
- connection-oriented: [[Handshaking|handshake]] required between client and server process
- does not provide: timing, minimum throughput guarantee, security

> Often involves *more commitment* than UDP

> TCP does NOT have a protocol for handling out-of-order segments


## Overview

TCP utilizes several different techniques to achieve it's stability.

- *point-to-point*
	- One sender, one receiver
- Reliable, in-order *byte stream*
	- No "message boundaries"
	- Continuous
- Full duplex data
	- Bi-directional data flow in same connection
	- MSS: maximum segment size

### Segment Structure

Each segment can be up to 32 bits wide.

1. Source port \# and destination port \#
2. Sequence number
	- Counts "number" of first byte in segments data.
3. Acknowledgement number
4. Length + Reset + Fin + Set + flow control + ACK
5. checksum
6. TCP Options
7. Application data

### Timeout

Bit of a balancing act, as too slow will lead to unnecessary retransmissions and too long will lead to delayed reactions to segment loss.

However, we can base our TCP timeout using the [[Round Trip Time|RTT]]. But, RTT varies a lot! So we make sure to measure it with a timer and we smooth out the variability ourselves.

- `EstimatedRTT` = $(1 - \alpha) * \text(EstimatedRTT) + \alpha * \text(SampleRTT)$
	- Typical $\alpha$ is ~$1.25$
- `TimeoutInterval`

## Roles

### Sender

> Given some data over the network...

1. Create a segment with seq \#
2. Seq \# is byte-stream number of first data byte in segment
3. Start time if not running
	- Expires based on the `TimeOutInterval`