The “zooming process” you’re seeing in Géron’s _Hands‑On Machine Learning_ refers to a **progressive refinement strategy for hyperparameter search**.

Here’s the idea in that section of the book:

- When tuning hyperparameters (like learning rate, number of hidden units, regularization strength), you often don’t know the right scale at first.
- Instead of starting with a very narrow grid, you begin with a **broad randomized search** across wide ranges (e.g., learning rate between (10^{-5}) and (10^{-1})).
- Once you identify promising regions, you “zoom in” by running another search with tighter bounds around those good values.
- This iterative narrowing is what Géron calls the **zooming process**: start wide → find promising zones → zoom in → refine further.

📌 **Example:**

1. First randomized search: learning rate sampled from reciprocal(0.0001, 0.1).
2. Best results cluster around 0.003–0.01.
3. Second search: restrict distribution to reciprocal(0.002, 0.02).
4. Possibly zoom in again if needed.

So “zooming” is not about image magnification—it’s about **progressively focusing your search space** for hyperparameters until you converge on optimal values.

![[Copilot_20260329_155235.png]]
