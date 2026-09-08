Different ways of storing code in memory (RAM)

### Stack
A stack, similar to an array. A continuous block of data. Because there's no [[Dictionaries|key-pairs]], the lookup for memory is very fast.
Memory management is a bit annoying though, since you have to *pop* the "top" of the memory before you can discard the bottom.

```
main() -> print() -> int a -> int b

dealloc:
int b -> int a -> print() -> main()
```

- Automatic storage (scope-based)
- Very fast allocation/deallocation
- LIFO (last in first out) structure
- Size fixed at a compile/runtime limit
- Lifetime = scope ({} / function)


| Stores       | local variables, function parameters, return addresses |
| ------------ | ------------------------------------------------------ |
| **Risks**    | No manual free, stack overflow                         |
| **Examples** | ``int x``, ``std::string s``                           |
## Heap
A dynamic, large storage solution. Much more flexible than a stack, but a lot slower (memory must be searched).

- Dynamic Storage
- Slower than a stack
- Large, flexible size
- Dynamic lifetime
- Manual management

| Stores        | Dynamically allocated objects<br>                             |
| ------------- | ------------------------------------------------------------- |
| **Risks**     | Leaks, dangling pointers, fragmentation<br>                   |
| **Preferred** | ``std::unique_ptr``, ``std::shared_ptr``, ``std::vector``<br> |

```c++
auto p = new Foo; // (avoid raw new)
``` 
