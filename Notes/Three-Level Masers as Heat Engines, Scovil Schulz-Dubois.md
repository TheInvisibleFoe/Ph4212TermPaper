---
title: Three-Level Masers as Heat Engines, Scovil Schulz-Dubois
date: 2026-04-14
lastmod: 2026-04-14
tags:
  - concept
  - status/1
  - literature
  - quantum/thermodynamics
  - maser
aliases: []
publish: true
anki-status: status/1
anki-last-sync:
---
> [!summary] TL;DR
> Note/Paper by H.E.D. Scovil and E.O. Shulz-DuBois published in PRL March 15, 1959 - Vol 2, Num 6.
> The paper intends to demonstrate that three-level masers can be regarded as heat engines.

# Some preliminary definitions
- [[Maser]]
- [[Heat Engine]]
- [[Carnot Theorem]]
- A lot of topics linked through the pre-requisites at the top of [[Quantum Engines and Refridgerators, Cangemi et al]]

# The Scovil-Schulz-DuBois (SSDB) Three-Level Maser Model
In 1959, Scovil and Shulz-DuBois demonstrated (theoretically) that one can use three discrete energy levels and two thermal baths to build a quantum analogue of a classical [[Heat Engine]].

## Setup: Quantum Piston
Let us use the typical three level system with $E_{3}>E_{2}>E_{1}$ as described in [[Maser]]. To keep the algebra simple, let us set $E_{1}=0$.

We couple this three-level system (it is truly unfortunate that Three and Two share the same first alphabet) to the environment in three ways:
1. **The Hot Bath**: This is held at some temperature $T_{H}$, and acts as the *pump* here, i.e. it couples $\ket{1}$ and $\ket{3}$. The bath constantly attempts to thermalize $p_{1}$ and $p_{3}$.
2. **The Cold Bath**; This is held at some temperature $T_{C}$, and couples $\ket{1}$ and $\ket{2}$. It attempts to thermalize the populations $p_{1}$ and $p_{2}$.
3. **The Work Extraction**: The $\ket{2}$ $\leftrightarrow$ $\ket{3}$ transitions are isolated from both the thermal baths, and it is coupled to a resonant electromagnetic cavity - this is where we hope to extract macroscopic coherent work in the form of stimulated emission via masing.

How to we couple certain energy gaps to certain baths? Simply, we connect the Three-Level system to a bath using a **filter** that only allows excitations that are resonant with the energy gap that we want coupled via this particular bath.

> [!NOTE] A small change in convention in maser levels
> Note that we will be treating $\ket{2}$ as the state **to** which we carry out stimulated emission, not $\ket{1}$ as in [[Maser]].

## Steady-State Populations
Assume that the coupling to the thermal baths is very strong, and thus the system reaches steady-state.

Using the detailed balance conditions derived in [[Open Quantum Systems and Thermalization#^4d7504]] and [[Open Quantum Systems and Thermalization#^c1ed26]] (i.e. the KMS condition), we can see that:
$$
\begin{align}
	\frac{p_{3}}{p_{1}} = \exp\left( -\frac{E_{3}}{k_{B}T_{H}} \right) \\
	\frac{p_{2}}{p_{1}} = \exp\left( -\frac{E_{2}}{k_{B}T_{C}} \right)
\end{align}
$$
Note that both the excited states are thermally tied to the ground state. This is a critical design feature of this engine.

## Masing (or, Lasing) Condition: Negative Temperatures
For our engine to output useful "work", it must emit coherent photons from the $\ket{3}\to \ket{2}$ transition. As seen in [[Effective Temperature and Non-Equilibrium States]] and [[Maser#The Impossibility of the Two-Level Continuous Inversion]], we require population inversion (i.e. $p_{3}>p_{2}$) and thus a negative effective temperature between these two levels. Substituting the steady-state thermal distributions into the population inversion inequality,
$$
	\exp\left( -\frac{E_{3}}{k_{B}T_{H}} \right) > \exp\left( -\frac{E_{2}}{k_{B}T_{C}} \right)
$$
Using the monotonicity of the exponential, and rearranging, we arrive at **the fundamental operational threshold for the maser engine**:
$$
	\frac{E_{3}}{T_{H}} < \frac{E_{2}}{T_{C}} \implies \frac{T_{C}}{T_{H}} < \frac{E_{2}}{E_{3}}
$$Thus, if we tune our energy levels $(E_{2},E_{3})$ and the bath temperatures to satisfy this condition, the hot bath will pump electrons into the level 3 faster than the cold bath can populate level 2 (by pulling from the ground level population). Steady population inversion can thus be achieved, and coupled to the resonant cavity such a system will **continuously lase/mase**! We have our long-awaited steady stream of coherent photons.

## Quantum Efficiency vs. The Carnot Bound
To finalize the analysis, we want to calculate how efficient this maser engine is - and how does it compare to a classical carnot engine that operates between these baths?

We begin by tracking the energy of a single complete cycle. We talk in terms of electrons just for the sake of it:
- An electron in the ground state first absorbs a "hot" photon from the reservoir at $T_{H}$ temperature, and this takes it to level 3.
	- Heat intake: $Q_{\text{in}} = E_{3}$
- The electron undergoes stimulated emission, dropping to level 2 and releasing a coherent photon in the cavity as work.
	- Work outflow: $W = E_{3}-E_{2}$
- The electron drops from level 2 back to the ground state, dumping a "cold" photon into the bath at temperature $T_{C}$.
	- Heat outflow: $Q_{\text{out}}=E_{2}$

Note that first law is cleanly satisfied, as,
$$

^4885cf
	W = Q_{\text{in}}-Q_{\text{out}}
$$
We calculate the quantum efficiency using the typical definition of efficiency (as in [[Heat Engine#Thermal efficiency]]):
$$
	\eta_{Q} = \frac{W}{Q_{\text{in}}} = \frac{E_{3}-E_{2}}{E_{3}} = 1 - \frac{E_{2}}{E_{3}}
$$
Looking back at the threshold condition for lasing/masing [[#^4885cf]], we see that:
$$
	\frac{E_{2}}{E_{3}} > \frac{T_{C}}{T_{H}}
$$
and substituting this directly into the quantum efficiency expression we get:
$$
	\eta_{Q} = 1 - \frac{E_{2}}{E_{3}} < 1 - \frac{T_{C}}{T_{H}} = \eta_{\text{carnot}}
$$
**The [[Carnot Theorem]] still holds!**. If we try to increase efficiency any furhter by tuning the energy levels, the lasing/masing inequality will collapse and there will be no steady population inversion. This, in a way, demonstrates that the Second Law of Thermodynamics holds even in such quantum systems.

---
## Connections & Derivations
- **Prerequisites:** [[ ]]
- **Follow-up:** [[ ]]
- **Relevant Literature:** 
