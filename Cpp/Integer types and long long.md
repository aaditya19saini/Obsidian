# Integer types and `long long`

C++ integer types store whole numbers. Different types have different ranges, so choose one that can hold the values your program needs.

| Type | Typical range |
| --- | --- |
| `int` | −2,147,483,648 to 2,147,483,647 |
| `long long` | −9,223,372,036,854,775,808 to 9,223,372,036,854,775,807 |

These are typical ranges on modern systems. The C++ standard guarantees that `long long` can hold at least this much, while exact widths can vary by implementation.

Use `long long` when an `int` may be too small:

```cpp
long long secretNumber = 7;
long long guess{};

std::cin >> guess;
```

If the number entered is outside the range of `long long`, input with `std::cin` fails. Check the stream so the program can respond instead of continuing as if the input succeeded:

```cpp
if (!(std::cin >> guess)) {
    std::cout << "That input is not a valid number in range.\n";
    return 1;
}
```

`long long` only stores whole numbers and still has a maximum value. Use a floating-point type such as `double` for fractional values, or a different approach for integers larger than its range.
