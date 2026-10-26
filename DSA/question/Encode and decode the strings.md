[problem ](https://neetcode.io/problems/string-encode-and-decode/question?list=neetcode150)


The problem is called Encode and Decode Strings.

## 1. What problem are we solving?

Suppose you're given a vector of strings:

```
vector<string> strs = {"hello", "world"};
```

You want to encode it into a single string, something like:

```
5#hello5#world
```

Then, when you decode that single string, you should get the original vector back:

```
{"hello", "world"}
```

The tricky part is that strings can contain almost anything, including numbers and special characters.

For example:

```
{"hello", "12#world", ""}
```

If you simply separate strings using `#`, how would you know whether a `#` belongs to the separator or to the original string?

The solution is to store the length of each string before storing the string itself.

For example:

```
5#hello6#12#world0#
```

Here's how to read it:

- `5#hello`: the next 5 characters are `hello`.
    
- `6#12#world`: the next 6 characters are `12#wor`? No. Let's count carefully: `12#world` has 8 characters, so its correct encoding is `8#12#world`.
    
- `0#`: the next string has zero characters.
    

So the correct complete encoding is:

```
5#hello8#12#world0#
```

Notice that the `#` inside `12#world` causes no ambiguity. The decoder uses the length, not the contents, to find the end of each string.

## 2. Understanding `encode()`

Here's your first function:

```
string encode(vector<string>& strs) {
    string res;
    for (const string& s : strs) {
        res.append(to_string(s.size()));
        res.push_back('#');
        res.append(s);
    }
    return res;
}
```

Let's go line by line.

### Line 1: Create the output string

```
string res;
```

We create an empty string called `res`. Everything we encode will be added to it.

Initially:

```
res = ""
```

### Line 2: Loop through every string

```
for (const string& s : strs)
```

This is a range-based `for` loop.

It means: take each string from `strs`, one at a time, and refer to it as `s`.

Suppose:

```
strs = {"cat", "hello"}
```

The loop executes twice:

- First iteration: `s = "cat"`
    
- Second iteration: `s = "hello"`
    

A quick explanation of the syntax:

- `string&` means reference to an existing string, avoiding a copy.
    
- `const` means the function promises not to modify that string through `s`.
    

You don't need to master references right now, but it's good to recognize them.

### Line 3: Append the string's length

```
res.append(to_string(s.size()));
```

This line does two operations.

First, `s.size()`

Returns the number of characters in the string.

```
string s = "cat";
s.size();  // 3
```

Second, `to_string()`

Converts that number into a string.

```
to_string(3);  // "3"
```

Why convert it? Because `res` is a string, and we're adding characters to it.

So:

```
res.append(to_string(s.size()));
```

For `"cat"`, this produces:

```
res = "3"
```

### Line 4: Add the delimiter

```
res.push_back('#');
```

Adds the character `#` to the end.

Now:

```
res = "3#"
```

This marks the end of the length field. The decoder will use it to locate the number.

### Line 5: Append the actual string

```
res.append(s);
```

Adds the original string after the length and delimiter.

For `"cat"`:

```
res = "3#cat"
```

That's one string encoded!

### Let's trace the complete encoding

Step 1 of 5

Encoding

Start with an empty output string.

Output string (`res`)

## ""

PreviousNext step

Finally:

```
return res;
```

Returns the encoded string to whoever called the function.

## 3. Understanding `decode()`

Now comes the more interesting part. We have one long string, and we need to figure out where each original string begins and ends.

Here's your function:

```
vector<string> decode(string s) {
    vector<string> res;
    int i = 0;

    while (i < s.size()) {
        int j = i;

        while (s[j] != '#') {
            j++;
        }

        int length = stoi(s.substr(i, j - i));

        i = j + 1;
        j = i + length;

        res.push_back(s.substr(i, length));
        i = j;
    }

    return res;
}
```

Let's assume the input is:

```
3#cat5#hello
```

### Line 1: Create a vector for the decoded strings

```
vector<string> res;
```

Unlike the encoding function, we're no longer building one long string. We're collecting multiple strings in a vector.

Initially:

```
res = []
```

### Line 2: Set the starting position

```
int i = 0;
```

`i` represents the index where the next encoded string's length begins.

For our input:

```
3#cat5#hello
^
i = 0
```

### Line 3: Keep decoding while there is input left

```
while (i < s.size())
```

This loop continues as long as `i` is smaller than the total length of the encoded string.

In other words, stop when you've processed the entire input.

### Line 4: Initialize another pointer

```
int j = i;
```

We use `j` to search for the delimiter `#`.

At the start:

```
3#cat5#hello
^
i, j = 0
```

Why two variables?

- `i` tracks where the current encoded entry begins.
    
- `j` searches for the end of its length field.
    

Keeping them separate allows us to find the length without losing our starting position.

### Line 5: Find the delimiter

```
while (s[j] != '#') {
    j++;
}
```

This loop moves `j` forward until it finds `#`.

For the string:

```
3#cat5#hello
 ^
 j = 1
```

At index `0`, the character is `'3'`, not `'#'`, so `j` increments.

At index `1`, the character is `'#'`, so the loop stops.

Now:

```
i = 0
j = 1
```

The characters between `i` and `j` contain the length.

### Line 6: Extract and convert the length

```
int length = stoi(s.substr(i, j - i));
```

This line combines two functions.

`substr()`

```
s.substr(i, j - i)
```

Extracts a substring starting at index `i`, with `j - i` characters.

Here:

```
s.substr(0, 1);  // "3"
```

`stoi()`

Converts a numeric string into an integer.

```
stoi("3");  // 3
```

Therefore:

```
length = 3;
```

We now know that the original string contains exactly three characters.

### Line 7: Move past the delimiter

```
i = j + 1;
```

Remember, `j` points at `#`.

We move `i` one position beyond it, so `i` points at the beginning of the actual string.

```
3#cat5#hello
  ^
  i = 2
```

The string `cat` begins at index 2.

### Line 8: Calculate where the string ends

```
j = i + length;
```

We know:

```
i = 2
length = 3
```

Therefore:

```
j = 2 + 3;  // 5
```

This gives us the position immediately after the string.

Think of it as calculating the endpoint rather than searching for another delimiter.

### Line 9: Extract the original string

```
res.push_back(s.substr(i, length));
```

This extracts three characters starting at index 2:

```
s.substr(2, 3);  // "cat"
```

Then `push_back()` adds that string to the vector.

Now:

```
res = ["cat"]
```

### Line 10: Move to the next encoded entry

```
i = j;
```

We set `i` to the position immediately after the string we just decoded.

```
3#cat5#hello
     ^
     i = 5
```

The next length begins at index 5, where the character `'5'` is located.

The outer loop repeats, and the same process decodes `"hello"`.

Eventually:

```
res = ["cat", "hello"]
```

The loop ends when `i` reaches the end of the encoded string, and the function returns `res`.

## 4. The entire decoding process at a glance

Encoded input

## `3#cat5#hello`

## 3

Length

First iteration

Find `#`, parse length `3`, extract `cat`.

Decoded: `["cat"]`

## 5

Length

Second iteration

Find `#`, parse length `5`, extract `hello`.

Decoded: `["cat", "hello"]`

## 5. Why does this solution work?

The most important idea is that the decoder never needs to search for the end of the original string.

It reads the length, skips the delimiter, and extracts exactly that many characters.

That means all of these inputs work:

```
{"hello", "world"}
{"12#abc", "xyz"}
{"", "hello", ""}
{"12345", "###"}
```

Even if a string contains `#`, numbers, or an empty string, the decoder can reconstruct it correctly because the length tells it exactly how many characters to consume.

## 6. Time and space complexity

Let \(N\) be the total number of characters across all input strings.

- Encoding: \(O(N)\), because every character is appended to the output.
    
- Decoding: \(O(N)\), because the decoder scans the encoded string and extracts each original string.
    
- Space complexity: \(O(N)\) for the encoded or decoded output, excluding the input.
    

One small technical note: the decoding loop assumes the input is a valid string produced by `encode()`. Arbitrary malformed input could cause an out-of-bounds access in `s[j]`, so production code should validate the input.

## 7. The three things to remember

1. `s.size()` gets a string's length.
    
2. `stoi()` converts a numeric string into an integer.
    
3. `substr(start, length)` extracts a specific number of characters from a string.
    

And the central algorithmic insight: store enough information during encoding that decoding never has to guess.

That's the whole trick. The code looks complicated because of the indexing, but the underlying idea is remarkably simple.