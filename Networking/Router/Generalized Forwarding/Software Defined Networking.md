---
aliases:
  - SDN
---
A type of networking where you split the data flow from the controller, since you can then use software to control your shit.

Split into two pieces:
- **Data Plane**
	- [[Match-Action]] in tables
	- Perform actions
	- Don't think very hard
- **Control Plane**
	- Defines the *match-action* rules that are in place
		- Can do so in real time