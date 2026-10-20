Lets us try to *dereference* a possible null expression.

- If you think it might get a null error, it will evaluate to null instead of throwing

```c#
string x = null;
Console.WriteLine(x?.Length); // will evaluate to null instead of crashing
```