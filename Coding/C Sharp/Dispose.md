A method that `IDisposable` objects can use. Think like file writers/threads/shit.

```C#
try 
{
	// code that might fail
}
finally
{
	o.Dispose();
}
```


If you do the `using` keyword though, you can make a little more smaller setup.
```c#
using(IDisposable obj = new ...)
{
	// code
}
```