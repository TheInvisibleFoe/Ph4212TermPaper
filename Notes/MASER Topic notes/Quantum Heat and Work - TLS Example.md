---
title: Quantum Heat and Work - TLS Example
date: 2026-04-16
lastmod: 2026-04-16
tags:
  - concept
  - status/1
  - quantum/thermodynamics
  - example
aliases: []
publish: true
anki-status: status/1
anki-last-sync:
---
> [!summary] TL;DR
> This note describes a very simple example of a quantum system (a TLS, spin-1/2 particle) interacting with an external, uniform magnetic field.

# Setup: Hamiltonian and Density Matrix
Let us choose the $z$-axis for the magnetic field direction. The interaction of the field with the spin-1/2 particle is given by the usual Zeeman Hamiltonian:
$$
	H = -\vec{\mu} \cdot \vec{B} = \frac{g \mu_{B} B}{2} \sigma_{z}
$$
Where all the terms mean the usual things. To keep the algebra simplified, we first define the energy gap between the states as:
$$
	E \equiv g \mu_{B} B
$$
In the energy eigenbasis of $\{ \ket{\uparrow}, \ket{\downarrow}\}$, the Hamiltonian is the following diagonal basis:
$$
H = 
	\begin{pmatrix}
	\frac{E}{2} & 0 \\
	0 & -\frac{E}{2}
	\end{pmatrix}
$$
Where the diagonal elements are the energy eigenvalues of the excited and ground states.

Let us now assume that the system is thermalized in some fashion, which means that the density matrix of the system can be written as:
$$
	\rho = \begin{pmatrix}
	p_{2} & 0 \\
	0 & p_{1}
	\end{pmatrix}
$$
Where $p_{1}$ and $p_{2}$ are the *classical probabilities* of the system being in each state. By definition, thus,
$$
	p_{1}+p_{2}=1 \implies dp_{1}=-dp_{2}
$$

^7a2b8e
which importantly implies that for this system any change in population must be *perfectly balanced*.

# The Internal Energy
As defined in [[Quantum Heat and Work]], the internal energy of the system is given as:
$$
	U = \mathrm{Tr}(\rho H) = p_{1}\left( -\frac{E}{2} \right) + p_{2}\left( \frac{E}{2} \right) = \frac{E}{2}(p_{2}-p_{1})
$$
Let us take an exact differential of this expression for get to a first law like expression:
$$
	dU = \frac{p_{2}-p_{1}}{2}dE + \frac{E}{2}d(p_{2}-p_{1})
$$
Using the exact balance condition [[#^7a2b8e]] here, we get,
$$
	dU = \frac{p_{2}-p_{1}}{2}dE + Edp_{2}
$$
Where as per the identification made in [[Quantum Heat and Work]], we identify the first term as Quantum Work ($dW$) and the second term as Quantum Heat ($dQ$).

# Physical Interpretation of the terms

## Quantum Work
$$
	dW = \mathrm{Tr}(\rho dH) = \frac{p_{2}-p_{1}}{2}dE
$$
Here, as we have discussed before, the population $(p_{1},p_{2})$ are constant and the energy gap $E$ is what changes. Physically, this can only happen if a parameter in the Hamiltonian changes, and in this case this parameter is the magnetic field strength $B$.

Because the populations do not change, the density matrix also does not change, and *the von Neumann entropy remains the same*,
$$
	S = - k_{B} \mathrm{Tr}(\rho \ln(\rho))
$$
Therefore, we can conclude that modulating the magnetic field that couples to a closed quantum system like this is an **isentropic (adiabatic) process**. "Mechanical" work is being done on the system by physically changing the energy gap, against the statistically determined weight of the state occupations.

## Quantum Heat
$$
	dQ = \mathrm{Tr}(Hd\rho) = E dp_{2}
$$
Here, the Hamiltonian is constant, and thus the magnetic field (the only parameter than can change in the Hamiltonian) is also constant. The change here is in the populations.

A population change can occur if the spin system is coupled to an external thermal bath (like a phonon bath in a lattice, if this system were to be embedded in one). The system in this case absorbs a quantum of energy from the bath and promotes a spin from the ground state to the excited state. Such a transition will show up as an increase in the excited state probability (i.e. $dp_{2}>0$).

Since the density matrix $\rho$ changes, the von Neumann entropy of the system changes. This is, of course, the calling card of heat exchange - the energy transfer accompanied by a change in entropy.

---
## Connections & Derivations
- **Prerequisites:** [[ ]]
- **Follow-up:** [[ ]]
- **Relevant Literature:** 
