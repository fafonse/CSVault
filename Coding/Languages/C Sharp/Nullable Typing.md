Every type in C# has a null and non-null type.
By default, variables are non-nullable; use `?` to make it nullable.
*This is only for compile-time warnings*.

```C#
// nullable
string? s;
int? i;
double? d;

// non-nullable / default
string s;
int i;
double d;
```

> While this can be seen as annoying, it also helps us write less *error-prone code*.