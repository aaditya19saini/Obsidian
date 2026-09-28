# Hello, world

A C++ source file usually ends in `.cpp`. This small program prints a message:

```cpp
#include <iostream>

int main() {
    std::cout << "Hello, world!\n";
    return 0;
}
```

- `#include <iostream>` makes the console input/output tools available.
- `int main()` is where the program starts. The braces contain its body.
- `std::cout` writes to the console. `<<` sends text to it.
- `"Hello, world!"` is a string literal. `\n` moves output to a new line.
- `return 0;` tells the operating system the program finished successfully.
- C++ statements usually end with a semicolon. Braces group a block of code.

`std::` means the name belongs to the C++ standard library's `std` namespace. Writing it explicitly avoids ambiguity as projects grow.
