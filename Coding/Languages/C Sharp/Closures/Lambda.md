A quick way of doing little code snippets in your code snippets.

```C#
Assert.Throws<Exception>(
{
	() => blah blah
}
);
```

> [!Warning] Nested Lambda
> If you have a lambda function in a for/loop/other thing, and you're using constantly changing variables, you have to do something different.
> Because of [[Closure|closure]], you can't just use changing variables, but instead have to create new ones so that each lambda has a different copy.
> ```C#
> for (int j = 0; j< 5; j++)
> {
> 	int index = j; // this is the stupid part
> 	onclick.Connect(() => MyClick(index));
> }
> ```

