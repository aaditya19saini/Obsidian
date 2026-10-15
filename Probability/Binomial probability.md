

The binomial distribution models the number of successes in a fixed number of repeated trials, when each trial has two possible outcomes and the chance of success stays the same.

## When to use a binomial model

A random variable $X$ has a binomial distribution when these conditions hold:

1. There is a fixed number of trials, $n$.
2. Each trial has two outcomes, usually called success and failure.
3. The probability of success, $p$, is the same on every trial.
4. The trials are independent.

The probability of failure on one trial is $1-p$. The notation is:

$$
X\sim\operatorname{Binomial}(n,p)
$$

Here, $X$ counts the number of successes, $n$ is the number of trials, and $p$ is the success probability on each trial.

## Probability of exactly $k$ successes

The probability of getting exactly $k$ successes in $n$ trials is:

$$
P(X=k)=\binom{n}{k}p^k(1-p)^{n-k},\qquad k=0,1,\ldots,n
$$

The binomial coefficient counts how many different ways the $k$ successes can be arranged among the $n$ trials:

$$
\binom{n}{k}=\frac{n!}{k!(n-k)!}
$$

The factor $p^k$ is the probability of the successes, and $(1-p)^{n-k}$ is the probability of the failures. Multiplying these gives the probability of one particular arrangement; multiplying by $\binom{n}{k}$ counts all arrangements.

## Example: exactly three heads

Flip a fair coin five times. Let $X$ be the number of heads. Then $n=5$, $p=0.5$, and the probability of exactly three heads is:

$$
P(X=3)=\binom{5}{3}(0.5)^3(0.5)^2
$$

$$
P(X=3)=10(0.5)^5=\frac{10}{32}=0.3125
$$

So there is a $31.25\%$ chance of getting exactly three heads.

## “At least,” “at most,” and ranges

The binomial formula gives the probability of an exact count. For a range of counts, add the probabilities for each allowed value:

$$
P(a\leq X\leq b)=\sum_{k=a}^{b}\binom{n}{k}p^k(1-p)^{n-k}
$$

For example:

- At most three successes: $P(X\leq 3)=P(X=0)+P(X=1)+P(X=2)+P(X=3)$.
- At least one success: it is often quickest to use the complement:

$$
P(X\geq 1)=1-P(X=0)=1-(1-p)^n
$$

Remember that “more than $k$” means $X>k$, while “at least $k$” means $X\geq k$.

## Mean and variance

For $X\sim\operatorname{Binomial}(n,p)$, the expected number of successes is:

$$
\mathbb{E}[X]=np
$$

The variance and standard deviation are:

$$
\operatorname{Var}(X)=np(1-p),\qquad \sigma=\sqrt{np(1-p)}
$$

For example, in 20 independent trials with success probability $0.3$, the expected number of successes is $20(0.3)=6$.

## How to solve a binomial problem

1. Define what counts as a success.
2. Identify $n$, $p$, and the requested count or range.
3. Check that the trials are independent and have the same success probability.
4. Use the exact-count formula, or add/complement probabilities for a range.
5. State the result in the context of the question.

## Common mistakes

- Using $n$ as the number of successes instead of the total number of trials.
- Forgetting the combination factor $\binom{n}{k}$, which counts possible arrangements.
- Using $p$ for failures; failure probability is $1-p$.
- Treating dependent trials or trials with changing probabilities as binomial.
- Confusing “at least” with “more than.”

## Connection to other distributions

Each individual trial can be modeled by a Bernoulli random variable. A binomial random variable is the sum of $n$ independent Bernoulli trials with the same success probability:

$$
X=X_1+X_2+\cdots+X_n
$$

When $n$ is large and $p$ is not too close to $0$ or $1$, a normal distribution may approximate the binomial distribution. When $n$ is large, $p$ is small, and $np$ remains moderate, a Poisson distribution may be useful as an approximation.
