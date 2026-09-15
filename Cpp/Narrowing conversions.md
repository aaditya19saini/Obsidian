[[Initialization]]
A **narrowing conversion** happens when a value of one data type is converted to another type that cannot guarantee storing all possible values without **data loss** or **loss of precision**.

---

## 1. When Narrowing Occurs

| From Type | To Type | What Gets Lost / Problem | Example |
| :--- | :--- | :--- | :--- |
| **Floating-point** | **Integer** | Fractional part is completely dropped (truncated) | `double` $\to$ `int` (`3.99` becomes `3`) |
| **Larger Float** | **Smaller Float** | Precision is lost (if value exceeds target range/precision) | `double` $\to$ `float` |
| **Larger Integer** | **Smaller Integer** | Value truncated if too large to fit in smaller bit size | `long long` $\to$ `int`, `int` $\to$ `short` / `char` |
| **Signed Integer** | **Unsigned Integer** | Negative numbers wrap around to massive positive numbers | `int` (`-1`) $\to$ `unsigned int` (`4294967295`) |

---

## 2. Silent Narrowing (Old/Traditional C++)

Traditional initialization (`=` or `()`) performs narrowing conversions **silently** without generating compiler errors.

```cpp
// 1. Floating-point to integer (Fraction dropped)
int a = 5.95;       // Silently truncates to 5

// 2. Large integer to smaller integer (Overflow/Truncation)
char b = 300;       // Exceeds 1-byte char limit (-128 to 127); overflows/wraps

// 3. Signed to unsigned (Wrap-around bug)
unsigned int c = -5; // Wraps to 4294967291