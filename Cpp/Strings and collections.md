# Strings and collections

## Text with `std::string`

Include `<string>` to use `std::string`:

```cpp
std::string name{"Ada"};
name += " Lovelace";
std::cout << name << '\n';
```

A string can contain spaces. Use `std::getline` to read a whole line; `std::cin >> name` reads only up to whitespace. See [[Input and output]].

## Fixed-size arrays

An array stores a fixed number of elements of the same type:

```cpp
int scores[3]{80, 95, 72};
std::cout << scores[0]; // first item
```

Indexes start at zero; valid indexes here are 0, 1, and 2. Accessing outside the array's bounds is a bug. For most beginner programs, prefer `std::vector` when the number of elements can change.

## `std::vector`

Include `<vector>`. A vector is a resizable sequence of values of one type:

```cpp
#include <vector>

std::vector<int> scores{80, 95, 72};
scores.push_back(88);
std::cout << scores.size();
```

Use `scores[i]` to access an element, `push_back` to add one at the end, `size()` to get the element count, and `empty()` to check whether it has any elements. Valid indexes are from zero up to but not including `size()`.

```cpp
for (int score : scores) {
    std::cout << score << '\n';
}
```

Use `for (int& score : scores)` to modify each element. See [[Vectors]] for more detail on insertion, removal, sorting, size, and capacity.

## Choose the right container

Start with `std::string` for text and `std::vector<T>` for a sequence that may grow or shrink. Learn other containers such as maps and sets when a problem needs lookup by key or unique values.
