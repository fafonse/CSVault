## String Parsing
You can use either `.TryParse()` or `.toString`.
- `.TryParse()`/`.Parse()` can convert a double to a string, or a string to a double
- `.toString()` gives an object a string vibe
```c#
double d1 = 100;
double d2 = 100.000;
double d3 = 1e2;

string s1 = double.TryParse(d1); // always get 100 for d*
string s2 = "100.00";
string s3 = "1e2";

double d1 = double.Parse(s1); // 100
double d2 = double.Parse(s2); // 100
double d3 = double.Parse(s3); // 100
```

## [[String Literal|String Literals]]
Use the `@` sign to designate a string literal.

```c#
string user_drive = @"C:\Users";
```