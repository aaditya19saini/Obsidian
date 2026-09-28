# Errors and debugging

Programs can fail in different ways. Identify which kind of problem you have before changing code.

## Three common kinds of errors

1. **Compile-time error:** the compiler cannot translate the program, often because of a typo, missing semicolon, or type mismatch. Read the first useful error and its file/line; later messages may be consequences.
2. **Runtime error:** the program builds but fails while running, such as trying to open a missing file or accessing an invalid index.
3. **Logic error:** the program runs but gives the wrong result. Trace the values and conditions to find where behavior diverges from what you expected.

## A simple debugging routine

1. Reproduce the problem with the smallest input that shows it.
2. Read the exact error or incorrect output.
3. Check the relevant variables and assumptions. Print values with `std::cout` or use a debugger breakpoint.
4. Change one thing at a time, then build and try the same input again.
5. Keep a small example that confirms the fix.

## Handle expected failures

Check operations that can fail, then respond clearly. For console input:

```cpp
int number{};
if (!(std::cin >> number)) {
    std::cerr << "Expected a whole number.\n";
    return 1;
}
```

`std::cerr` is the standard error output stream. A nonzero return from `main` conventionally signals failure.

For files, check that opening succeeded before reading or writing:

```cpp
#include <fstream>
#include <iostream>

std::ifstream input{"data.txt"};
if (!input) {
    std::cerr << "Could not open data.txt\n";
    return 1;
}
```

## Exceptions

Exceptions report failures that interrupt normal control flow. Catch an exception only when the current code can recover or add useful context. Do not use `try`/`catch` to hide ordinary input validation or logic errors. Learn exceptions after you are comfortable with return values and checking operations.

Also prevent errors: initialize variables, check indexes, keep functions small, and compile with warnings enabled. See [[Build and run]].
