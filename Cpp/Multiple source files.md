# Multiple source files and program communication

There are two different ideas that are easy to mix up:

1. **Several source files make one program.** The compiler and linker combine `.cpp` files into one executable.
2. **Separate programs communicate while running.** They exchange data through input/output, files, pipes, or a network connection.

## Build one program from several C++ files

For a small project, a header (`.h`) declares functions and a source file (`.cpp`) defines them.

`greeting.h` — declaration:

```cpp
#pragma once
#include <string>

std::string makeGreeting(const std::string& name);
```

`greeting.cpp` — definition:

```cpp
#include "greeting.h"

std::string makeGreeting(const std::string& name) {
    return "Hello, " + name + "!";
}
```

`main.cpp` — uses the function:

```cpp
#include <iostream>
#include "greeting.h"

int main() {
    std::cout << makeGreeting("Ada") << '\n';
}
```

Compile both `.cpp` files together. With GCC or MinGW:

```sh
g++ -std=c++20 -Wall -Wextra -pedantic main.cpp greeting.cpp -o greeting
```

On Windows, run the resulting `greeting.exe`. The exact compiler command can vary by toolchain.

The header tells each source file what the function looks like; the `.cpp` file provides its implementation. Include the header in both places so the compiler can check that the declaration and definition agree. `#pragma once` is widely supported; portable code can use traditional include guards instead.

Do not `#include` a `.cpp` file. Compile each `.cpp` source file once and let the linker connect the function calls. If the linker reports an undefined reference, check that the defining `.cpp` file was included in the build command and that names/signatures match.

## Separate programs talking to each other

A simple way for one program to provide data to another is standard input and output. One program prints a documented format; the other reads that format. Files work similarly when programs need to exchange data later or independently. For more advanced cases, operating systems provide pipes, and network programs use sockets.

Agree on the data format and who owns each step. For example, one program can write one number per line to a file, and another can read each line and validate it. Handle missing files, malformed data, and failed reads. Avoid relying on informal screen text as a data format if another program must parse it.

Use multiple `.cpp` files when organizing one application. Use files or streams when independent programs need to exchange data. See [[Input and output]], [[Errors and debugging]], and [[Build and run]].
