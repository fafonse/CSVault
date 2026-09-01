---
aliases:
  - regex
---
A way to search and filter strings using a "formula".
## Searching

String Literals
	- `abc` finds *abc*
	- The space character is not a token separator, but a character.

Or
- `gray|grey` matches "gray" and "grey"

Subexpressions
- `(CS|cs)2420 is (fun|hard)` matches 4 strings

Brackets
- Match a single character within
- Can do ranges
- `[abc]` matches *a*, *b*, or *c*.
- `[a-z]` matches all lower case letters.
- `[a-zA-Z0-9]` matches all letters and numbers *(just one though)*

Curly Brackets
- Match the preceeding \>=m, \<n
- A uID is formatted `u[0-9]{7,7}`
	- u1484948
	- The 0-9 occurs at least 7 times, and at most 7 times.

Plus sign
- Makes something that selects a single character select any character next to it thats part of the "class"
- `[a-z]+0` accepts *a0* and *abc0*
	- `[a-z]0` only accepts *a0*

Start and End line
- `^` starts
- `$` ends