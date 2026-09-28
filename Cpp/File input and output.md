# File input and output

The `<fstream>` header provides streams for reading and writing files. Check that a file opened successfully before using it.

## Read a file

```cpp
#include <fstream>
#include <iostream>
#include <string>

int main() {
    std::ifstream input{"notes.txt"};
    if (!input) {
        std::cerr << "Could not open notes.txt\n";
        return 1;
    }

    std::string line;
    while (std::getline(input, line)) {
        std::cout << line << '\n';
    }
}
```

The path is interpreted relative to the program's current working directory, which may differ from the source file's folder. Use a known path or configure the working directory when needed.

## Write a file

```cpp
#include <fstream>
#include <iostream>

int main() {
    std::ofstream output{"result.txt"};
    if (!output) {
        std::cerr << "Could not create result.txt\n";
        return 1;
    }

    output << "First line\n";
}
```

Opening an `std::ofstream` this way creates the file or replaces its existing contents. To append instead, use `std::ofstream output{"result.txt", std::ios::app};`.

Streams close automatically when they leave scope. Check stream state after operations if a partial read/write would be a problem. See [[Errors and debugging]] and [[Multiple source files]].
