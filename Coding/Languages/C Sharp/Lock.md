Implements [[Mutex|section locking for threads.]]

- The "owner" thread locks and unlocks as it uses the code section
- Other threads go to sleep until the lock is available

```c#
lock (a)
{
}
```

Couple things to note:
- Does not "lock" `a`
- `a` must be an object all threads have access to
	- Should be related to the data changing at hand