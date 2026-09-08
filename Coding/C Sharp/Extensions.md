Methods you can add to already created classes without making a whole new derived class. A simple way of using them is like as a object "macro".

> [[Syntactic Sugar]], but useful for readability for SE

## Creation

- Create a static class to hold extension methods
```c#
static class StackExtensions
{
	// "this" keyword is required
	// refers to the caller of method, just needs to be typed
	public static RETURN_TYPE foo(this TYPE x, ...)
	{
	}
	
	public static bool isOnTop<int>(this Stack<int> s, T val)
	{
		return s.Count > 0 && s.Peek().Equals(x);
	}
}

```