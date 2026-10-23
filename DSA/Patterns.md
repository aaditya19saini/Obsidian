# Pattern Problems

Pattern problems turn a shape into a set of loop bounds. The key is to decide what each row prints, then translate that rule into the inner loop.

## A reliable approach

1. Let `n` be the pattern's size (often its number of rows).
2. Count rows with the outer loop. Use `i` for the row number.
3. For each row, identify its parts: leading spaces, symbols or numbers, and any gaps between them.
4. Write the count for each part as a function of `i` and `n`.
5. Print one row, then print a newline after the inner loop(s).
6. Check the first row, a middle row, and the last row. For symmetric patterns, compare the left and right halves.

Use a small trace table before coding when the bounds are unclear:

| Row `i` | Spaces | Symbols / values |
|---:|---:|---|
| 1 | ... | ... |
| 2 | ... | ... |
| ... | ... | ... |

## Starter patterns

### Solid square

Both row and column counts stay fixed at `n`.

```text
****
****
****
****
```

```cpp
for (int i = 0; i < n; ++i) {
    for (int j = 0; j < n; ++j) cout << "*";
    cout << '\n';
}
```

### Increasing left triangle

Row `i` prints `i` symbols (with rows numbered from 1).

```text
*
**
***
****
```

```cpp
for (int i = 1; i <= n; ++i) {
    for (int j = 1; j <= i; ++j) cout << "*";
    cout << '\n';
}
```

### Decreasing left triangle

Row `i` prints `n - i + 1` symbols.

```text
****
***
**
*
```

```cpp
for (int i = 1; i <= n; ++i) {
    for (int j = 1; j <= n - i + 1; ++j) cout << "*";
    cout << '\n';
}
```

### Counting triangle

If the value depends on the column, print `j`. If every value in a row is the same, print `i` instead.

```text
1
1 2
1 2 3
1 2 3 4
```

```cpp
for (int i = 1; i <= n; ++i) {
    for (int j = 1; j <= i; ++j) cout << j << ' ';
    cout << '\n';
}
```

## Symmetric patterns

For a centered pyramid, the number of leading spaces decreases as the row grows, while the number of symbols increases by two:

| Row `i` (1-based) | Leading spaces | Symbols |
|---:|---:|---:|
| 1 | `n - 1` | 1 |
| 2 | `n - 2` | 3 |
| `i` | `n - i` | `2*i - 1` |

The pyramid's widest row has `2*n - 1` symbols. For a diamond, pair the increasing pyramid with a decreasing inverted pyramid, taking care not to print the widest row twice.

## Common loop layouts

- **Rectangle or square:** fixed number of rows and fixed number of columns.
- **Growing triangle:** columns `1..i`.
- **Shrinking triangle:** columns `1..n-i+1`.
- **Right-aligned triangle:** print `n-i` spaces, then `i` symbols.
- **Pyramid:** print `n-i` spaces, then `2*i-1` symbols.
- **Hollow shape:** print a symbol on a boundary; print a space in the interior. For a rectangle, the boundary condition is `i == 1 || i == n || j == 1 || j == n`.

## Common mistakes

- Mixing 0-based and 1-based row numbers. Choose one convention and derive every bound from it.
- Putting the newline inside the inner loop, which breaks one row into many lines.
- Forgetting that spaces count as output columns in aligned patterns.
- Using `n - i` where the row count should be `n - i + 1` (or the reverse). Trace the first and last rows to catch off-by-one errors.
- Printing a trailing space after every value. This is usually accepted, but print separators only between values when exact formatting matters.

## Complexity

If an `n` by `n` pattern visits every cell, it takes `O(n^2)` time. A triangle with row lengths `1, 2, ..., n` prints `n(n+1)/2` items, also `O(n^2)`. The output itself usually dominates the work; aside from the output, the loop variables use `O(1)` extra space.
