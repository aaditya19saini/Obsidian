# Conditions and loops

Conditions let a program choose what to do. Loops repeat work.

## `if` and `else`

```cpp
if (temperature > 30) {
    std::cout << "Hot\n";
} else if (temperature >= 20) {
    std::cout << "Warm\n";
} else {
    std::cout << "Cool\n";
}
```

The condition inside parentheses must be true or false. Braces make it clear which statements belong to each branch.

Use `==` for equality, not `=` (which assigns). Combine conditions with `&&` (both true), `||` (either true), and `!` (not).

## `while`: repeat while a condition is true

```cpp
int guess{};
const int secret{7};

while (guess != secret) {
    std::cout << "Guess: ";
    std::cin >> guess;
}
```

Make sure something inside the loop can change its condition. Otherwise it may never stop. Always handle failed input too; see [[Input and output]].

## `for`: repeat a known number of times

```cpp
for (int i{}; i < 5; ++i) {
    std::cout << i << '\n';
}
```

The three parts are initialization (`int i{}`), continue condition (`i < 5`), and update (`++i`). This prints 0 through 4.

## Range-based `for`: visit each element

```cpp
for (int value : numbers) {
    std::cout << value << '\n';
}
```

To change elements in place, use a reference: `for (int& value : numbers)`. See [[Strings and collections]].

## `break` and `continue`

`break` exits the nearest loop. `continue` skips to the next iteration. Use them when they make the loop easier to follow; avoid hiding complicated control flow inside them.
