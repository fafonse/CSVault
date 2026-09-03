The opposite of [[Design Patterns|design patterns]]. If you see these, that means your code is kinda bad.

## Loops
Sometimes you use the wrong kind of loop for your code.
- Using a regular loop for a collection
	- Iterate instead
- Use a while loop like a for loop

> Don't let yourself be able to make mistakes!

## Hard Coding Values
Global/local hard coded values with no explanation.
- Just put it in a config
- Add comments

## Repeated Code
If you have 2-3 lines of repeated code just make another function.
- Makes it easier to modify shit
- Cleaner

## Pre-optimizing
First rule of optimizing: **DON'T!**

- Straight forward implementation first
- Only optimize if needed
- Don't sacrifice clean design for "speed"
	- The compiler does most for you

## Reinventing the Wheel
If it's already been optimized, why try to do it your own way?

## Silver Bullet
Not every tool works for every job.

> "Python is the best language for everything"