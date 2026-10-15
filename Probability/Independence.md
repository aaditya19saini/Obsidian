# Independence

Two events are independent when knowing that one occurred does not change the probability of the other. Independence describes a relationship between events before conditioning on additional information.

## Definition for events

Events $A$ and $B$ are independent if:

$$
P(A\cap B)=P(A)P(B)
$$

When $P(B)>0$, this is equivalent to:

$$
P(A\mid B)=P(A)
$$

The same relationship then holds in the other direction: $P(B\mid A)=P(B)$, when $P(A)>0$.

If the product rule does not hold, the events are dependent. Observing one event gives information about the other.

## Example: two coin flips

Flip a fair coin twice. Let $A$ be “the first flip is heads” and $B$ be “the second flip is heads.” The flips are independent, so:

$$
P(A\cap B)=\frac14=\frac12\cdot\frac12=P(A)P(B)
$$

Knowing the first flip was heads does not change the chance that the second flip is heads.

## Independence of random variables

Random variables $X$ and $Y$ are independent if knowing the value of one does not change the probability distribution of the other. For discrete variables, this means:

$$
P(X=x,Y=y)=P(X=x)P(Y=y)
$$

for every possible pair of values $x$ and $y$. For continuous variables, the corresponding condition is that their joint density factors into the product of their marginal densities.

## Multiple events

For three events, pairwise independence alone does not guarantee that all three are jointly independent. Joint independence requires the product rule to hold for every subset of the events. For example, for $A$, $B$, and $C$, we need both pairwise factorizations and:

$$
P(A\cap B\cap C)=P(A)P(B)P(C)
$$

## Connection to conditional probability

Independence can be expressed using [[Conditional probability]]: conditioning on $B$ leaves the probability of $A$ unchanged. Conditioning on a third event can change whether two events appear independent; see [[Conditional independence]] and [[Independence and conditional independence]].

## Common mistake

Mutually exclusive events with positive probabilities are not independent. If $A$ and $B$ cannot occur together, then $P(A\cap B)=0$, while $P(A)P(B)>0$. Learning that one occurred tells us the other did not.
