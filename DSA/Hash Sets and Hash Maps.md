
	```

Hashing stores or retrieves information by a **key**. It is useful when an algorithm repeatedly needs to test membership, count occurrences, or look up data associated with a value

## Core idea

A **hash function** transforms a key into a hash value, which is used to choose a bucket or location in a **hash table**. For example, `hash(key) = key % 10` maps `12` to bucket `2`.

A hash table is the underlying idea; common interfaces built on it are:

- **Hash set:** stores unique keys. Use it for membership checks or distinct values.
- **Hash map:** stores key-value pairs. Use it when each key has associated information, such as a frequency.

In C++, the standard hash-based containers are `unordered_set` and `unordered_map`.

## When hashing helps

Use hashing when you need to:

- Check quickly whether an element has appeared.
- Count frequencies of numbers, characters, or words.
- Count distinct values.
- Associate a key with data, such as `student ID -> marks`.
- Avoid repeatedly scanning an array or string for the same value.

For example, the array `[2, 5, 2, 8, 5, 2]` can be summarized as:

```text
2 -> 3
5 -> 2
8 -> 1
```

## Hash set vs. hash map

| Structure | Stores | Typical use |
|---|---|---|
| Hash set | Unique keys | “Have I seen this value?”; count distinct values |
| Hash map | Key -> value | “How many times?”; associate extra information with a key |

Example with the same input:

```text
Set: {2, 5, 8}
Map: {2 -> 3, 5 -> 2, 8 -> 1}
```

## Frequency counting pattern

Traverse once and update the count for each item:

```cpp
unordered_map<int, int> freq;
for (int x : nums) {
    ++freq[x];
}
```

For characters:

```cpp
unordered_map<char, int> freq;
for (char ch : s) {
    ++freq[ch];
}
```

To count distinct values, either insert into a set and use its size, or count the distinct keys in a frequency map.

## Collisions

A **collision** occurs when different keys produce the same hash location. For example, with `key % 10`, both `12` and `22` map to bucket `2`. A hash table must handle collisions so keys can still be stored and found correctly.

Common strategies:

- **Separate chaining:** each bucket holds a collection of entries that map there.
- **Open addressing:** entries stay in the table; on collision, probing searches for another available slot. Linear and quadratic probing are examples.

Collisions are expected; a good hash table handles them while keeping operations efficient on average.

## Complexity

| Operation | Average | Worst case |
|---|---:|---:|
| Search / membership | `O(1)` | `O(N)` |
| Insert | `O(1)` | `O(N)` |
| Delete | `O(1)` | `O(N)` |

`N` is the number of stored keys. Average constant time relies on a good distribution of keys and manageable collisions. If many keys collide, an operation may need to inspect many entries.

Building a frequency map for `N` input elements takes `O(N)` average time and up to `O(U)` extra space, where `U` is the number of distinct keys. The worst-case time can degrade if collisions are pathological.

## Example: highest-frequency element

For `[1, 2, 2, 3, 1, 2]`, the counts are `1 -> 2`, `2 -> 3`, and `3 -> 1`, so the answer is `2`.

If multiple values tie and the required answer is the one appearing first in the input, preserve that tie rule explicitly. One simple approach is to build the frequency map, then scan the original array from left to right and update the answer only when a strictly larger frequency is found. This ensures the first value among tied candidates remains selected.

## Common mistakes

- Using a set when you need counts or other values associated with keys; use a map instead.
- Assuming hash operations are guaranteed `O(1)`; that is the average case, while worst case can be `O(N)`.
- Forgetting the problem's tie-breaking rule when selecting a most-frequent value.
- Iterating over a hash map and assuming keys appear in insertion or sorted order. Hash maps generally do not guarantee either order; scan the original input when order matters.

## Quick recall

```text
Need membership / uniqueness?     -> hash set
Need key -> associated data?       -> hash map
Frequency counting?                -> map[item]++
Average lookup / insert / delete?   -> O(1)
Worst-case hash operation?          -> O(N)
Collision?                          -> different keys map to same bucket
```

Source: [Hashing in Data Structures: Hash Maps and Collisions — takeUforward](https://takeuforward.org/blogs/data-structure-and-algorithm/hashing-data-structures)
