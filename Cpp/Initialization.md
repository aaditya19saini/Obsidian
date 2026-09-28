# Initialization

Initialization means giving an object its first value. Initialize variables before using them so their values are predictable.

```cpp
int score{10};  // initialize with 10
int count{};    // value-initialize; for int this is 0
```

The braces are called list initialization. They reject many narrowing conversions, such as placing `4.9` into an `int`:

```cpp
int whole{4.9}; // compile-time error: would lose the fraction
```

Other forms you may see:

```cpp
int a = 5; // copy initialization
int b(6);  // direct initialization
int c{7};  // direct-list initialization
int d{};   // value initialization; zero for an int
```

For local variables, `int a;` does not give `a` a useful initial value. Reading it before assigning a value is a bug. Global and `static` variables have different initialization rules, but prefer initializing variables where they are declared.

A declaration like `int x();` declares a function named `x`; it does not create an integer. Use `int x{};` for a zero-initialized integer.

**Rule of thumb:** initialize variables when declaring them, and prefer braces when they fit the code.
