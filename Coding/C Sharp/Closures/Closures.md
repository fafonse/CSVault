Code snippets that require shit outside of their scope, the compiler then includes entire outside scope along with it.

%% Begin Waypoint %%
- [[Actions]]
- [[Delegate]]
- [[Func]]
- [[Lambda]]

%% End Waypoint %%


## Example

```C#
foreach (obj x in objectList)
{
	someFunction(() => x + 2); // closure here
}
```
- In this example the closure is made, but the lambda will just continually add 2 to the `x`

```C#
{
	obj a = x;
	someFunction(() => a + 2);
}
```
- Here we declare a variable in the local scope and use that instead, which ensures that we have a new value in our lambda every loop