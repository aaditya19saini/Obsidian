# Time Complexity

Time complexity describes how an algorithm's running time grows as the input size grows. It is an asymptotic measure: it focuses on growth, not the machine, language, or exact number of seconds.

## How to describe it

- State the input size, usually $n$ (for example, the number of elements in an array).
- State which case you are analyzing: worst case, average case, or best case. Worst case is common, but it is not the only kind of analysis.
- Use asymptotic notation to describe a bound. $O(f(n))$ is an upper bound, $\Omega(f(n))$ is a lower bound, and $\Theta(f(n))$ is a tight bound. Big O does not by itself mean worst case; the case and the bound are separate choices.
- For a simplified growth class, ignore constant factors and lower-order terms: $3n^2 + 5n + 2 = \Theta(n^2)$.

## Common growth rates

From slower to faster growth (for sufficiently large $n$):

| Complexity | Name | Example pattern |
|---|---|---|
| $O(1)$ | Constant | Access an array element by index |
| $O(\log n)$ | Logarithmic | Repeatedly halve the search range |
| $O(n)$ | Linear | Scan every element once |
| $O(n \log n)$ | Linearithmic | Typical efficient comparison sorting |
| $O(n^2)$ | Quadratic | Compare every pair, or two full nested loops |
| $O(n^3)$ | Cubic | Three full nested loops |
| $O(2^n)$ | Exponential | Try every subset of an $n$-element set |
| $O(n!)$ | Factorial | Try every ordering of $n$ items |

## Estimating from code

- A fixed number of basic operations is $O(1)$.
- A loop that visits $n$ items is $O(n)$, assuming each iteration does constant work.
- Sequential sections add: $O(n) + O(n^2) = O(n^2)$.
- Independent nested loops multiply: two loops that each run $n$ times do $O(n^2)$ work.
- If a loop halves or doubles its remaining range each iteration, it usually runs $O(\log n)$ times.
- For branching or recursive algorithms, count the work across calls; write a recurrence when that makes the structure clearer.

These are rules of thumb. Check loop bounds, early exits, input characteristics, and the cost of operations used inside the algorithm. For example, a hash table lookup is often $O(1)$ on average but can be $O(n)$ in the worst case.

## Time and space

Time complexity measures operations as input grows. Space complexity measures memory as input grows. Auxiliary space counts extra memory used by the algorithm; total space may also include the input, depending on the convention being used. State which measure you report.
