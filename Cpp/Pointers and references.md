# Pointers and references

A reference is another name for an existing object. A pointer stores the address of an object. Both let code work with an object without copying it, but they have different rules.

## References

```cpp
int score{10};
int& scoreAlias{score};
scoreAlias = 12; // score is now 12
```

A reference must be initialized when declared and cannot later be made to refer to a different object. Use references for function parameters when a function should use or modify the caller's object. Add `const` when it should only read the object:

```cpp
void printScore(const int& score);
void addPoint(int& score);
```

## Pointers

```cpp
int score{10};
int* scoreAddress{&score}; // & obtains the address
*scoreAddress = 12;        // * accesses the pointed-to object
```

A pointer may point to no object. Use `nullptr` to represent that explicitly and check before dereferencing:

```cpp
int* value{nullptr};
if (value != nullptr) {
    std::cout << *value;
}
```

Dereferencing a null, invalid, or expired pointer is a bug. A pointer does not automatically own or manage the object it points to.

## Lifetime matters

Do not return a pointer or reference to a local variable: that variable stops existing when its function returns. Prefer returning a value; C++ can return strings, vectors, and other objects safely and efficiently.

For dynamic ownership, prefer standard library types such as `std::vector` and smart pointers (`std::unique_ptr`) over manually paired `new` and `delete`. Learn pointers gradually; many programs can use values and references without raw pointers.

The symbol `&` also means bitwise AND in a different context. See [[Operators]] and [[Functions and scope]].
