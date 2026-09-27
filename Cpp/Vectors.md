Think of a vector as:

> **A dynamic array that can grow and shrink while your program is running.**

---

# 1. What is a vector?

A normal C++ array has a fixed size:

```cpp
int numbers[5] = {10, 20, 30, 40, 50};
```

You decided its size is `5`.

A vector:

```cpp
#include <vector>

std::vector<int> numbers = {10, 20, 30, 40, 50};
```

can grow:

```cpp
numbers.push_back(60);
numbers.push_back(70);
```

Now:

```text
10 20 30 40 50 60 70
```

The vector automatically manages the memory required to store the additional elements.

---

# 2. Creating vectors

Basic:

```cpp
std::vector<int> v;
```

Empty vector of integers.

With initial values:

```cpp
std::vector<int> v = {10, 20, 30, 40};
```

You can also write:

```cpp
std::vector<int> v{10, 20, 30, 40};
```

Create a vector of 5 zeros:

```cpp
std::vector<int> v(5);
```

```text
[0, 0, 0, 0, 0]
```

Create 5 copies of 7:

```cpp
std::vector<int> v(5, 7);
```

```text
[7, 7, 7, 7, 7]
```

---

# 3. Accessing elements

Exactly like an array:

```cpp
std::vector<int> v = {10, 20, 30, 40};

cout << v[0];
```

Output:

```text
10
```

Indexes start at **0**.

```text
index:    0   1   2   3
          ↓   ↓   ↓   ↓
vector:  10  20  30  40
```

You can modify them:

```cpp
v[2] = 100;
```

Now:

```text
10 20 100 40
```

---

# 4. `push_back()` ⭐

This is one of the most important vector functions.

```cpp
v.push_back(50);
```

It adds an element to the **end**.

Suppose:

```cpp
vector<int> v = {10, 20, 30};
```

Then:

```cpp
v.push_back(40);
```

becomes:

```text
Before:

[10] [20] [30]

             ↑
            end


After:

[10] [20] [30] [40]
```

You were asking about `push_back()` earlier. That's literally its job:

> **push an element onto the back of the vector.**

---

# 5. `pop_back()`

Removes the last element.

```cpp
vector<int> v = {10, 20, 30, 40};

v.pop_back();
```

Result:

```text
10 20 30
```

Important:

```cpp
v.pop_back();
```

does **not return the removed value**.

If you need the value first:

```cpp
int x = v.back();
v.pop_back();
```

---

# 6. `size()`

Tells you how many elements are currently inside.

```cpp
vector<int> v = {10, 20, 30, 40};

cout << v.size();
```

Output:

```text
4
```

Notice:

```cpp
v.size()
```

is the **number of elements**, not the last index.

For:

```text
[10] [20] [30] [40]
```

size = `4`

last index = `3`

---

# 7. `front()` and `back()`

```cpp
v.front();
```

gets the first element.

```cpp
v.back();
```

gets the last element.

Example:

```cpp
vector<int> v = {10, 20, 30, 40};

cout << v.front();  // 10
cout << v.back();   // 40
```

These are especially useful when you're treating a vector like a sequence.

---

# 8. Iterating through a vector

The classic way:

```cpp
for (int i = 0; i < v.size(); i++) {
    cout << v[i] << " ";
}
```

Output:

```text
10 20 30 40
```

This is extremely important because you'll use this constantly.

### Range-based `for`

Modern C++ gives you:

```cpp
for (int x : v) {
    cout << x << " ";
}
```

Meaning:

> For every element `x` inside `v`, do this.

Much cleaner.

---

# 9. Modifying elements with a loop

Suppose:

```cpp
vector<int> v = {1, 2, 3, 4};
```

You want to double everything.

You could do:

```cpp
for (int i = 0; i < v.size(); i++) {
    v[i] *= 2;
}
```

Result:

```text
2 4 6 8
```

There's another important version:

```cpp
for (int& x : v) {
    x *= 2;
}
```

The `&` means `x` refers to the actual element rather than being a copy.

---

# 10. `empty()`

Checks whether the vector contains anything.

```cpp
if (v.empty()) {
    cout << "Vector is empty";
}
```

It returns:

```text
true
```

or

```text
false
```

So:

```cpp
if (!v.empty()) {
    cout << v.back();
}
```

is useful when you're not sure whether the vector has elements.

---

# 11. Removing elements

You already have:

```cpp
v.pop_back();
```

for removing the last element.

But you can remove an element from the middle using `erase()`.

```cpp
vector<int> v = {10, 20, 30, 40};
```

Remove `30`:

```cpp
v.erase(v.begin() + 2);
```

Result:

```text
10 20 40
```

What's happening?

`v.begin()` points to the first element.

```text
v.begin()
   ↓
[10] [20] [30] [40]
```

`v.begin() + 2`:

```text
          ↓
[10] [20] [30] [40]
```

So:

```cpp
v.erase(v.begin() + 2);
```

means:

> Remove the element at index 2.

---

# 12. `clear()`

Deletes all elements:

```cpp
v.clear();
```

Before:

```text
[10] [20] [30] [40]
```

After:

```text
[]
```

And:

```cpp
v.size()
```

becomes `0`.

---

# 13. Inserting elements

You can insert something at a particular position:

```cpp
vector<int> v = {10, 20, 40};
```

Insert `30` before `40`:

```cpp
v.insert(v.begin() + 2, 30);
```

Result:

```text
10 20 30 40
```

So:

```cpp
v.insert(position, value);
```

---

# 14. Vector of strings

Vectors aren't restricted to integers.

```cpp
vector<string> names = {
    "Aaditya",
    "John",
    "Sarah"
};
```

Then:

```cpp
names.push_back("Mike");
```

Result:

```text
Aaditya John Sarah Mike
```

---

# 15. Vector of doubles

```cpp
vector<double> temperatures = {
    32.5, 31.2, 29.8
};
```

---

# 16. Vector of vectors

This is where shit gets interesting.

You can have:

```cpp
vector<vector<int>> matrix;
```

That's basically a dynamic 2D array.

For example:

```cpp
vector<vector<int>> matrix = {
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
```

Visualize it as:

```text
1 2 3
4 5 6
7 8 9
```

Access:

```cpp
matrix[1][2]
```

gives:

```text
6
```

Because:

```text
matrix[1] → {4, 5, 6}

matrix[1][2] → 6
```

---

# 17. `capacity()` vs `size()`

This is one of the more important concepts underneath vectors.

Suppose:

```cpp
vector<int> v;

v.push_back(10);
v.push_back(20);
v.push_back(30);
```

You have:

```cpp
v.size()
```

which might be:

```text
3
```

But internally the vector may have allocated space for more elements.

That's:

```cpp
v.capacity()
```

For example:

```text
size = 3
capacity = 4
```

Meaning:

```text
Currently being used:
[10] [20] [30]

Allocated space:
[10] [20] [30] [   ]
```

If you add another:

```cpp
v.push_back(40);
```

there's room.

But eventually capacity gets exhausted.

The vector then allocates a larger block of memory and moves/copies the elements there.

That's one reason vectors are called **dynamic arrays**.

---

# 18. `reserve()`

If you know you're going to add a lot of elements, you can tell the vector to allocate memory beforehand.

```cpp
vector<int> v;

v.reserve(1000);
```

Now the vector has capacity for at least 1000 elements.

But:

```cpp
v.size()
```

is still:

```text
0
```

This distinction is important:

```text
reserve() → memory allocation

size() → actual elements
```

For example:

```cpp
vector<int> v;

v.reserve(100);

cout << v.size();      // 0
cout << v.capacity();  // >= 100
```

---

# 19. `resize()`

`resize()` actually changes the number of elements.

```cpp
vector<int> v = {1, 2, 3};

v.resize(5);
```

Now:

```text
1 2 3 0 0
```

Whereas:

```cpp
v.reserve(5);
```

would still leave:

```text
1 2 3
```

So remember:

**`reserve()` = prepare space**

**`resize()` = change the vector's size**

---

# 20. Sorting vectors

This is extremely useful.

```cpp
#include <algorithm>

vector<int> v = {5, 2, 8, 1, 9};

sort(v.begin(), v.end());
```

Result:

```text
1 2 5 8 9
```

Reverse:

```cpp
sort(v.rbegin(), v.rend());
```

Result:

```text
9 8 5 2 1
```

You'll use `vector + algorithm` **a lot** in C++.

---

# 21. A complete example

Let's put everything together.

```cpp
#include <iostream>
#include <vector>
#include <algorithm>

using namespace std;

int main() {

    vector<int> numbers;

    numbers.push_back(50);
    numbers.push_back(20);
    numbers.push_back(80);
    numbers.push_back(10);

    cout << "Original: ";

    for (int x : numbers) {
        cout << x << " ";
    }

    cout << "\n";

    sort(numbers.begin(), numbers.end());

    cout << "Sorted: ";

    for (int x : numbers) {
        cout << x << " ";
    }

    cout << "\n";

    cout << "Size: " << numbers.size() << "\n";
    cout << "First: " << numbers.front() << "\n";
    cout << "Last: " << numbers.back() << "\n";

    numbers.pop_back();

    cout << "After pop_back: ";

    for (int x : numbers) {
        cout << x << " ";
    }
}
```

Output:

```text
Original: 50 20 80 10
Sorted: 10 20 50 80
Size: 4
First: 10
Last: 80
After pop_back: 10 20 50
```

---

# 22. The vector cheat sheet

These are the ones I'd memorize first:

|Operation|Code|
|---|---|
|Create|`vector<int> v;`|
|Initialize|`vector<int> v = {1,2,3};`|
|Add to end|`v.push_back(5);`|
|Remove last|`v.pop_back();`|
|First element|`v.front();`|
|Last element|`v.back();`|
|Access index|`v[i];`|
|Number of elements|`v.size();`|
|Empty?|`v.empty();`|
|Remove everything|`v.clear();`|
|Insert|`v.insert(...);`|
|Erase|`v.erase(...);`|
|Sort|`sort(v.begin(), v.end());`|
|Reserve memory|`v.reserve(n);`|
|Change size|`v.resize(n);`|
|Capacity|`v.capacity();`|

---

# 23. The mental model I want you to have

Don't think of:

```cpp
vector<int> v;
```

as some magical C++ object.

Think:

```text
             VECTOR
               │
               ▼
        ┌─────────────────┐
        │ 10 │ 20 │ 30 │  │
        └─────────────────┘
          ↑    ↑    ↑
        index index index
          0    1    2

size = 3
capacity = maybe 4
```

Then:

```cpp
v.push_back(40);
```

becomes:

```text
        ┌─────────────────────┐
        │ 10 │ 20 │ 30 │ 40  │
        └─────────────────────┘

size = 4
```

And when there's no room left, C++ handles allocating a larger chunk of memory and moving the elements.

That's the core idea.

---

## What you should learn next

Once you're comfortable with vectors, I'd go in this order:

```text
vector
  ↓
iterators
  ↓
references (&)
  ↓
pointers
  ↓
arrays
  ↓
strings
  ↓
STL algorithms
  ↓
maps / unordered_map
  ↓
sets
  ↓
stacks / queues
```

And **don't just read this**. Write a little program that takes `n` numbers from the user, stores them in a vector, then finds the **mean, maximum, minimum, and standard deviation**. That'll make vectors stick very quickly.