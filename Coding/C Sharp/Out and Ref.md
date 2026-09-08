Allows you to control parameters and sort of play with your memory a bit more.
> Keywords must be used when the method *is called* as well.
## ref
Designates a parameter as [[Pass By Reference]]. 
Use this when your function is going to use the value already stored in there.

```c#
void AddOne(ref int y)
{
	y++;
}

int y = 3;
AddOne(ref y); // y = 4
```

## out
Designates an output parameter. Must be initialized before the method is called.

```c#
void setXYZ(out int x, out int y, out int z)
{
	x = 10;
	y = 5;
	z = 2;
}

int y; // initialized
int x;
int z;
setFive(out x, out y, out z); // x = 10, y = 5, z = 2
```