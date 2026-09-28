# Integer types and `long long`

C++ integer types store whole numbers. Pick a type that can represent all values the program needs.

| Type | Common range on modern systems |
| --- | --- |
| `int` | about −2.1 billion to +2.1 billion |
| `long long` | at least about −9.2 quintillion to +9.2 quintillion |

Exact ranges depend on the implementation; these are common values. Use `<limits>` and `std::numeric_limits<T>` when code needs to ask for the actual limits.

```cpp
long long secretNumber{7};
long long guess{};
std::cin >> guess;
```

A `long long` still has a maximum and minimum, and it stores whole numbers only. If input is too large to fit, extraction with `std::cin` fails; check the stream before relying on the value. For decimals, use a floating-point type such as `double`. See [[Variables and types]] and [[Input and output]].
