Similar to class attributes, but like with *built in getter and setter methods*.
C# [[Syntactic Sugar|syntactic sugar]] for class attributes. 

```C#
public string Major {
	get
	{
		// invoked when reading Major
	}
	set
	{
		// Invoked when assigning to Major
	}
}
```

- If you don't include a `set` method, the property becomes read-only

> [!example]
> You still need to have a property to store the value
> ```c#
> private string p_major;
> 
> public string Major {
> 	get {
> 		return p_major;
> 	}
> 	set {
> 		p_major = value;
> 	}
> }
> ```