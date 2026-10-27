Using a reference passed as a parameter as the output for your function.
C# has a special usage for this kind of output.

```C#
double a;
double x = double.TryParse("1e0", out a);
```