Kind of like importing a module in python.

```c#
using OtherNamespace; // imagine it has class Ball

namespace FirstOneLOL
{
	// If we didn't apply "using", we'd have to phrase it like this:
	// personalBall = new OtherNamespace.Ball;
	personalBall = new Ball;
}
```