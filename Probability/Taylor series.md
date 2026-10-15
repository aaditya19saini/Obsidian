

## 1. What is a Taylor series?

A Taylor series represents a complicated function as an infinite sum of simpler polynomial terms.

Suppose you have a function like \(e^x\), \(\sin x\), or \(\ln(1+x)\). Instead of working with the original function directly, you can approximate it using powers of \(x\).

The general formula is:

\[ \boxed{f(x)=\sum_{n=0}^{\infty} \frac{f^{(n)}(a)}{n!}(x-a)^n} \]

Here is what each symbol means:

- \(f(x)\): the original function.
    
- \(a\): the point around which you expand the function.
    
- \(f^{(n)}(a)\): the \(n\)-th derivative evaluated at \(a\).
    
- \(n!\): factorial of \(n\).
    
- \((x-a)^n\): powers of the distance from the expansion point.
    

You use the function's derivatives to construct a polynomial that matches its behavior near \(a\).

## 2. Example: Taylor series of \(e^x\)

The exponential function is particularly convenient because every derivative of \(e^x\) is \(e^x\).

At \(x=0\), every derivative equals \(1\). Substituting into the formula gives:

Let's approximate \(e^{0.1}\) using just the first four terms:

\[ e^{0.1}\approx 1+0.1+\frac{0.1^2}{2} +\frac{0.1^3}{6} \]

\[ e^{0.1}\approx 1.10517 \]

The actual value is approximately \(1.10517\). Even a low-degree polynomial gives an excellent approximation here.

That's the power of Taylor series.

## 3. How do you derive one?

Let's take a simple function:

\[ f(x)=\sin x \]

We expand around \(a=0\), which is called a Maclaurin series.

|Derivative|Value at \(x=0\)|
|---|---|
|\(f(x)=\sin x\)|\(0\)|
|\(f'(x)=\cos x\)|\(1\)|
|\(f''(x)=-\sin x\)|\(0\)|
|\(f'''(x)=-\cos x\)|\(-1\)|
|\(f^{(4)}(x)=\sin x\)|\(0\)|

Insert these values into the formula:

\[ \boxed{\sin x=x-\frac{x^3}{3!} +\frac{x^5}{5!}-\cdots} \]

Notice that only odd powers appear because the even-order derivatives evaluate to zero at the origin.

## 4. Taylor series vs. Maclaurin series

Taylor series

Expands a function around any suitable point \(a\).

\[ f(x)=f(a)+f'(a)(x-a)+\cdots \]

Maclaurin series

A special case of the Taylor series where \(a=0\).

\[ f(x)=f(0)+f'(0)x+\cdots \]

## 5. Why should you care?

Taylor series has practical applications across several fields:

- Calculus: understanding local function behavior and estimating limits.
    
- Numerical analysis: approximating functions when exact calculations are expensive.
    
- Machine learning: understanding local approximations, optimization, and gradient-based methods.
    
- Physics and engineering: simplifying complicated equations near equilibrium points.
    
- Statistics: deriving approximations for likelihoods, distributions, and estimators.
    

For example, in optimization, a second-order Taylor approximation is:

\[ f(x+\Delta x)\approx f(x)+f'(x)\Delta x +\frac{f''(x)}{2}(\Delta x)^2 \]

The first derivative describes the local slope, while the second derivative captures curvature. This is closely related to Newton's optimization method.

## 6. The most important intuition

Think of Taylor series as building a function in layers:

- Constant term: matches the function's value at the expansion point.
    
- Linear term: matches its slope.
    
- Quadratic term: matches its curvature.
    
- Cubic and higher terms: capture increasingly subtle local behavior.
    

One important caveat: an infinite Taylor series does not necessarily converge to the original function everywhere. You must consider its interval or region of convergence.

My recommendation: Learn Taylor series in this order: derivatives and factorials, Maclaurin expansions of \(e^x\), \(\sin x\), and \(\cos x\), then general Taylor expansions and the remainder/error term. Once those click, the topic becomes much easier.
