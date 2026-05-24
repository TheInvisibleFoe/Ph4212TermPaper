---
title: title
date:
tags:
  - 
---
# Population Growth Equation
The Population growth equation needs to be realistic. Cannot be exponential growth without any limits. Also cannot be such that one shall just die. Basically cannot be modelled by,
$$
	\dot{x} = ax
$$
Basically if $a>0$ then the population goes to $\infty$ exponentially and if $a<0$ then the population goes to 0 after some time, also exponentially decaying. Thus a realistic equation of state is given by the logistic equation,
$$
	\dot{x} = rx\left( 1-\frac{x}{K} \right)
$$
where $r$ is the reproduction rate in the absence of density regulation, $K$ is something called the carrying capacity. The carrying capacity basically models the fact that the increasing the number of individuals in a limited environment, leads to decreasing supplies for each individual. Instead of exponentials, we get the solution,
$$
	\dot{x} = \frac{K x_{0} e^{rt}}{K + x_{0} (e^{rt}-1)}
$$
In the limit of infinite time the population size goes to equilibrium $x^* =K$. One can easily say this from the flow diagram and standard methods of NLD.

# Population with selection(different species)

Selection basically means that there are different types of individuals who reproduce at different rates. One can see that in infinite populations, whether a species gets selected or not completely depends on the reproduction rate. Consider the exponential growth laws for species $x$ and $y$ with reproduction rates $a,b$. Then considering the ratio $\rho = \frac{x(t)}{y(t)}$, we get the solution
$$
\rho(t)  = \rho_{0 e^{(a-b)t}}
$$
One basically gets $\rho=0$ or $\rho=\infty$, depending on $a,b$. A more realistic modelling is when we considering the environment has limited resources, leading to a constant population. $x(t)+y(t) = 1$, where $x,y$ are species frequencies. 
$$
	 \begin{align}
		\dot{x} = x(a - \phi)  \\
		\dot{y} = y(b  -\phi)
	 \end{align}
$$
$\phi = a x + by$ ensures that total population is conserved. This can be completely replaced by the single variable equation, which already takes into account the population constraint,
$$
	\dot{x} = x(1-x)(a-b)
$$
![[Pasted image 20260502041636.png]]
The survival of the fittest is indicated by the flow diagram. This can be extended to a population with $n$ species. Consider the population frequency vector $\vec{x} = (x_{1},x_{1,\dots x_{n}})$, with the population conservation constraint, and reproduction rate $f_i$. Then the equations are given by, for each $i$,
$$
	\begin{align}
		\dot{x_{i}} = x_{i}(f_{i}-\phi) \\
		\phi = \sum_{i=1}^{n} f_{i} x_{i}
	\end{align}
$$
$\phi$ is chosen in this way to constraint the total population.

## Two species generalized equation
Consider the two species equation, but with power law growth instead of linear,
$$
	\begin{align}
		\dot{x} = ax^c - \phi x \\
		\dot{y} = by^c - \phi y
 	\end{align}
$$
with $\phi = ax^c + b^c$. Effective one variable equation,
$$
	\dot{x} = x(1-x)(a x^{c-1} - b(1-x)^{c-1})
$$
The cases $c>1$ and $c<1$ allow for mixed state equilibrium.
![[Pasted image 20260502042620.png]]
The mixed state fixed point is given by,
$$
	x^* = \frac{1}{1+\left( \frac{a}{b} \right)^{1/(c-1)}}
$$
Note that this does not exist for $c=1$.

# Mutation without selection

Basically one defines mutation with the master equation approach. The mutation rates are $u_{1} :A \to B$ and $u_{2}: B \to A$. Ignore selection for the moment with $a=b=1$. Then one can easily write the master equation,
$$
	\begin{align}
		\dot{x} = x(1-u_{1}) + y u_{2} - \phi x \\
		\dot{y} = x u_{1} = y(1-u_{2}) - \phi y
	\end{align}
$$
Since there is no selection $\phi=1$. Again we get the differential equation and the stable fixed point as,
$$
\begin{align}
	\dot{x} = u_{1} - x(u_{1} + u_{2}) \\
	x^* = \frac{u_{2}}{u_{1}+u_{2}}
\end{align}
$$
Thus mutation leads to coexistence. One can generalize this mutation dynamics over $n$ different types. Suppose that our rates are given by the mutation matrix $Q = [q_{ij}]$, where $q_{ij}$ is proportional to the probability of the jump from $i \to j$. Again this assumes the form of a stochastic matrix, since $\sum_{j=1}^n q_{ij} = 1$,
$$
	\dot{x}_{i} = \sum_{j=1}^n x_{j} q_{ji} - \phi x_{i}
$$
Under the no-selection limit, we get $\phi=1$ and the fixed point is given by,
$$
	\vec{x}^* Q= \vec{x}^* 
$$
This is the left eigenvector assosciated with the eigenvalue $1$. In our case, the right eigenvector for this eigenvalue shall be $\vec{\pi} = (1,1,\dots,1)$. One can show under certain considerations, that for an irreducible stochastic matrix, the **Perron Frobenius Theorem** guarantees the existence of a stable equilibrium. It moreover states that the equilibrium state shall be unique and independent of the initial population configuration.

# Mutation with selection
One can generalize the mutation without selection to the mutation with selection. This is called the **Quasi-species Equation**. Consider $n$ individuals, with frequency vector $\vec{x}$ , fitness vector $\vec{f}$ and mutation matrix $Q = [q_{ij}]$. Note the mutation matrix is a stochastic matrix. The average fitness is given by $\phi = \vec{x}.\vec{f}$ . The quasispecies equation is given by,
$$
	\dot{x}_{i}= \sum_{j=1}^n x_{i}f_{j}q_{ji} - \phi(\vec{x})x_{j}
$$
![[Pasted image 20260502050143.png]]