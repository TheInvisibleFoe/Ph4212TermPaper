# The Fermi Update Rule in Evolutionary Game Theory

In the context of evolutionary game theory and finite populations, the **Fermi update rule** (or Fermi-Dirac imitation rule) is a widely used mechanism to model how individuals change their strategies over time. 

Unlike the Moran or Wright-Fisher models, which typically represent genetic reproduction (birth and death), the Fermi update is used to model **social learning, cultural evolution, or imitation**, where individuals consciously or subconsciously copy the strategies of others based on their relative success.

## 1. The Mechanism of the Fermi Update

The Fermi update relies on a **pairwise comparison process**. At each time step in a finite population:
1. An individual $x$ is chosen at random to reconsider their strategy.
2. They randomly choose a neighbor (or another random individual in a well-mixed population), $y$, to compare themselves against.
3. Individual $x$ adopts the strategy of individual $y$ with a probability $P(x \to y)$ determined by the difference in their expected payoffs (fitness).

The probability of switching is given by the Fermi distribution function:

$$P(x \to y) = \frac{1}{1 + \exp[-\beta (\Pi_y - \Pi_x)]}$$

Where:
* $\Pi_x$ is the payoff (fitness) of individual $x$.
* $\Pi_y$ is the payoff of individual $y$.
* **$\beta$** is a crucial parameter representing the **intensity of selection**.



## 2. The Significance of $\beta$ (Intensity of Selection)

The brilliance of the Fermi update lies in the parameter $\beta$. Borrowed from the Fermi-Dirac distribution in statistical physics (where it represents inverse temperature, $1/kT$), in evolutionary dynamics, $\beta$ acts as a "rationality" or "selection strength" dial:

* **Weak Selection / High Noise ($\beta \to 0$):**
  If $\beta = 0$, the exponent becomes $0$, and the probability $P(x \to y) = 1 / (1 + 1) = 0.5$. This means individual $x$ flips a coin to decide whether to copy $y$, regardless of their payoffs. This represents **neutral drift**, where strategy adoption is completely random.
  
* **Strong Selection / Perfect Rationality ($\beta \to \infty$):**
  If $\beta$ is very large, the function approaches a step function. If $\Pi_y > \Pi_x$, the probability approaches $1$ (individual $x$ definitely copies $y$). If $\Pi_y < \Pi_x$, the probability approaches $0$ ($x$ absolutely refuses to copy a worse strategy).
  
* **Intermediate Selection (Finite $\beta$):**
  For normal values of $\beta$, individuals *usually* copy those who are doing better than them. However, if $\Pi_y < \Pi_x$, there is still a small, non-zero probability that $x$ will copy $y$.

## 3. Why is the Fermi Update so Significant?

### A. It Models "Bounded Rationality" and Noise
In the real world, biological organisms and human agents are not perfectly rational calculating machines. We make mistakes, experiment, act on incomplete information, and sometimes imitate a neighbor who is actually doing worse than us (perhaps falsely attributing their success to their strategy). The Fermi function mathematically captures this "bounded rationality" by allowing irrational moves with a probability that shrinks as the payoff deficit grows.

### B. It Bridges Physics and Biology
Because the update rule is derived directly from statistical mechanics, it allows physicists and mathematicians to apply powerful, pre-existing tools from statistical physics to biological and economic systems. This cross-pollination has driven massive advancements in evolutionary game theory over the last two decades.

### C. It is the Standard for Evolutionary Graph Theory
When studying spatial games (where individuals are arranged on complex networks or lattices instead of well-mixed pools), the Fermi rule is the gold standard. It cleanly handles negative payoffs—unlike fitness-proportional rules which require baseline adjustments to avoid negative probabilities—making it ideal for games with strict penalties, like the Snowdrift or Public Goods games on networks.

### D. Tractability in the Weak Selection Limit
Just as with the Moran process, expanding the Fermi function in the limit of weak selection ($\beta \ll 1$) yields a highly tractable linear approximation:

$$P(x \to y) \approx \frac{1}{2} + \frac{\beta}{4}(\Pi_y - \Pi_x)$$

This linearization makes the exact analytical calculation of fixation probabilities on complex networks possible, leading to foundational theorems in evolutionary graph theory (such as the Isothermal Theorem).

# Derivation: Fixation Probability under the Fermi Update Rule

In a finite population of size $N$, let the state of the system $i$ be the number of individuals playing the mutant strategy $A$, and $N-i$ be the number of individuals playing the resident strategy $B$. 

We want to find the probability $\rho_A$ that a single mutant ($i=1$) eventually takes over the entire population ($i=N$).

## Step 1: Define the Transition Probabilities
Under the Fermi pairwise comparison process, at each time step, one individual is chosen at random to update their strategy, and another is chosen at random as a role model. 

The probability of increasing the number of $A$ players by one ($P_{i, i+1}$) requires three things to happen simultaneously:
1. A $B$ player is chosen to update (probability $\frac{N-i}{N}$).
2. An $A$ player is chosen as the role model (probability $\frac{i}{N}$).
3. The $B$ player successfully copies the $A$ player using the Fermi function.

$$P_{i, i+1} = \left( \frac{N-i}{N} \right) \left( \frac{i}{N} \right) \frac{1}{1 + \exp[-\beta (\Pi_A(i) - \Pi_B(i))]}$$

Similarly, the probability of decreasing the number of $A$ players by one ($P_{i, i-1}$) requires an $A$ player to be chosen, a $B$ player to act as the role model, and the $A$ player to copy the $B$ player:

$$P_{i, i-1} = \left( \frac{i}{N} \right) \left( \frac{N-i}{N} \right) \frac{1}{1 + \exp[-\beta (\Pi_B(i) - \Pi_A(i))]}$$

*(Note: $\Pi_A(i)$ and $\Pi_B(i)$ are the expected payoffs for $A$ and $B$ when there are $i$ players of type $A$.)*

## Step 2: Calculate the Ratio of Transition Probabilities ($\gamma_i$)
To use the standard Markov chain formula for fixation probability, we need the ratio of the "death" step to the "birth" step: 
$$\gamma_i = \frac{P_{i, i-1}}{P_{i, i+1}}$$

Substitute the equations from Step 1. Notice that the selection probabilities $\frac{i(N-i)}{N^2}$ appear in both the numerator and denominator, so they perfectly cancel out:

$$\gamma_i = \frac{\frac{1}{1 + \exp[-\beta (\Pi_B(i) - \Pi_A(i))]}}{\frac{1}{1 + \exp[-\beta (\Pi_A(i) - \Pi_B(i))]}}$$

Let the payoff difference be $\Delta \Pi_i = \Pi_A(i) - \Pi_B(i)$. 
Substituting this in simplifies the fraction to:

$$\gamma_i = \frac{1 + \exp[-\beta \Delta \Pi_i]}{1 + \exp[\beta \Delta \Pi_i]}$$

We can simplify this further using a basic algebraic trick. Multiply the numerator and denominator by $\exp[-\beta \Delta \Pi_i]$:

$$\gamma_i = \frac{1 + \exp[-\beta \Delta \Pi_i]}{1 + \exp[\beta \Delta \Pi_i]} \cdot \frac{\exp[-\beta \Delta \Pi_i]}{\exp[-\beta \Delta \Pi_i]}$$

$$\gamma_i = \frac{(1 + \exp[-\beta \Delta \Pi_i]) \exp[-\beta \Delta \Pi_i]}{\exp[-\beta \Delta \Pi_i] + 1}$$

The term $(1 + \exp[-\beta \Delta \Pi_i])$ cancels out entirely from the top and bottom, leaving us with a beautiful, exact simplification:

$$\gamma_i = \exp[-\beta \Delta \Pi_i]$$
$$\gamma_i = \exp[-\beta (\Pi_A(i) - \Pi_B(i))]$$

## Step 3: The General Fixation Probability
The standard formula for the fixation probability of a single mutant in a birth-death process is:

$$\rho_A = \frac{1}{1 + \sum_{k=1}^{N-1} \prod_{i=1}^k \gamma_i}$$

Plug our simplified $\gamma_i$ into the product:

$$\prod_{i=1}^k \gamma_i = \prod_{i=1}^k \exp[-\beta (\Pi_A(i) - \Pi_B(i))]$$

Because multiplying exponentials is the same as adding their exponents, the product becomes a sum inside the exponent:

$$\prod_{i=1}^k \gamma_i = \exp\left[ -\beta \sum_{i=1}^k (\Pi_A(i) - \Pi_B(i)) \right]$$

Finally, substitute this back into the main formula to get the **exact general fixation probability for the Fermi process**:

$$\rho_A = \frac{1}{1 + \sum_{k=1}^{N-1} \exp\left[ -\beta \sum_{i=1}^k (\Pi_A(i) - \Pi_B(i)) \right]}$$

---

## Step 4: Special Case - Constant Fitness
If the game has constant fitness (meaning $\Pi_A$ and $\Pi_B$ are fixed numbers that do not depend on the frequency $i$), then the payoff difference $\Delta \Pi = \Pi_A - \Pi_B$ is a constant.

The exponent summation simply becomes $k \cdot \Delta \Pi$:
$$\prod_{i=1}^k \gamma_i = \exp[-\beta k \Delta \Pi] = (\exp[-\beta \Delta \Pi])^k$$

This turns the denominator into a standard geometric series: $\sum_{k=1}^{N-1} x^k$ where $x = \exp[-\beta \Delta \Pi]$. Using the geometric series sum formula, the fixation probability resolves to a closed form:

$$\rho_A = \frac{1 - \exp[-\beta (\Pi_A - \Pi_B)]}{1 - \exp[-\beta N (\Pi_A - \Pi_B)]}$$

*(This elegantly mirrors the exact formulation of the fixation probability in the standard Moran process with constant fitness, but driven by imitation rather than reproduction!)*