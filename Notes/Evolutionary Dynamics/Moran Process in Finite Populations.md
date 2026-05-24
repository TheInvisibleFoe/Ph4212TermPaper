---
title: title
date:
tags:
  - 
---
> Small Note here:
> This derivation is largely unnecessary and contains a lot of unnecessary steps. **However Sir has done the whole derivation in class sooooo.**

# Derivation: Fixation Probability in the Weak Selection Limit

This derivation outlines the Taylor expansion of the fixation probability ($\rho_A$) in the weak selection limit ($w \ll 1$), which serves as the mathematical foundation for the $1/3$ Law.

## Step 1: The General Fixation Probability Formula

In the Moran process, let $i$ be the number of individuals playing strategy $A$. The state space is $i \in \{0, 1, \dots, N\}$. 
At any state $i$, the probability of increasing the number of $A$ individuals by one is $P_{i, i+1}$, and the probability of decreasing by one is $P_{i, i-1}$.

From standard Markov chain theory for birth-death processes, the probability $\rho_A$ that a single mutant ($i=1$) eventually reaches fixation ($i=N$) is given by:

$$\rho_A = \frac{1}{1 + \sum_{k=1}^{N-1} \prod_{i=1}^k \gamma_i}$$

where $\gamma_i$ is the ratio of the "death" probability to the "birth" probability of strategy $A$:

$$\gamma_i = \frac{P_{i, i-1}}{P_{i, i+1}} = \frac{g_i}{f_i}$$

*(Note: $f_i$ is the fitness of $A$ and $g_i$ is the fitness of $B$ when there are $i$ individuals of type $A$.)*

## Step 2: Defining Fitness with Selection Intensity

Fitness is defined as a convex combination of a baseline survival rate ($1$) and the expected payoff from the game ($F_i$ or $G_i$), modulated by the selection intensity $w$:

* $f_i = 1 - w + w F_i$
* $g_i = 1 - w + w G_i$

Substituting these into our ratio $\gamma_i$ yields:

$$\gamma_i = \frac{1 - w + w G_i}{1 - w + w F_i}$$

## Step 3: Taylor Expansion of $\gamma_i$ (Weak Selection, $w \ll 1$)

Assuming weak selection ($w \to 0$), we use the Taylor expansion $(1+x)^{-1} \approx 1 - x$ for small $x$. 

First, rewrite the denominator:

$$\frac{1}{1 - w(1 - F_i)} \approx 1 + w(1 - F_i)$$

Multiply this by the numerator:

$$\gamma_i \approx (1 - w + w G_i)(1 + w - w F_i)$$

Expanding and ignoring terms of $O(w^2)$ and higher:

$$\gamma_i \approx 1 + w - w F_i - w + w G_i$$

$$\gamma_i \approx 1 - w(F_i - G_i)$$

## Step 4: Expanding the Product and Sum

Substitute this linearized $\gamma_i$ into the product $\prod_{i=1}^k \gamma_i$. 
For small $\epsilon$, the product $(1 - \epsilon_1)(1 - \epsilon_2) \dots \approx 1 - (\epsilon_1 + \epsilon_2 + \dots)$. Therefore:

$$\prod_{i=1}^k \gamma_i \approx \prod_{i=1}^k \left[1 - w(F_i - G_i)\right] \approx 1 - w \sum_{i=1}^k (F_i - G_i)$$

Next, evaluate the summation in the denominator of the main formula:

$$\sum_{k=1}^{N-1} \prod_{i=1}^k \gamma_i \approx \sum_{k=1}^{N-1} \left[ 1 - w \sum_{i=1}^k (F_i - G_i) \right]$$

Split this into two parts:

$$= \sum_{k=1}^{N-1} 1 - w \sum_{k=1}^{N-1} \sum_{i=1}^k (F_i - G_i)$$

$$= (N - 1) - w \sum_{k=1}^{N-1} \sum_{i=1}^k (F_i - G_i)$$

## Step 5: Final Expansion of $\rho_A$

Substitute this back into the denominator of the original $\rho_A$ formula:

$$\rho_A \approx \frac{1}{1 + (N - 1) - w \sum_{k=1}^{N-1} \sum_{i=1}^k (F_i - G_i)}$$

$$\rho_A \approx \frac{1}{N - w \sum_{k=1}^{N-1} \sum_{i=1}^k (F_i - G_i)}$$

Factor out $N$ from the denominator to prepare for another Taylor expansion:

$$\rho_A \approx \frac{1}{N \left[ 1 - \frac{w}{N} \sum_{k=1}^{N-1} \sum_{i=1}^k (F_i - G_i) \right]}$$

Using $(1-x)^{-1} \approx 1+x$ one last time on the bracketed term in the denominator:

$$\rho_A \approx \frac{1}{N} \left[ 1 + \frac{w}{N} \sum_{k=1}^{N-1} \sum_{i=1}^k (F_i - G_i) \right]$$

---

## Final Conclusion

Expanding the bracket gives the final approximated form:

$$\begin{equation}
	\rho_A \approx \frac{1}{N} + \frac{w}{N^2} \sum_{k=1}^{N-1} \sum_{i=1}^k (F_i - G_i)
	\label{lol}
\end{equation}
$$

**Physical Interpretation:**
* **The first term ($1/N$):** The probability of fixation under purely neutral drift ($w=0$).
* **The second term:** The first-order correction due to natural selection. If the double sum of $(F_i - G_i)$ is positive, then $\rho_A > 1/N$, meaning selection *favors* the mutant $A$ taking over the population.
# Derivation: The 1/3 Law in Terms of Payoff Matrix $(a, b, c, d)$

We start from the Taylor expansion of the fixation probability under weak selection:

$$\rho_A \approx \frac{1}{N} + \frac{w}{N^2} \sum_{k=1}^{N-1} \sum_{i=1}^k (F_i - G_i)$$

For selection to favour the invasion of mutant $A$, we require $\rho_A > 1/N$. **What this means is that if $\rho< \frac{1}{N}$ , then selection shall hinder the invasion.** The extra factor arrives due to the interactions between the species and the games played between them. The interactions change the fitness over time resulting in either hindrance or favouring of the invasion. *This means the double sum must be strictly positive*:

$$\sum_{k=1}^{N-1} \sum_{i=1}^k (F_i - G_i) > 0$$

## Step 1: Define Expected Payoffs in a Finite Population
Let the payoff matrix be:
$$\begin{pmatrix} a & b \\ c & d \end{pmatrix}$$

In a population of size $N$ with $i$ individuals of type $A$, an individual of type $A$ interacts with $i-1$ other $A$'s and $N-i$ $B$'s. An individual of type $B$ interacts with $i$ $A$'s and $N-i-1$ $B$'s. The total number of interactions for anyone is $N-1$.

The expected payoffs are:
$$F_i = \frac{a(i-1) + b(N-i)}{N-1}$$
$$G_i = \frac{ci + d(N-i-1)}{N-1}$$

## Step 2: Calculate the Payoff Difference $(F_i - G_i)$
Subtract $G_i$ from $F_i$ and group the terms by $i$:

$$F_i - G_i = \frac{a(i-1) + b(N-i) - ci - d(N-i-1)}{N-1}$$

$$F_i - G_i = \frac{i(a - b - c + d) - a + bN - dN + d}{N-1}$$

To make the math cleaner, let's define two constants (independent of $i$ and $k$):
* $u = a - b - c + d$
* $v = -a + bN - dN + d$

So we can rewrite the difference as:
$$F_i - G_i = \frac{1}{N-1} (u \cdot i + v)$$

## Step 3: Evaluate the Inner Sum ($\sum_{i=1}^k$)
Now we sum this difference from $i = 1$ to $k$:

$$\sum_{i=1}^k (F_i - G_i) = \frac{1}{N-1} \sum_{i=1}^k (u \cdot i + v)$$

Using the standard formula $\sum_{i=1}^k i = \frac{k(k+1)}{2}$:

$$\sum_{i=1}^k (F_i - G_i) = \frac{1}{N-1} \left[ \frac{u}{2}k(k+1) + vk \right]$$

## Step 4: Evaluate the Outer Sum ($\sum_{k=1}^{N-1}$)
Now we plug the result of the inner sum into the outer sum:

$$\sum_{k=1}^{N-1} \frac{1}{N-1} \left[ \frac{u}{2}k(k+1) + vk \right]$$

We need two standard summation identities for this step:
1. $\sum_{k=1}^{N-1} k = \frac{(N-1)N}{2}$
2. $\sum_{k=1}^{N-1} k(k+1) = \frac{(N-1)N(N+1)}{3}$

Substituting these identities in:

$$= \frac{1}{N-1} \left[ \frac{u}{2} \frac{(N-1)N(N+1)}{3} + v \frac{(N-1)N}{2} \right]$$

Notice that $(N-1)$ nicely cancels out from all terms!

$$= \frac{u \cdot N(N+1)}{6} + \frac{v \cdot N}{2}$$

Factor out $\frac{N}{6}$:

$$= \frac{N}{6} \left[ u(N+1) + 3v \right]$$

## Step 5: Substitute $u$ and $v$ Back
Now we substitute our original payoff variables back into the bracketed term $\left[ u(N+1) + 3v \right]$:

$$u(N+1) = (a - b - c + d)(N+1) = aN + a - bN - b - cN - c + dN + d$$
$$3v = 3(-a + bN - dN + d) = -3a + 3bN - 3dN + 3d$$

Add them together:
$$u(N+1) + 3v = (a - b - c + d + 3b - 3d)N + (a - b - c + d - 3a + 3d)$$

Group the $N$ terms and the constant terms:
$$u(N+1) + 3v = N(a + 2b - c - 2d) + (-2a - b - c + 4d)$$

Thus the final double sum evaluates as the above. Substituting it into the Taylor series of the invasion prob, we get,

$$
	\rho_{A} \approx \frac{1}{N} + \frac{w}{6N}[N(a+2b-c-2d)-(2a+b+c-4d)]
$$
## Step 6: The Final Condition
Remember, for selection to favor the mutant $A$, this entire expression must be strictly greater than zero:

$$N(a + 2b - c - 2d) + (-2a - b - c + 4d) > 0$$

This is the exact, rigorous condition for any finite population size $N$. We can map this a PD game. In that, we find a critical population size $N_{c}$ , only above which selection favours cooperators,
$$
	N > N_{c} =  \frac{2a + b + c - 4d}{a + 2b - c - 2d}
$$



However, evolutionary game theory usually considers the limit of a **large population** ($N \gg 1$). In this limit, the term multiplied by $N$ completely dominates the constant term. Therefore, the condition simplifies to:

$$a + 2b - c - 2d > 0$$

$$\implies a + 2b > c + 2d$$

### Connection to the "1/3 Law"
In the deterministic replicator equation, the internal equilibrium point $x^*$ (the frequency of strategy $A$) is given by:
$$x^* = \frac{d - b}{a - b - c + d}$$

If you solve the inequality $x^* < \frac{1}{3}$, you get exactly:
$$a + 2b > c + 2d$$

Therefore, a single mutant $A$ is favored to take over a finite population of $B$ if and only if the deterministic equilibrium frequency of $A$ is less than $1/3$. **This means that the basin of attraction of B is less than one-third**.

# TFT can invade ALLD

One important consequence of finite populations is the fact that TFT can invade ALLD in a  finite population(*in the weak selection limit*). The TFT ALLD matrix is given by,
$$
	M = \begin{bmatrix}
m a & b + (m-1)d \\
c+(m-1)d & md
\end{bmatrix}
$$
Just substitute these values into into the place holders $a,b,c,d$. As a result one can find for fixed $N$, the critical value of $m$ over which selection favours cooperators, $\rho_{TFT}>1/N$ implies,
$$
	m > \frac{-b(2N-1)+c(N+1)+d(N-2)}{(N-2)(a-d)}
$$
In the large population limit $N\gg 1$, we obtain the inequality,
$$
	m> \frac{c+d-2b}{a-d}
$$
For a fixed $m$, there is a critical value of $N=N_{c}$, above which in the weak selection limit TFT can invade ALLD,
$$
	N > \frac{2ma+b+c-2d(m+1)}{ma+2b+c-d(m+1)}
$$

