---
title: Effective Temperature and Non-Equilibrium States
date: 2026-04-16
lastmod: 2026-04-16
tags:
  - concept
  - status/1
  - non-equilibrium
  - open-quantum-systems
aliases: []
publish: false
anki-status: status/1
anki-last-sync:
---
> [!summary] TL;DR
> This notes discusses the notion of effective temperatures and non-equilibrium states in open quantum systems, particular in the context of [[Quantum Heat and Work - TLS Example]]. This is not a general overview, and the discussion is entirely oriented towards motivating the [[Maser]] and the [[Three-Level Masers as Heat Engines, Scovil Schulz-Dubois]] model.

# Detailed Balance recap
Note that in our TLS (with $E_{1}=0$ and $E_{2}=E$, say), coupled to a single bath with temperature $T$ [[The Lindblad Master Equation]] dissipator drives the system until the ration of the upward and downward jump rates equals the Boltzmann Factor (KMS condition):
$$
	\frac{\Gamma_{\uparrow}}{\Gamma_{\downarrow}} = \exp\left( -\frac{E}{k_{B}T} \right)
$$

^56e659
Since $T>0$, we always have $\Gamma_{\downarrow}>\Gamma_{\uparrow}$. The system, will *always relax into a steady state where the ground state is more populated than the excited state*, i.e. $p_{1}>p_{2}$.

Even at infinite temperature, we only ever reach $p_{1}=p_{2}=0.5$. This is obviously not ideal for the population inversion that we require (and see) in masers - thus we can not talk about masers as heat engines before we deal with this.

# Defining an effective temperature
Let us imagine that we use a very strong pump to push the system into a state where $p_{2}>p_{1}$. We can do this with a high-energy laser pulse that is resonant with the gap, for example.

Looking at the density matrix, and our previous calculations, it is clear that this system is *not in thermal equilibrium*.

However, we can invert [[#^56e659]] and define an **effective temperature** as follows:
$$
	T_{\text{eff}} = \frac{E}{k_{B}\ln\left( \frac{p_{1}}{p_{2}} \right)}
$$
It is clear that:
1. If $p_{1}>p_{2}$ as usual, $T_{\text{eff}}>0$ - the usual case.
2. If $p_{1}=p_{2}$, then $T_{\text{eff}}$ is mathematically undefined and physically infinite.
3. (**IMP**) If $p_{1}<p_{2}$, i.e. the system has population inversion, then $T_{\text{eff}}<0$. This means that we now have *negative* temperature.

# The Thermodynamics of negative temperature
In a strict thermodynamic sense, a system that has negative temperature is "hotter" than the system at any positive temperature.

To understand why, we can look at the fundamental thermodynamic definition of temperature in terms of entropy and internal energy:
$$
	\frac{1}{T} = \frac{\partial S}{\partial U}
$$
In normal systems that do not have an upper limit on its energy (say, an ideal gas), we always have increasing entropy. This is because constituents of the system occupy higher and higher states and thus a vastly larger number of microstates.

But in the case of our TLS, we have a *bounded energy spectrum*. When the entire system has no energy, we have $p_{1}=1$ and the entire system is perfectly ordered - entropy can be defined to be $S=0$ here and $T=0$.

Now, pumping in more energy and/or increasing the temperature of the system, $p_{2}$ rises and eventually at $T \to \infty$ we have $p_{1}=p_{2}$. This is a state of maximum uncertainty (or, highest disorder). Thus, the entropy vs. internal energy curve just *plateaus* here!

Pumping the system further invariably gives us a situation where we have $p_{2}>p_{1}$ - this means the system is now more ordered than the infinite temperature case! The Entropy vs. Internal Energy curve now bends down - giving us negative temperatures.

> [!NOTE] Absolute source of extractable energy
> Since we always have a flow of heat from a system that has a higher value of $\frac{\partial S}{\partial U}$ to a system with a lower value of the same, if we put a system with a any positive temperature in contact with a system that has a negative temperature, energy will always from out from the latter in the form of heat.

---
## Connections & Derivations
- **Prerequisites:** [[ ]]
- **Follow-up:** [[ ]]
- **Relevant Literature:** 
