---
title: Quantum Engines and Refridgerators, Cangemi et al
date: 2026-04-15
lastmod: 2026-04-15
tags:
  - concept
  - status/1
  - quantum/thermodynamics
aliases: []
publish: true
anki-status: status/1
anki-last-sync:
---
> [!summary] TL;DR
> Engines are systems and devices that convert one form of energy into another - typically a more useful form that can perform work.
> In classical setups, this largely involves the conversion of heat into work.
> In the quantum regime, the principles of energy conservation become ambiguous.
> This paper provides a broad overview of the the field of quantum engines and refrigerators

# Basic Concepts
- [[Quantum Heat and Work]]
- [[Open Quantum Systems and Thermalization]]
- [[Effective Temperature and Non-Equilibrium States]]
## Quantum Thermodynamic processes
In classical thermodynamics, a *process* is defined as a change that a system undergoes from some initial *equilibrium* state to a final one. During such a process, thermodynamics state variables like pressure, volume, and temperature may change.
In Quantum Mechanics, the system undergoing the thermodynamic process is considered fully quantized. As a result, the relevant variables that change along the process are now eigenenergies and energy-level occupations of the system.

Some analogues to classical thermodynamical processes can be drawn in quantum systems:
- The closest quantum counterpart to a quasistatic process can be imagined to be a quantum system undergoing an adiabatic process. This means that the control Hamiltonian for the closed quantum system changes slowly enough for the system's state to align with the *instantaneous eigenenergies of the perturbed system*, all the while maintaining a constant population.
- The analogue of the isothermal process is an open quantum system that is interacting with a heat reservoir, and the energy levels of the system slowly adjust to keep thermal equilibrium.
	- Note that if the thermalization time is significantly shorter than the internal dynamics of the system, it stays in a Gibbs state at a fixed temperature, aligned with the instantaneous Hamiltonian.
- The analogue of the isochoric process is a system where the modifications are only in the population distribution across the energy spectrum, with the energy eigenvalues remaining the same in the process. The energy interaction of the quantum system with the thermal bath is recognized as heat here, and thus leads to a change in the entropy.

## Quantum engines and refrigeration cycle
### Quantum Carnot Cycle
To understand the basic operation of an ideal quantum Carnot cycle, we start with the cycle of a heat engine with a Two-Level system (hereafter abbreviated as TLS) working medium. This heat engine operates quasistatically between two heat baths at temperatures $T_{H}>T_{C}$.
Like any other Carnot Cycle, this engine works via:
- Two isothermal strokes
- Two adiabatic strokes


---
## Connections & Derivations
- **Prerequisites:** [[ ]]
- **Follow-up:** [[ ]]
- **Relevant Literature:** 
