There's a couple different ways of typecasting in C++, but the most common by far is the `static_cast<>()` method.

```cpp
int i = 32;

// format like static_cast<new_type>(var);
unsigned char char_i = static_cast<unsigned char>(i);
```

## Reinterpret Cast
Reinterpret cast is used primarily for pointer casting, where C++ doesn't change the actual data stored, just tells the compiler to view it *differently*.

```cpp
char* c = 'c'; // -> x037
unsigned char* p = reinterpret_cast<unsigned char*>(c);
// still points to x037

unsigned char* n = static_cast<unsigned char*>(c);
// errors out, unsafe conversion (cannot convert types)
```