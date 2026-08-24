TCP naturally tries to avoid congestion, leading to avoidance of "unfair" bandwidth usage.

When TCP has two competing connections, you can imagine them having an upper bound on their transmission rate. One connection using more bandwidth leads to the other having decreased bandwidth, and both need to share the network.
As each connection tries to achieve maximum bandwidth, they go over that 