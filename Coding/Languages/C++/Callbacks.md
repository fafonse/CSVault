When you pass a function as a parameter to another function, you get a *callback*. This is especially useful in event driven programming, where you can pass actions according to event easily.

```cpp
void addOne(int &x) {
	x++;
}

void addTwo(int &x) {
	x += 2;
}

// how you add one as a parameter
void adder(int &x, void (*function_pointer) (int)) {
	function_pointer(x);
}

int main() {
	int test = 0;
	adder(test, addOne); // test = 1
	adder(test, addTwo); // test = 2
}
```

You can also declare a new function pointer type for easier readability.

```cpp
 #include blahblahblah
 
 typedef void (*function_type) (char); //  takes 1 int, returns void
 
void adder(int &x, function_type fp) {
	fp(x); // now its easy to add wherever!
}
```