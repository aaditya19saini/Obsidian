# Build and run

C++ source code (`.cpp`) must be compiled into an executable before it can run. The compiler translates source files; the linker joins compiled pieces and libraries into a program.

## Compile a single file

With GCC or MinGW, from the folder containing `hello.cpp`:

```sh
g++ -std=c++20 -Wall -Wextra -pedantic hello.cpp -o hello
```

On Windows, the output may be named `hello.exe`. Run it from the terminal with `./hello` on many Unix-like shells or `./hello.exe` in PowerShell, depending on the environment.

- `-std=c++20` selects the language version.
- `-Wall -Wextra -pedantic` asks the compiler to report useful warnings.
- `-o hello` names the output program.

In VS Code, select the build task configured for the active `.cpp` file. Build the file that contains `main`, and include other source files when the project has them. See [[Multiple source files]].

## Errors and warnings

A compiler error means no executable was produced. Fix errors before running. A warning may point to suspicious code even when compilation succeeds; understand and fix warnings rather than ignoring them.

If the program compiles but behaves incorrectly, that is a runtime or logic problem. See [[Errors and debugging]].
