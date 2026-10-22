The entire context, including the enclosing scope used to run a method. You can think of it as a function pre-bundled with it's local variables.

The details of the closure are hidden from the invoker, supporting the separation of concerns.

> In C#, closures are commonly implemented with [[Delegate|delegates]]

## Code Example
I don't know if python supports closures like this... but this would work in JavaScript.

```python
def outer():
	a = 1
	def inner():
		print(a)
	return inner
	
myFunction = outer()
myFunction() # prints "1"
```