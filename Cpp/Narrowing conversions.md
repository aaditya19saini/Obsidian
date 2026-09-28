# Conversions and narrowing

A conversion changes a value from one type to another. Some conversions are safe for a particular value; others can lose information.

```cpp
double measurement{3.9};
int whole = measurement; // becomes 3: the fractional part is discarded
```

A conversion from a wider integer type to a narrower one may not preserve the value. Converting a negative signed number to an unsigned type produces a large nonnegative value; it does not preserve the negative meaning.

```cpp
int signedValue{-1};
unsigned int unsignedValue = signedValue; // large unsigned value
```

Do not rely on out-of-range signed integer conversions behaving as wraparound. Their behavior has varied across C++ versions and implementations. Avoid them or check the range first.

List initialization catches many narrowing conversions at compile time:

```cpp
int a{3.9}; // error: narrowing conversion
```

But braces do not replace range checks for values read from a user or calculated at runtime. Check that a value fits before converting it. See [[Variables and types]] and [[Input and output]].
