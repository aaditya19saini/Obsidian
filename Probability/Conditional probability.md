# Conditional Probability

Conditional probability measures the chance of an event when we know that another event has occurred. Knowing the condition can change the set of outcomes we consider, and therefore change the probability.

## Definition

For events $A$ and $B$, the probability of $A$ given that $B$ has occurred is:

$$
P(A\mid B)=\frac{P(A\cap B)}{P(B)},\qquad P(B)>0
$$

Here:

- $P(A\mid B)$ means “the probability of $A$ given $B$.”
- $A\cap B$ means that both $A$ and $B$ occur.
- $P(B)$ is the probability of the condition event.

The condition $B$ becomes the new reference group: among outcomes where $B$ occurred, we ask what fraction also have $A$.

## Example: drawing a card

Draw one card from a standard 52-card deck. Let $A$ be the event “the card is a king” and $B$ be “the card is a face card.” There are 12 face cards, and 4 of them are kings, so:

$$
P(A\mid B)=\frac{4}{12}=\frac{1}{3}
$$

Once we know the card is a face card, we only consider those 12 cards.

## Multiplication rule

Rearranging the definition gives the multiplication rule:

$$
P(A\cap B)=P(A\mid B)P(B)
$$

The events can also be considered in the opposite order:

$$
P(A\cap B)=P(B\mid A)P(A)
$$

These rules are useful for finding the probability that several events all occur.

## Independence

Events $A$ and $B$ are [[Independence|independent]] when knowing that one occurred does not change the probability of the other:

$$
P(A\mid B)=P(A)
$$

For events with positive probabilities, equivalent tests are:

$$
P(B\mid A)=P(B)
$$

and

$$
P(A\cap B)=P(A)P(B)
$$

Conditional independence is a related but distinct idea: two events can be independent given a third event and dependent overall, or independent overall but dependent after conditioning. See [[Conditional independence]] and [[Independence and conditional independence]].

For independent repeated trials, the probability of success stays the same after earlier outcomes are known. This is one of the assumptions behind the [[Binomial probability]] model.

## Law of total probability

Suppose events $B_1, B_2,\ldots,B_m$ divide all possible outcomes into non-overlapping cases. Then the probability of $A$ can be calculated by adding its probabilities across those cases:

$$
P(A)=\sum_{i=1}^{m}P(A\mid B_i)P(B_i)
$$

For two cases, $B$ and its complement $B^c$:

$$
P(A)=P(A\mid B)P(B)+P(A\mid B^c)P(B^c)
$$

## Bayes’ theorem

Bayes’ theorem reverses a conditional probability. It lets us find the probability of a possible cause $B$ after observing evidence $A$:

$$
P(B\mid A)=\frac{P(A\mid B)P(B)}{P(A)},\qquad P(A)>0
$$

Using the law of total probability to expand the denominator gives:

$$
P(B\mid A)=\frac{P(A\mid B)P(B)}{P(A\mid B)P(B)+P(A\mid B^c)P(B^c)}
$$

### Example: a medical test

Suppose a condition affects $1\%$ of people. A test is positive for $99\%$ of people who have the condition, and falsely positive for $5\%$ of people who do not have it. Let $D$ mean “has the condition” and $+$ mean “tests positive.” Then:

$$
P(D\mid +)=\frac{P(+\mid D)P(D)}{P(+\mid D)P(D)+P(+\mid D^c)P(D^c)}
$$

$$
P(D\mid +)=\frac{0.99(0.01)}{0.99(0.01)+0.05(0.99)}\approx 0.167
$$

So a positive result corresponds to about a $16.7\%$ chance of having the condition under these assumptions. The low base rate matters: most people tested do not have the condition, so false positives make up a substantial share of all positive results.

## Common mistakes

- Reversing the condition: $P(A\mid B)$ is generally different from $P(B\mid A)$.
- Treating events as independent without checking whether the condition changes the probability.
- Forgetting to restrict the reference group to outcomes where the condition occurred.
- Confusing “and” ($A\cap B$) with “given” ($A\mid B$).

## Quick summary

$$
P(A\mid B)=\frac{P(A\cap B)}{P(B)},\qquad
P(A\cap B)=P(A\mid B)P(B)
$$

Conditional probability updates a probability using known information. Independence is the special case where the information does not change the probability.
