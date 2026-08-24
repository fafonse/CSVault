---
aliases:
  - SDN
  - Software-defined Network
  - OpenFlow
---
Simple packet-handling rules. Any of several actions (including drop/block, forward to a given interface, or duplicate-and-forward) can be made based on the contents of one or more packet header fields.


- match: pattern values in packet header fields
- actions: for matched packet: drop, forward, modify packet or send matched packet to controller
- priority: disambiguate overlapping patterns
- counters: # bytes and # packets

%% Begin Landmark %%
- [[Flow Table Abstraction]]
- [[Match-Action]]

%% End Landmark %%