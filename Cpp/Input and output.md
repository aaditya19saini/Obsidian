# Input and output

Use `std::cout` to display output and `std::cin` to read console input. Both are in `<iostream>`.

```cpp
#include <iostream>

int main() {
    int age{};
    std::cout << "Enter your age: ";
    std::cin >> age;
    std::cout << "You entered " << age << '\n';
}
```

`<<` sends values to output; `>>` extracts a value from input. `std::cin >>` skips leading whitespace and reads one value. Reading a string this way stops at whitespace, so `Ada Lovelace` would read as only `Ada`.

## Read a full line

Use `std::getline` for text containing spaces. Include `<string>`.

```cpp
#include <iostream>
#include <string>

int main() {
    std::string fullName;
    std::cout << "Enter your full name: ";
    std::getline(std::cin, fullName);
    std::cout << "Hello, " << fullName << '\n';
}
```

## Mixing `>>` and `getline`

After `std::cin >> age`, the newline from pressing Enter remains in the input stream. A following `getline` would consume that newline and return an empty string. Discard the rest of the current line first:

```cpp
#include <iostream>
#include <limits>
#include <string>

int main() {
    int age{};
    std::string name;

    std::cin >> age;
    std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');
    std::getline(std::cin, name);
}
```

## Check input

Invalid text or a number outside the destination type's range makes extraction fail. Check before using the value:

```cpp
int number{};
if (!(std::cin >> number)) {
    std::cout << "Please enter a valid whole number.\n";
    return 1;
}
```

Once a stream fails, later reads also fail until its state is cleared and bad input is removed. For small programs, showing an error and exiting is often simplest. See [[Errors and debugging]] and [[Integer types and long long]].

Use `'\n'` for a line break. `std::endl` also flushes the output buffer, which is usually unnecessary for ordinary output.
