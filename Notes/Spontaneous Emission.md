---
title: Spontaneous Emission
date: 2026-04-14
lastmod: 2026-04-14
tags:
  - concept
  - status/1
  - qft
  - quantum
  - radiation
aliases: []
publish: true
anki-status: status/1
anki-last-sync:
---
> [!summary] TL;DR
> Spontaneous emission is the process by which a quantum system (anything, an atom for example) transitions from an excited energy state to a lower energy state without any external electromagnetic field driving the transition, and emitting a photon in the process.

Rutherford's model of the atom failed because it could not be reconciled with the prediction of Classical Electromagnetism - an accelerated charge will radiate energy in the form of electromagnetic waves. Bohr tackled this problem using the idea of stationary states in orbit. But even this idea has a problem - it can not explain why an electron in an excited stationary state would eventually decay to a less energetic stationary state.

Albert Einstein, in 1916, introduced the idea of the $A$ coefficient for spontaneous emission *purely through thermodynamic arguments*. Eventually, QED would provide the fundamental microscopic mechanism - vacuum fluctuations.

## Thermodynamic Argument for Spontaneous Emission
Consider a two-level system that is in thermal equilibrium with a *blackbody radiation field* inside a cavity, at some temperature $T$.

The energy levels here are $E_{1}$ and $E_{2}$, with the energy difference being $\Delta E = E_{2}-E_{1} = \hbar \omega$.

Let $\rho(\omega)$ be the spectral energy density of the radiation field at angular frequency $\omega$.

There are three processes that are occurring here:
1. **Stimulated Absorption**: An atom in the state $E_{1}$ absorbs a photon and jumps to $E_{2}$. The rate of this process is given by $B_{12}\rho(\omega)N_{1}$ (say).
2. **[[Stimulated Emission]]**: A photon induces an atom in $E_{2}$ to drop to $E_{1}$, emitting an identical photon. The rate of this process is given by $B_{21}\rho(\omega)N_{2}$.
3. **Spontaneous Emission**: An atom in $E_{2}$ state spontaneously drops down to $E_{1}$. The rate of this process is given by $A_{21}N_{2}$. Since it is "spontaneous", the rate has no dependency on the radiation field itself.
At thermal equilibrium, the population $N_{1}$ and $N_{2}$ are constant - this means that the total rate of upward transitions must be exactly balanced by the total rate of downward transitions (this is a detailed balance),
$$
B_{12}\rho(\omega)N_{1} = A_{21}N_{2} + B_{21}\rho(\omega)N_{2}
$$

^eq:detailed_balance

Rearranging this expression, we can solve for an expression for the radiation spectral density,
$$
\rho(\omega) = \frac{A_{21}N_{2}}{B_{12}N_{1}-B_{21}N_{2}} = \frac{A_{21}}{B_{12}\left( \frac{N_{1}}{N_{2}} \right) - B_{21}}
$$
^eq:radiation_density ^617fa6

As the system is in thermal equilibrium, the populations much follow the Maxwell-Boltzmann distribution:
$$
\frac{N_{1}}{N_{2}} = \exp\left( \frac{\hbar \omega}{k_{B}T} \right)
$$

^eq:population_boltzmann

If we substitute this into [[#^617fa6]], we can see that we arrive at something very similar to Planck's Law for Blackbodies,
$$
\rho(\omega) = \frac{A_{21}}{B_{12}\exp\left( \frac{\hbar \omega}{k_{B}T} \right) - B_{21}}
$$

^eq:almost_planck ^317df9

Einstein recognized the similarity and demanded that for this quantum model to be valid, the radiation density $\rho(\omega)$ must perfectly match Planck's Law for Blackbody Radiation, which is known to be,
$$
\rho(\omega) = \frac{\hbar \omega^3}{\pi^2c^3} \frac{1}{\exp\left( \frac{\hbar \omega}{k_{B}T} \right) - 1}
$$

^eq:planck_blackbody ^2f90d3

### Extracting Einstein Coefficients from the identification with Planck's Law
Comparing equations [[#^317df9]] and [[#^2f90d3]], we get two facts.

The first is that for the denominator to match we must have,
$$
B_{12}=B_{21}\equiv B
$$

^eq:absorption_emission

Which means that the probability of an incident photon causing stimulated absorption is identical to the probability of it causing stimulated emission.

Secondly, if we factor out the $B$ from the denominator and compare the numerators, we can find the following relationship:
$$
A_{21} = \frac{\hbar \omega^3}{\pi^2 c^3} B_{21}
$$

^eq:a_coeff ^76e62b

This is the required expression for the $A$ coefficient as described beforehand.

### Physical Implications: Why are masers easy to realize and lasers not?
Note that the Einstein A coefficient as described in [[#^76e62b]] has a crucial $\omega^3$ dependence. This implies the following:
1. In the microwave regime ($\approx 10^{10} Hz$), $\omega$ is quite small. Therefore, the $A$ coefficient is also small and spontaneous decay is not a huge threat - we can obtain a stable population inversion state with moderate pumping. This is why masers are relatively easy to construct, and predate lasers. Excited spin states in ruby crystals (used as the medium for early masers) can sit in the intermediate state for seconds or milliseconds, which makes the state highly metastable.
2. In the optical regime ($\approx 10^{14} Hz$), $\omega$ is quite large and spontaneous emission is thus a huge factor. This results in the metastablility of the intermediate state being reduced. We require a much stronger, and frequent pump to maintain population inversion.

Of course, beyond this thermodynamic treatment of the problem, QED (Quantum Electrodynamics) provides a more rigorous understanding of the problem. It explains the phenomena of spontaneous emission using the concept of **vacuum fluctuations** in the electromagnetic field, which in turn couples to the system in the excited state and then induces a stimulated emission. Thus, in reality, *spontaneous emission is understood to be stimulated emission due to zero-point vacuum fluctuations of the electromagnetic field*.


---
## Connections & Derivations
- **Prerequisites:** [[ ]]
- **Follow-up:** [[ ]]
- **Relevant Literature:** 
