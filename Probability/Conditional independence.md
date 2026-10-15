# Conditional Independence

Two events or random variables are conditionally independent when they become independent after we know the value of a third event or variable. The conditioning information can remove an association, or reveal one that was hidden in the unconditioned data.

## Definition for events

Events $A$ and $B$ are conditionally independent given an event $C$ (with $P(C)>0$) when:

$$
P(A\cap B\mid C)=P(A\mid C)P(B\mid C)
$$

Equivalently, when the relevant conditional probabilities are defined:

$$
P(A\mid B\cap C)=P(A\mid C)
$$

Knowing that $B$ occurred gives no additional information about $A$ once we already know $C$.

## Definition for random variables

Random variables $X$ and $Y$ are conditionally independent given $Z$ if, for each value $z$ with positive probability, their conditional joint distribution factors:

$$
P(X=x,Y=y\mid Z=z)=P(X=x\mid Z=z)P(Y=y\mid Z=z)
$$

This is commonly written:

$$
X\perp Y\mid Z
$$

For continuous variables, use conditional densities in place of probabilities.

## Example: outcomes given the weather

Suppose $Z$ is the weather, and $X$ and $Y$ indicate whether two people bring umbrellas. Given the weather, assume their choices are independent: knowing one brought an umbrella does not tell us whether the other did, once the weather is known.

Without knowing the weather, the choices can be associated. If it is raining, both are more likely to bring umbrellas; if it is sunny, both are less likely. The shared weather creates an association in the combined data even though the choices are independent within each weather condition.

## Conditional independence is not ordinary independence

Conditional independence does not generally mean that $X$ and $Y$ are independent without conditioning. A shared cause can make them associated overall even when they are independent within each value of that cause.

Conversely, ordinary independence does not guarantee conditional independence. Conditioning on a third variable can create a relationship between variables that were independent before conditioning.

These two distinctions are worked through in [[Independence and conditional independence]]. For ordinary independence, see [[Independence]].

## Where it is useful

- **Probability and statistics:** simplifying joint distributions and calculations.
- **Bayesian networks:** expressing which variables become independent after other variables are known.
- **Causal reasoning:** separating an association caused by shared background information from a direct relationship.
- **Repeated trials:** independent trials stay independent when conditioned on information that does not affect their outcomes; see [[Binomial probability]].

## Notation reminder

$$
X\perp Y \quad\text{means independence},\qquad
X\perp Y\mid Z \quad\text{means conditional independence given }Z
$$
