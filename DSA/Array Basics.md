# Array Basics

An array stores elements in an ordered sequence. Each element is identified by an index, so arrays are useful when values need to be accessed or processed by position.

## Indexing and memory

Most languages use zero-based indexing. For an array with `N` elements, valid indices are `0` through `N - 1`.

Array elements occupy contiguous memory. If each element takes `s` bytes and the first element is at address `base`, then:

```text
address(arr[i]) = base + i * s
```

This lets the computer locate an element directly from its index, giving array access `O(1)` time.

## Size and capacity

- **Size:** number of elements currently stored.
- **Capacity:** number of elements the allocated storage can hold.

For `[10, 20, 30, _, _]`, the size is `3` and capacity is `5`. A fixed-size array cannot grow in place. A dynamic array (such as C++ `vector` or Java `ArrayList`) can grow by allocating a larger block and copying elements when needed.

## Array dimensions

- **1D:** a single sequence, e.g. `[5, 10, 15]`.
- **2D:** rows and columns; an element is addressed with two indices, e.g. `matrix[row][column]`.
- **Multidimensional:** three or more indices, for data represented across several dimensions.

## Core operations

| Operation | Typical time | Why |
|---|---:|---|
| Access by index | `O(1)` | Address is calculated directly |
| Update by index | `O(1)` | Locate the position directly |
| Traverse all `N` elements | `O(N)` | Visit each element |
| Linear search | `O(N)` worst case | May inspect every element |
| Binary search | `O(log N)` | Repeatedly halves the search range; requires sorted data |
| Insert at end with free capacity | `O(1)` | No existing elements move |
| Insert at beginning or middle | `O(N)` | Elements must shift right |
| Delete last element | `O(1)` | No elements move |
| Delete beginning or middle | `O(N)` | Following elements must shift left |

These operation costs assume storage is already allocated. Resizing a dynamic array requires extra memory and copying; appending to a full dynamic array can therefore take `O(N)` for that operation, even though appends are typically efficient over a sequence of operations.

## Insertion and deletion

To insert `X` at index `K` in an array with spare capacity:

1. Check that `0 <= K <= size` and that capacity is available.
2. Shift elements from the end toward `K`, moving **right to left** so values are not overwritten.
3. Write `X` at `K` and increment the size.

Example: insert `25` at index `2`:

```text
[10, 20, 30, 40, _]
[10, 20, _, 30, 40]
[10, 20, 25, 30, 40]
```

To delete the element at index `K`:

1. Check that `0 <= K < size`.
2. Shift following elements one position left.
3. Decrement the logical size. The allocated capacity usually stays the same.

## Searching

**Linear search** checks values in order and returns the index when the target is found. If the target is absent, or appears last, it checks all `N` elements: `O(N)` time and `O(1)` auxiliary space.

**Binary search** is available when the array is sorted. It compares against the middle element and discards half the remaining range each step, taking `O(log N)` time. It cannot be applied directly to an unsorted array.

## Strengths and limitations

**Strengths**

- Fast random access by index.
- Contiguous storage supports efficient traversal and good cache performance.
- Simple representation for sequences; arrays also underpin structures such as matrices and heaps.

**Limitations**

- A fixed-size array has limited capacity; resizing means allocating and copying.
- Inserting or deleting near the beginning or middle requires shifting elements.
- Allocated but unused slots may waste memory.
- Traditional arrays generally store elements of one type.
- Invalid indices can cause errors or undefined behavior, depending on the language.

## Common pitfalls

- For size `N`, index `N` is out of bounds; the last valid index is `N - 1`.
- Keep logical size distinct from capacity.
- Shift right-to-left for insertion and left-to-right for deletion.
- Update the logical size after insertion or deletion.
- Check capacity before inserting into a fixed-size array.
- Use binary search only on sorted data.

## Quick recall

```text
Index access/update: O(1)
Visit or linearly search N elements: O(N)
Binary search (sorted array): O(log N)
Middle insert/delete: O(N) due to shifting
```

Source: [Array Basics — takeUforward](https://takeuforward.org/blogs/data-structure-and-algorithm/array-basics)
