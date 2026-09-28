# Vectors (`std::vector`)

A vector is a resizable sequence of values of one type. Include `<vector>` to use it.

```cpp
#include <iostream>
#include <vector>

int main() {
    std::vector<int> scores{80, 95, 72};
    scores.push_back(88); // add to the end

    for (int score : scores) {
        std::cout << score << ' ';
    }
}
```

## Create and access

```cpp
std::vector<int> empty;            // no elements
std::vector<int> values{2, 4, 6}; // three values
std::vector<int> zeros(5);         // five zero-initialized ints
std::vector<int> sevens(5, 7);     // five copies of 7
```

Indexes begin at zero. For three elements, valid indexes are `0`, `1`, and `2`. Accessing an invalid index is a bug. `at(index)` checks the index and throws an exception when it is out of range; `operator[]` does not check it.

```cpp
int first{values[0]};
values[1] = 10;
```

## Common operations

| Operation | Meaning |
| --- | --- |
| `v.size()` | Number of elements |
| `v.empty()` | Whether there are no elements |
| `v.push_back(x)` | Add `x` at the end |
| `v.pop_back()` | Remove the last element; does not return it |
| `v.front()` / `v.back()` | First / last element; only use when nonempty |
| `v.clear()` | Remove all elements |
| `v.insert(pos, x)` | Insert before an iterator position |
| `v.erase(pos)` | Remove the element at an iterator position |

To remove the last item while keeping its value, read `v.back()` before calling `pop_back()`. Check that a vector is not empty before using `front()`, `back()`, or `pop_back()`.

## Loop over elements

```cpp
for (int value : values) {       // value is a copy
    std::cout << value << '\n';
}

for (int& value : values) {      // reference can modify the element
    ++value;
}
```

Use `const int&` instead of `int` for a large element type that should not be copied or changed.

## Size and capacity

`size()` is the number of existing elements. `capacity()` is how many elements can fit before the vector needs to allocate more storage. `reserve(n)` may increase capacity but does not add elements. `resize(n)` changes the number of elements.

When a vector grows, it may move its elements to new storage. That can invalidate pointers, references, and iterators to its elements. Avoid keeping those across operations that may grow or modify the vector.

## Algorithms

Include `<algorithm>` to sort:

```cpp
#include <algorithm>
std::sort(values.begin(), values.end());
```

Use `std::vector` when a sequence's size can change. For fixed-size sequences, `std::array` (from `<array>`) is another option. See [[Strings and collections]] for the overview.
