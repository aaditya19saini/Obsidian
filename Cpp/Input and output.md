# Input and output

C++ console programs commonly use `std::cout` to display output and `std::cin` to read input. Both are provided by the `<iostream>` header.

```cpp
#include <iostream>

int main() {
    int age{};

    std::cout << "Enter your age: ";
    std::cin >> age;

    std::cout << "You entered " << age << '\n';
}
```

## Displaying output with `std::cout`

The insertion operator `<<` sends values to the output stream. You can chain values together:

```cpp
std::cout << "Age: " << age << '\n';
```

`'\n'` starts a new line. `std::endl` also starts a new line, but it additionally flushes the output buffer; use `'\n'` for ordinary line breaks.

## Reading a value with `std::cin >>`

The extraction operator `>>` reads a value from the input stream:

```cpp
int count{};
std::cin >> count;
```

Formatted extraction skips leading whitespace and reads one value. For example, reading a `std::string` this way stops at the first space:

```cpp
std::string firstName;
std::cin >> firstName; // Input: Ada Lovelace -> stores "Ada"
```

Include `<string>` when using `std::string`.

## Reading a whole line with `std::getline`

Use `std::getline` when the input can contain spaces:

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

`std::getline` reads until the user presses Enter and keeps spaces in the string.

## Mixing `>>` and `getline`

After `std::cin >> number`, the Enter key remains in the input stream as a newline. A `getline` immediately afterward sees that newline and returns an empty line.

```cpp
#include <iostream>
#include <limits>
#include <string>

int main() {
    int age{};
    std::string name;

    std::cout << "Enter your age: ";
    std::cin >> age;

    // Discard the rest of this line, including its newline.
    std::cin.ignore(std::numeric_limits<std::streamsize>::max(), '\n');

    std::cout << "Enter your name: ";
    std::getline(std::cin, name);

    std::cout << name << " is " << age << " years old.\n";
}
```

The call to `ignore` needs `<limits>`. It discards the rest of the current line so the next `getline` can read the user's answer.

## Check whether input worked

If the user enters text where an integer is expected, or a number too large for the type, extraction fails. Check the stream before using the value:

```cpp
int number{};

if (!(std::cin >> number)) {
    std::cout << "Please enter a valid whole number.\n";
    return 1;
}
```

When extraction fails, `std::cin` enters a failed state. Later reads will also fail until the state is cleared and the invalid input is removed. For a beginner program, reporting the problem and ending is often the simplest response.

## Quick guide

| Goal | Use |
| --- | --- |
| Print text or values | `std::cout << value;` |
| Read one number or one word | `std::cin >> value;` |
| Read a full line with spaces | `std::getline(std::cin, text);` |
| Start a new output line | `'\n'` |
| Use `getline` after `>>` | `std::cin.ignore(...)` to discard the pending newline |
