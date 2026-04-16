---
title: Quantum Heat and Work
date: 2026-04-16
lastmod: 2026-04-16
tags:
  - concept
  - status/1
  - quantum/thermodynamics
  - open-quantum-systems
aliases: []
publish: true
anki-status: status/1
anki-last-sync:
---
> [!summary] TL;DR
> Here, we try to extend the classical thermodynamic concepts of Heat and Work to Quantum Mechanical systems.

Classically, the first law of thermodynamics is straightforward: The (change in) Internal Energy of the system is the sum of the Heat added to the system and the work done on the system:
$$
	dU = dQ + dW
$$
Now, to build a quantum thermodynamic framework, we need to map $dQ$ and $dW$ onto quantum observables. We begin by using a *density matrix* ($\rho$) representation of the system. The reason we do this is that the density operator formalism allows us to handle statistical mixtures (ensembles) which should be crucial for thermal states. Let $H$ be the Hamiltonian for the system.

The internal energy $U$ of the quantum system is defined simply as the expectation value of the Hamiltonian:
$$
	U \equiv  \langle H \rangle = \mathrm{Tr}(\rho H)
$$
To find a first law equivalent, we take an exact differential of this internal energy. Since the Trace is a linear operation, we get:
$$
	dU = \mathrm{Tr}(d\rho H)+\mathrm{Tr}(\rho dH)
$$
This nicely mirrors the form of the classical first law of course, but what do the terms mean?

## Quantum Heat ($dQ$)
The first term, $\mathrm{Tr}(d\rho H)$ describes a process where the energy levels (i.e. the Hamiltonian itself) remains fixed, but the state of the system changes (i.e. we have $d\rho$). Physically, this represents transitions of the system between energy levels - which can only be driven by interactions with an external environment (like a heat bath). Precisely, this is like the system absorbing or emitting a photon, when the external environment is a quantized radiation field. Therefore, we can identify this term as the **quantum heat**:
$$
	dQ = \mathrm{Tr}(H d \rho)
$$
## Quantum Work ($dW$)
The second term, $\mathrm{Tr}(\rho dH)$, describes a process where the state of the system (i.e. $\rho$) is constant, but the Hamiltonian itself changes. Physically, this can happen when a parameter of the Hamiltonian is varied (say, changing the applied field). The populations of the energy levels do not change as $\rho$ is still the same, but the **energy eigenvalues** of the levels change. Therefore, we identify:
$$
	dW = \mathrm{Tr}(\rho dH)
$$

Looking at this setup in the energy eigenbasis $\{\ket{n}\}$, where $H \ket{n}=E_{n}\ket{n}$, **and** the density matrix has diagonal elements $p_{n}$ (which are the population probabilities of the $n$th states), the traces simplify to:
$$
	dQ = \sum_{n}E_{n}dp_{n}
$$
and,
$$
	dW = \sum_{n}p_{n}dE_{n}
$$
Instead of writing it like this, keeping it all inside the density matrix allows us to deal with systems where there are quantum coherences (i.e. off-diagonal elements in the density matrix) - these end up playing an important role in advanced quantum engines.

- [[Quantum Heat and Work - TLS Example]]


---
## Connections & Derivations
- **Prerequisites:** [[ ]]
- **Follow-up:** [[ ]]
- **Relevant Literature:** 
