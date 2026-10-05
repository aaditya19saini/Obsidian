# Operators

Operators work on values. For example, `+` adds numbers and `==` compares two values.

## Arithmetic

`+` add, `-` subtract, `*` multiply, `/` divide, `%` remainder for integers, `++` increment, `--` decrement.

```cpp
int a{7};
int b{2};
int quotient{a / b}; // 3: integer division discards the fraction
int remainder{a % b}; // 1
```

When both operands are integers, `/` performs integer division. Use a floating-point operand when a fractional result is needed.

## Compare and combine conditions

- `==`, `!=`: equal, not equal
- `<`, `>`, `<=`, `>=`: less/greater comparisons
- `&&`, `||`, `!`: logical AND, OR, NOT

Use `==` to compare values and `=` to assign a value.

## Assign and update

`=`, `+=`, `-=`, `*=`, `/=` assign values. For example, `score += 1;` adds one to `score`.

## Other operators to recognize

- `<<` and `>>` send/read values with streams such as `std::cout` and `std::cin`.
- `&` can mean address-of or bitwise AND depending on context; `*` can mean multiplication or pointer dereference.
- `.` accesses a member, such as `person.name`.
- `?:` is the conditional operator; learn `if` first.

Parentheses can make the intended order clear. Learn operators as you encounter them rather than memorizing a long catalog.


[[Assignment operators ]],[[Mathematical operators]] 