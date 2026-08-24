A mesh of interconnected routers, based on the fundamental idea of [[Packet Switching]].

The network forwards packets from one router to the next, daisy chaining until it reaches it's intended destination.

## Forwarding and Routing

A network core has two *key functions*: forwarding and routing.
**Forwarding**
- AKA "switching"
- Uses a forwarding table to know which packets go where
- A *local* action: move arriving packets from the router input link to the appropriate router output link
**Routing**
- *Global* action: Determine the paths taken by packets
- Routing algorithms

> [!EXAMPLE] A Car Trip Analogy
> If we were to put forward and routing in easier terms, we could compare them to a car trip.
> Routing is the deciding of which roads to take, finding which *route*/highways you need to go down.
> Forwarding is kind of like stopping at a city, coming from one "input" highway and going out a "output" highway.
