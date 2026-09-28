# Variables and types

A variable is a named place for a value. Its type determines what kind of value it can hold and which operations make sense for it.

```cpp
int count{3};
double temperature{21.5};
bool isReady{true};
char grade{'A'};
std::string name{"Aaditya"};
```

Include `<string>` to use `std::string`.

## Common types

| Type | Stores | Example |
| --- | --- | --- |
| `int` | Whole numbers | `int score{42};` |
| `long long` | Larger whole numbers | `long long population{8000000000LL};` |
| `double` | Decimal numbers | `double price{3.50};` |
| `bool` | `true` or `false` | `bool finished{false};` |
| `char` | One character | `char initial{'A'};` |
| `std::string` | Text | `std::string city{"Delhi"};` |

The exact range of integer types depends on the implementation; `int` is commonly 32 bits and `long long` at least 64 bits. Choose a type based on the values and precision the program needs. Integer types cannot store fractions. For money, consider storing the smallest unit as an integer (for example, paise) to avoid floating-point rounding surprises.

## Names and constants

Names can use letters, digits, and underscores, but cannot start with a digit. C++ is case-sensitive: `score` and `Score` are different names.

Use `const` when a value should not change after initialization:

```cpp
const int maxAttempts{3};
```

Use `auto` when the type is obvious from the starting value:

```cpp
auto count{3}; // int
```

Prefer clear names and explicit types while learning.

## A type has limits

A type cannot represent every possible value. If an input number does not fit in an `int`, reading it into an `int` can fail. Use a wider type when appropriate, and still check input. See [[Integer types and long long]] and [[Input and output]].
