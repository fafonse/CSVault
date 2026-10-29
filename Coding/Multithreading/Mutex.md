Provides [[Thread|threads]] the ability to "lock" a section of code.

- Locks as it enters the lines, unlocks it as it leaves the section
- Locks intentionally *remove concurrency*, therefore reducing performance
	- Good algorithms have as few critical sections as possible