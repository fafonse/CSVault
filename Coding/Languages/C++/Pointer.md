A variable that holds the memory address of another variables (*points to another variable*).

```cpp
int i = 3;
int *ptr = &i; // set pointer to address of i
```

## Usage
Pointers are very useful for multiple things, as they can just point around in memory where needed. They're notable different from [[References]], as they are mutable after initialization.
Pointers are specifically useful in accessing arrays, using pointer math to access indexes.

When using pointers to access the variable they point to you need to use the `*` to *dereference* it.

```cpp
cout << *ptr; // print 3
cout << ptr; // print memory address of i (if no crash)
```

You can also make pointers to pointers, as well as use pointers to point to `NULL`.

```cpp
*ptr = nullptr; // point to null
int **ptr2 = &ptr; // point to pointer that points to null 
```

### Pointer Math
Pointers are variables that store addresses in memory, so if you add/subtract from it, you shift the pointer around memory. This is how arrays are accessed a lot in C/C++.
```cpp
int main() {
    int arr[5] = {10, 20, 30, 40, 50};

    int* ptr = arr;   // points to first element

    // Access elements using pointer arithmetic
    for (int i = 0; i < 5; i++) {
        std::cout << *(ptr + i) << " ";
    }

    return 0;
}
```