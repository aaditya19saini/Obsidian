# Functions and scope

A function is a named block of code that performs a task. Functions help break a program into understandable pieces.

```cpp
int add(int left, int right) {
    return left + right;
}

int main() {
    int total{add(3, 4)};
}
```

`int` before `add` is its return type. `left` and `right` are parameters. `return` sends a result back to the caller. Use `void` when a function does not return a value.

## Pass by value and by reference

By default, a function receives a copy:

```cpp
void printScore(int score) { /* changing score won't change caller's variable */ }
```

A reference parameter refers to the caller's object, so a function can change it without copying:

```cpp
void addOne(int& number) {
    ++number;
}
```

Use a const reference for a large value that should not be copied or changed:

```cpp
void printName(const std::string& name);
```

For small types such as `int`, passing by value is usually simple and clear.

## Declarations and definitions

A function must be declared before it is used, or defined earlier in the file. A declaration tells the compiler its name, return type, and parameters:

```cpp
int add(int left, int right); // declaration
```

The body with `{ ... }` is the definition. See [[Multiple source files]] for placing declarations in headers and definitions in `.cpp` files.

## Scope

A local variable exists only inside the block where it is declared. A function's parameters are local to that function. Prefer passing needed values as parameters rather than relying on global variables.

## Small design rules

Give each function one clear job, use descriptive names, and keep the parameter list manageable. `main` can coordinate smaller functions rather than containing every step.
