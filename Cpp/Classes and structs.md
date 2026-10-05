# Classes and structs

A `struct` or `class` groups related data and functions into a new type. This is useful when several values describe one thing.

```cpp
#include <string>

struct Person {
    std::string name;
    int age{};
};

int main() {
    Person person{"Ada", 36};
}
```

Access a public member with the dot operator: `person.name` or `person.age`.

A `class` is similar, but its members are private by default. A `struct`'s members are public by default. Use `private:` for implementation details and `public:` for the operations callers may use.

```cpp
class Counter {
public:
    void increment() { ++value; }
    int get() const { return value; }

private:
    int value{};
};
```

A `const` member function promises not to modify the object's observable state. Keep data private when the class must enforce rules, and expose simple public functions to use it.

You do not need a class for every group of values. A struct is a good simple container for related data; use a class when behavior or rules need to be protected.
