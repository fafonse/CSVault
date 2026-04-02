---
aliases:
  - TCAM
  - ternary content addressable memories
---
When looking for a forwarding table entry for a given the destination address, use the *longest* address prefix that matches the destination address.

- For a 32-bit IP address to match a prefix, all the zeroes to the left of the address must match those of the prefix.
	- Choose the one that's the longest match.

This is often performed using *ternary content addressable memories* (TCAMs).
- *content addressable*: present address to TCAM: retrieve address in one clock cycle, regardless of table size
	- Really really fast lookups
- Cisco Catalyst: ~1M routing table entries in TCAM