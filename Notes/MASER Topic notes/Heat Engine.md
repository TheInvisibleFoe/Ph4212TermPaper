---
title: Heat Engine
date: 2026-04-15
lastmod: 2026-04-15
tags:
  - concept
  - status/1
  - thermodynamics
aliases: []
publish: true
anki-status: status/1
anki-last-sync:
---
> [!summary] TL;DR
> A thermodynamic heat engine is a theoretical (and practical) construct that extracts macroscopic usable work from the miscroscopic thermal energy of a system.

Fundamentally, a heat engine operates in a closed, cyclic process. It absorbs heat from a high-temperature reservoir. converts a portion of that thermal energy into mechanical work, and rejects the remaining heat to a low-temperature reservoir.

# The Laws of Thermodynamics applied to Heat Engines
Let us define some variables of the system:
- $T_{H}$: Temperature of the hot reservoir
- $T_{C}$: Temperature of the cold reservoir
- $Q_{H}$: Heat absorbed from the hot reservoir (Note, $Q_{H}>0$)
- $Q_{C}$: Heat rejected into the cold reservoir (Note, $Q_{C}<0$ but just $|Q_{C}|$ is often used for clarity)
- $W$: Net work done by the engine on the surroundings

## The First Law (Energy Conservation)
Since Heat Engines are cyclic, the system of the engine returns to its initial state after one complete cycle. This means that there is no net change in the internal energy of the engine over one complete cycle, i.e. $\Delta U=0$. Therefore, we must have:
$$
	W = Q_{H}-|Q_{C}|
$$
## Thermal efficiency
We can define **thermal efficiency** ($\eta$) for the engine as,
$$
	\eta = \frac{W}{Q_{H}}= \frac{Q_{H}-|Q_{C}|}{Q_{H}} = 1- \frac{|Q_{C}|}{Q_{H}}
$$

^411607
## The Second Law (as per Kelvin-Planck Statement)
It is not possible for any device operating in a thermodynamic cycle to receive heat from a single thermal reservoir and produce a net amount of work. Mathematically, this essentially enforces that $|Q_{C}|>0$. Therefore, we always have $\eta<1$.

# Ideal Limit of the Heat Engine: The Carnot Cycle
To determine the maximum theoretical limit of a heat engine's efficiency, **Sadi Carnot** proposed a perfectly reversible cycle consisting of *four* distinct processes.
For ease of derivation (due to a particularly nice EOS), an **ideal gas** is taken to be the working fluid of this *Carnot Engine*. The basic trick that the cycle pulls to maximize its efficiency is a complete elimination of any entropy generation due to irreversible processes or *finite temperature difference heat conduction*.

### Step 1: Reversible Isothermal Expansion
The gas is made to expand from some volume $V_{1}$ to some volume $V_{2}$ while in contact with a hot reservoir. Since the process is isothermal, the temperature is constant and $\Delta U = 0$.
We get,
$$
	Q_{H} = W_{1 \to 2} = \int_{V_{1}}^{V_{2}} P dV = \frac{\int_{V_{1}}^{V_{2}}(RT_{H})}{V dV} = RT_{H} \ln\left( \frac{V_{2}}{V_{1}} \right)
$$
### Step 2: Reversible Adiabatic Expansion
Now, we thermally isolate the system (i.e. $Q=0$) and allow it to expand from $V_{2}$ to $V_{3}$. The gas does some work in this process, at the expense of its internal energy. This cools it from $T_{H}$ to $T_{C}$. Using the adiabatic relation,
$$
	TV^{\gamma-1} = \text{constant}
$$
Where $\gamma=\frac{C_{p}}{C_{v}}$.
Thus, we have,
$$
	T_{H}V_{2}^{\gamma-1} = T_{C}V_{3}^{\gamma-1}
$$

^bee531
### Step 3: Reversible Isothermal Compression
The gas is now put into contact with the cold reservoir, and is compressed from $V_{3}$ to $V_{4}$. Work is done *on* the gas in this process, and heat is thus expelled into the reservoir.
$$
	|Q_{C}| = - W_{3 \to 4} = - \int_{V_{3}}^{V_{4}} \frac{R T_{C}}{V}dV = RT_{C} \ln\left( \frac{V_{3}}{V_{4}} \right)
$$
### Step 4: Reversible Adiabatic Compression
The gas is again thermally isolated, and is *compressed* from $V_{4}$ back to the initial volume $V_{1}$. This heats the gas from $T_{C}$ to $T_{H}$. Again, we have the relation,
$$
	T_{C}V_{4}^{\gamma-1} = T_{H}V_{1}^{\gamma-1}
$$

^39deb4
## Deriving Carnot Engine's efficiency
Note that the equation derived above allow us to have expressions for $Q_{H}$ and $Q_{C}$. There are two ways of getting to a nice expression for the efficiency.
### Relating Volume Ratios
Notice that using [[#^bee531]] and [[#^39deb4]] we have,
$$
	\left( \frac{V_{2}}{V_{1}} \right)^{\gamma-1} = \left( \frac{V_{3}}{V_{4}} \right)^{\gamma-1}
$$
Which leads to the crucial geometric symmetry of:
$$
	\frac{V_{2}}{V_{1}} = \frac{V_{3}}{V_{4}}
$$

^b563a3
Now, taking the ratio of heats,
$$
	\frac{|Q_{C}|}{Q_{H}} = \frac{RT_{C}\ln\left( \frac{V_{3}}{V_{4}} \right)}{RT_{H}\ln\left( \frac{V_{2}}{V_{1}} \right)}
$$
The logarithms cancel out because of [[#^b563a3]], and so we get,
$$
	\frac{|Q_{C}|}{Q_{H}} = \frac{T_{C}}{T_{H}}
$$

^7907a1
Substituting this back into the general efficiency equation [[#^411607]], we get:
$$
	\eta_{\text{Carnot}}= 1- \frac{T_{C}}{T_{H}}
$$
### Entropy and Clausius Theorem
The more elegant way to view this is through entropy ($S$). For a reversible cycle, the Clausius Theorem assures that the net change in entropy is zero. Since entropy is a state function, the integral of $dS$ over a closed cycle for the system is zero. So, we have,
$$
	\oint \frac{dQ_{\text{rev}}}{T} = 0
$$
Since heat is only exchanged during the isothermal steps in the Carnot Cycle, the integral simplifies to:
$$
	\frac{Q_{H}}{T_{H}} - \frac{|Q_{C}|}{T_{C}} = 0 \implies \frac{Q_{H}}{T_{H}} = \frac{|Q_{C}|}{T_{C}}
$$
This easily gives us the ratio in [[#^7907a1]] , and allows us to derive the Carnot efficiency.

> [!NOTE] Importance of the Carnot Cycle
> Note that the Carnot Cycle, designed as described above, is very general in scope. The expression for the efficiency of the Engine (derived above using an ideal gas as the working fluid) holds for **any** fluid that can be used, i.e. it is entirely independent of the working substance. The Carnot Engine thus serves as a theoretical boundary condition for the second law of thermodynamics.



---
## Connections & Derivations
- **Prerequisites:** [[ ]]
- **Follow-up:** [[ ]]
- **Relevant Literature:** 
