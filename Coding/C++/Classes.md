
## Initializer List
When constructing an object, sometimes you need your parameters to be defined with parameters right as they're created. This is important for any bigger objects (vectors, strings, etc.) as well as any non-mutable variables.

This is the common approach taken with higher-level languages:
```cpp
Class::Class(int parameter) {
    this->parameter = parameter;
}
```
However, this is slower as `parameter` goes through a default constructor and then is reassigned to its value.

Instead you use this format for initializing on load:
```cpp
Class::Class(int value) 
	: parameter(value) {}

// multiple values

Class::Class(int a, int b)
    : x(a), y(b), z(a + b)
{}
```

An initializer list is needed for
- `const` variables
	- default construction is `null` and cannot be reassigned
- References
	- must be assigned on declaration
- No default constructor
- Base classes (inheritance)