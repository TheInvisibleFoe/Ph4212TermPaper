---
title: What is a Superoperator?
date: 2026-04-16
lastmod: 2026-04-16
tags:
  - concept
  - status/1
  - open-quantum-systems
aliases: []
publish: true
anki-status: status/1
anki-last-sync:
---
> [!summary] TL;DR
> An explanation of superoperators, like the Liouvillian that shows up in the general density matrix equation of motion 

When we move from the usual wavefunction formalism to the density matrix formalism, we move from a *vector* (1D) to a *density matrix* (2D). The state of the system is now essentially an operator on the Hilbert space itself.

Therefore, if we want to evolve the density matrix, we require a mathematical object that takes this matrix and spits out a new matrix.

> [!definition] Superoperator
> A function that maps an operator on the Hilbert Space to another operator on the Hilbert Space is called a superoperator.

The entire $H\rho - \rho H$ form of the commutator as used in the normal von Neumann Equation of Motion, for example, can be represented by a single operator acting on the density matrix, as it requires a matrix multiplication from either side. We thus require the concept of the superoperator to generalize the RHS of the von Neumann equation.

---
## Connections & Derivations
- **Prerequisites:** [[ ]]
- **Follow-up:** [[ ]]
- **Relevant Literature:** 
