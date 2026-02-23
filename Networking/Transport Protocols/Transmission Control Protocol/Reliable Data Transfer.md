- Reliable service *abstraction*
- Reliable service *implementation*
	- TCP helps interface between the transport layer and the *unreliable* network layer
	- Complexity depends on the characteristics of unreliable channel

> Servers are oblivious to each other, "two generals" sort of.


## RDT interfaces

Build up interfaces for the servers and clients to manage the RDT protocol.

```
        SERVER                          CLIENT
  ┌──────────────────────┐     ┌─────────────────────────┐
  │                      │     │                         │
  │rdt_send()=>udt_send()│  == │rdt_rcv()=>deliver_data()│
  │                      │     │                         │
  └──────────────────────┘     └─────────────────────────┘
```

- Use finite state machines (FSM) to specify sender, receiver.
	- Each state transitions to new states when given input