# Independence and Conditional Independence

Independence asks whether two events or variables are unrelated in the full probability model. Conditional independence asks whether they are unrelated after a third piece of information is known. Neither property generally implies the other.

For events, independence means:

$$
P(A\cap B)=P(A)P(B)
$$

Conditional independence of $A$ and $B$ given $C$ means:

$$
P(A\cap B\mid C)=P(A\mid C)P(B\mid C)
$$

## Conditional independence does not imply independence

Imagine a fair coin determines whether it rains, and two people independently decide whether to carry umbrellas given the weather. Their umbrella choices can be independent within each weather condition, but associated overall: seeing one person with an umbrella makes rain more plausible, which makes the other person more likely to have one too.

In general, even if $X\perp Y\mid Z$, averaging across values of $Z$ can produce dependence between $X$ and $Y$. The shared variable $Z$ can influence both.

## Independence does not imply conditional independence

Let $X$ and $Y$ be independent fair bits, each taking values $0$ and $1$. Define $Z$ to be their exclusive OR:

$$
Z=X\mathbin{\mathrm{XOR}}Y
$$

Because $X$ and $Y$ are chosen independently, they are independent before observing $Z$. But if we learn that $Z=0$, then $X=Y$. Knowing $X$ now determines $Y$, so they are dependent given $Z=0$.

For example:

$$
P(X=1\mid Z=0)=\frac12,\qquad
P(Y=1\mid Z=0)=\frac12
$$

but

$$
P(X=1,Y=1\mid Z=0)=\frac12\neq\frac14
$$

Thus $X$ and $Y$ are independent, but not conditionally independent given $Z$.

## Summary of implications

| Relationship | Generally true? |
|---|---|
| $X\perp Y\;\vert\;Z$ implies $X\perp Y$ | No |
| $X\perp Y$ implies $X\perp Y\;\vert\;Z$ | No |

The two properties can coincide under extra assumptions, but neither implication holds in general. Always state what information is being conditioned on.

## Related notes

- [[Independence]] defines independence without conditioning.
- [[Conditional independence]] defines independence after conditioning on a variable or event.
- [[Conditional probability]] introduces the probability rules used in both definitions.
