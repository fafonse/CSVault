## Network

The transport layer abstracts everything the network does to keep it simple.
The transport layer handles all the application and socket shit, while the network layer actually passes it along the wire.

> [!example] Houshold Analogy
> *12 kids in Ann's house sending letters to 12 kids in Bill's house*
> - hosts = houses
> - processes = kids
> - app messages = letters
> - *transport protocol* = Ann and Bill who demux to in-house siblings
> - Network-layer protocol = postal service