A programming feature that allows developers to define custom behaviors for standard operators (like +, -, \*, etc.) when they are used with user-defined types.

> Usually you can have some operator overloads refer to previous ones (!= and \==)

```cpp
bool operator==(const PPM& rhs) const;
// this == that
bool operator>(const PPM& rhs) const;
// this > that

// Returns true if "this" fulfills the condition compared to the other class. This being the object on the lefthand side of the operator.
// Remember to use the const keyword when you're not modifying the object being called.
```