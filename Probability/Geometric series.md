# Geometric Series

## 1. Definition

A geometric series is the sum of the terms of a geometric sequence, where each term is obtained by multiplying the previous term by a constant called the common ratio $r$.

For example:

$$
 2+6+18+54+162+\cdots 
$$

Here, each term is multiplied by $3$, so the common ratio is $r=3$.

The general form of a geometric series is:

$$
 a+ar+ar^2+ar^3+\cdots 
$$

where:

- $a$ = first term
    
- $r$ = common ratio
    
- $n$ = number of terms
    

## 2. Sum of a Finite Geometric Series

The sum of the first $n$ terms is:

$$
 \boxed{S_n=\frac{a(1-r^n)}{1-r}}, \qquad r\neq 1 
$$

An equivalent form is:

$$
 S_n=\frac{a(r^n-1)}{r-1} 
$$

### Example

Find the sum:

$$
 2+6+18+54+162 
$$

Here, $a=2$, $r=3$, and $n=5$.

Using the formula:

$$
 S_5=\frac{2(1-3^5)}{1-3} 
$$

$$
 =\frac{2(1-243)}{-2} 
$$

$$
 \boxed{S_5=242} 
$$

If $r=1$, every term equals $a$, so $S_n=na$.

## 3. Sum of an Infinite Geometric Series

An infinite geometric series has infinitely many terms:

$$
 a+ar+ar^2+ar^3+\cdots 
$$

Its sum is finite only when the common ratio satisfies:

$$
 \boxed{|r|<1} 
$$

In that case:

$$
 \boxed{S_\infty=\frac{a}{1-r}} 
$$

### Example

Find the sum:

$$
 1+\frac12+\frac14+\frac18+\cdots 
$$

Here, $a=1$ and $r=\frac12$.

Since $\left|\frac12\right|<1$, the series converges.

$$
 S_\infty=\frac{1}{1-\frac12} 
$$

$$
 \boxed{S_\infty=2} 
$$

Although there are infinitely many terms, their sum approaches $2$.

## 4. Convergence and Divergence

The behavior of an infinite geometric series depends on its common ratio.

|Common ratio|Behavior|Example|
|---|---|---|
|$\lvert r\rvert<1$|Converges to a finite sum|$1+\frac12+\frac14+\cdots$|
|$r=1$|Diverges, unless all terms are zero|$1+1+1+\cdots$|
|$r>1$|Diverges for $a\neq0$|$1+2+4+8+\cdots$|
|$r\leq -1$|Diverges for $a\neq0$|$1-1+1-1+\cdots$|

Important: For $r=-1$, the partial sums oscillate rather than approaching a single value.

## 5. Derivation of the Infinite Sum Formula

Start with:

$$
 S=a+ar+ar^2+ar^3+\cdots 
$$

Multiply both sides by $r$:

$$
 rS=ar+ar^2+ar^3+\cdots 
$$

Subtract the second equation from the first:

$$
 S-rS=a 
$$

Factor out $S$:

$$
 S(1-r)=a 
$$

Therefore:

$$
 S=\frac{a}{1-r} 
$$

This derivation is valid for the infinite sum when $|r|<1$, so that the terms tend to zero and the series converges.

## 6. Connection to Taylor Series

Geometric series are particularly useful in calculus because they provide expansions for functions.

For $|x|<1$:

$$
 \boxed{\frac{1}{1-x}=1+x+x^2+x^3+\cdots} 
$$

This follows directly from the infinite geometric series formula by taking $a=1$ and $r=x$.

For example, replacing $x$ with $-x$ gives:

$$
 \boxed{\frac{1}{1+x}=1-x+x^2-x^3+\cdots} 
$$

This is a Maclaurin series, which is a special type of Taylor series.

## Key Takeaways

- A geometric series has a constant ratio between consecutive terms.
    
- Finite sum: $\displaystyle S_n=\frac{a(1-r^n)}{1-r}$.
    
- Infinite sum: $\displaystyle S_\infty=\frac{a}{1-r}$, provided $|r|<1$.
    
- Geometric series are fundamental to understanding Taylor series, power series, and convergence in calculus.