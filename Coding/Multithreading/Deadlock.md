When [[Thread|threads]] [[Mutex|lock]] each other up.

> Thread 1 holds something Thread 2 needs, Thread 2 holds something Thread 1 needs.

- Proving that you're deadlock-free is pretty hard.
- Try to avoid complex *nested locking*
	- A lock inside a lock is a *code smell*