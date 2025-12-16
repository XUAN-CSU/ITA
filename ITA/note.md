# <span style="font-family: Times New Roman; color: red; font-size: 2em;">P15</span>
*Efficiency as a design criterion.*

# <span style="font-family: Times New Roman; color: red; font-size: 2em;">P18</span>
- divide-and-conquer
- dynamic programming
- greedy algorithms
- [amortized analysis](#amortized-analysis)
- augmenting data structures
- NP-completeness
- approximation algorithms

## amortized-analysis
* test 

# <span style="font-family: Times New Roman; color: red; font-size: 2em;">P29</span>

$$
\int_{-\infty}^{\infty} e^{-x^2} dx = \sqrt{\pi}
$$

## <font color='blue'>Prove</font>

$$
\lim_{n \to \infty} \frac{n!}{x^n} = 0
$$

## Proof That n! Grows Faster Than x^n (for Fixed x > 0)

**Statement**:  
For any fixed real $$x > 0$$,

$$
\lim_{n\to\infty} \frac{x^n}{n!} = 0 \quad \text{and} \quad \lim_{n\to\infty} \frac{n!}{x^n} = \infty.
$$

This means $$n! = \omega(x^n)$$ as $$n \to \infty$$.

---

### 1. Proof Using Ratio Test

Let 
$$
a_n = \frac{x^n}{n!}.
$$

Consider the ratio of successive terms:

$$
\frac{a_{n+1}}{a_n} = \frac{x^{n+1} / (n+1)!}{x^n / n!} = \frac{x}{n+1}.
$$

This ratio tends to 0 as $$n \to \infty$$.  

Choose $$N$$ such that $$N > 2x$$. Then for all $$n \ge N$$,

$$
\frac{a_{n+1}}{a_n} \le \frac{x}{N+1} < \frac12.
$$

Thus for $$n \ge N$$,

$$
a_{n+1} \le \frac12 a_n.
$$

Iterating:

$$
a_n \le a_N \cdot \left(\frac12\right)^{n-N} \quad \text{for } n \ge N.
$$

Since $$(1/2)^{n-N} \to 0$$ as $$n \to \infty$$, $$a_n \to 0$$.  
Hence:

$$
\boxed{\lim_{n\to\infty} \frac{x^n}{n!} = 0}.
$$

---

### 2. Proof Using Direct Comparison

Let $$m = \lceil 2x \rceil$$. For $$n > m$$,

$$
\frac{n!}{x^n} = \frac{m!}{x^m} \cdot \frac{(m+1)(m+2)\dots n}{x^{n-m}}.
$$

Every factor $$m+1, m+2, \dots, n$$ is $$\ge m+1 > 2x$$. Therefore:

$$
\frac{n!}{x^n} > \frac{m!}{x^m} \cdot \frac{(2x)(2x)\dots(2x)}{x^{n-m}} = \frac{m!}{x^m} \cdot 2^{n-m}.
$$

Since $$2^{n-m} \to \infty$$, we get $$\frac{n!}{x^n} \to \infty$$.

---

### 3. Proof Using Stirling’s Approximation

Stirling’s approximation:

$$
n! \sim \sqrt{2\pi n} \left( \frac{n}{e} \right)^n.
$$

Then:

$$
\frac{n!}{x^n} \sim \sqrt{2\pi n} \, \left( \frac{n}{e x} \right)^n.
$$

For large $n$, $n/(ex) > 1$. The term $\left( \frac{n}{e x} \right)^n$ grows **super-exponentially** (base grows with $n$), so $n! / x^n \to \infty$.

---

### 4. Intuition

- $n!$ is a product of $n$ integers growing linearly.
- $x^n$ is a product of $n$ copies of the constant $x$.
- Once $n > x$, each new factor in $n!$ is larger than the fixed factor $x$ in $x^n$, so $n!$ eventually outruns $x^n$ very quickly.

---

### 5. Formal Conclusion

For **any fixed $$x > 0$$**:

$$
\boxed{n! = \omega(x^n)}.
$$

Factorial grows strictly faster than exponential with constant base.

---

### Summary of Methods

| Method            | Key Idea |
|-------------------|----------|
| Ratio Test        | Show $$\frac{a_{n+1}}{a_n} \to 0$$ ⇒ $$a_n \to 0$$ |
| Direct Comparison | Compare tail product to powers of 2 |
| Stirling          | Asymptotic approximation shows super-exponential growth |

---
