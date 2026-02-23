---
aliases:
  - TCP
---
An overall secured, highly dressed up protocol. HTTP uses TCP for all of it's safety features, but if you're looking to make your own thing, use [[UDP]].

- *reliable transport* between sending and recieving process
- flow control: sender wont overwhelm receiver
- congestion control: throttle sender when network overloaded
- connection-oriented: setup required between client and server process
- does not provide: timing, minimum throughput guarantee, security

> Often involves *more commitment* than UDP