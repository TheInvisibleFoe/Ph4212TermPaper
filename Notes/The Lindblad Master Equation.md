---
title: The Lindblad Master Equation
date: 2026-04-16
lastmod: 2026-04-16
tags:
  - concept
  - status/1
  - open-quantum-systems
  - quantum/thermodynamics
aliases: []
publish: true
anki-status: status/1
anki-last-sync:
---
> [!summary] TL;DR
> The Lindblad Master Equation, or formally the Gorini-Kossakowski-Sudarshan-Lindblad (GKLS) equation, is the fundamental equation of motion for open quantum systems.

# The Mathematical Constraints
If you have a closed system, the density matrix $\rho$ evolves according to the von Neumann equation:
$$
	\frac{d\rho}{dt} = -\frac{i}{\hbar}[H,\rho]
$$
When we "open" this system up to a bath, we are effectively adding a *superoperator* $\mathcal{L}$ called the Liouvillian, that acts on the density matrix as:
$$
	\frac{d\rho}{dt} = \mathcal{L}[\rho] 
$$

- [[What is a Superoperator?]]

The Liouvillian is a generic, stand-in superoperator and is used to denote the superoperator that shows up on the RHS of the generic density matrix equation of motion.

$\mathcal{L}$ can not be any arbitrary function, as it needs to satisfy several constraints that keep $\rho(t)$ a physically valid representation of the system. These constraints are:
1. **Hermiticity Preservation**: If $\rho$ starts Hermitian (i.e. $\rho = \rho ^{\dagger}$), it must remains so
2. **Trace Preservation**: The sum of the probabilities must always be equal to one, $\mathrm{Tr}[\rho(t)]=1$.
3. **Complete Positivity**: This is the strictest condition, and tells us that it is not enough that the eigenvalues of $\rho$ remain positive - if the environment that the system is entangled with is an isolated system in itself then the evolution of the primary system *should not cause the combined system to develop negative probabilities*.

In 1976, Gorini, Kossakowski Sudarshan, and Lindblad independently proved that any dynamical generator $\mathcal{L}$ that is **Markovian** (memoryless) and satisfies these conditions *must* take a specific algebraic form:
$$
	\mathcal{L}[\rho] = -\frac{i}{\hbar}[H,\rho] + \sum_{k} \gamma_{k} \left( L_{k}\rho L_{k}^{\dagger} - \frac{1}{2}\{L_{k}^{\dagger}L_{k},\rho\} \right) 
$$
If the Liouvillian does not have this form, the differential equation for $\rho$ will eventually violate alteast one of the conditions set down above.

- [ ] Go over the derivation, and add it here ➕ 2026-04-16 

# Understanding the Dissipator Term
The second term in the Liouvillian is called the *dissipator* term. This is the part of the Liouvillian that is responsible for the non-unitary evolution of the system. It is driven by the **jump operators**, or, the **Lindblad operators** $L_{k}$. Each of these represent distinct ways in which the system interacts with the environment. $\gamma_{k}$s represent the rate of the interaction.

> [!example] Atom undergoing [[Spontaneous Emission]]
> In this case, the jump process is the atomic lowering operator:
> $$
>	L = \sigma_{-} = \ket{g} \bra{e} 
> $$
> Where $\ket{g}$ is the ground state and $\ket{e}$ is the excited state.

^8333ce

The dissipator itself has two distinct terms, which we now attempt to explain separately.

## First Term of the Dissipator: The Quantum Jump ($L_{k}\rho L_{k}^{\dagger}$)
Mathematically, this is called a *complete positive map*. It describes the system making a transition, or a *jump*.

Following through with [[#^8333ce]], if the atom is already in the excited state $\rho = \ket{e}\bra{e}$, then applying the jump operator in this term gives us,
$$
	L \rho L^{\dagger} = \sigma_{-} (\ket{e} \bra{e} )\sigma_{+} = \ket{g} \bra{g} 
$$
This term thus takes the population from the excited state and puts it into the ground state. In doing so, it represents the sudden and discontinuous movement when the atom spontaneously emits a photon and collapses into the ground state. This justifies calling it a "jump".

## Second Term of the Dissipator: The Attrition ($-\frac{1}{2} \{L_{k}^{\dagger}L_{k},\rho\}$)
Since the first term feeds the population into the target state, the second term must ensure that the total trace remains exactly 1.

Note that $L_{k}^{\dagger}L_{k}$ is a Hermitian operator. Continuing with the example, our atom has,
$$
	L^{\dagger}L = \sigma_{+}\sigma_{-} = \ket{e} \bra{e}
$$
which is the number operator for the excited state.
The anticommutator term looks like,
$$
	- \frac{1}{2} (L^{\dagger}L\rho + \rho L^{\dagger}L)
$$
If the atom is in an excited state, this would simply evaluate to $-\ket{e}\bra{e}$. This perfectly cancels out the trace gained by the first term!

Further, the anticommutator governs the evolution of the system when such a jump *does not* happen. Thinking more in terms of information (and measurement), let us assume that we are waiting for a signal from this TLS with a perfect photon detector that has infinite resolution in time. After each interval of time we wait where we *do not* register a spontaneous emission from the TLS, we do gain some information about the system - it becomes a bit more unlikely that it was never in the excited state to begin with. This causes us to smoothly update the density matrix (which makes sense, as the entries there are classical probabilities of the system being in a particular state) to reflect this knowledge. Such an update is described by the anticommutator term.

Another interesting factor is that this term explicitly acts on the off-diagonal terms of the density matrix, i.e. the "coherences". Even if a spontaneous jump does *not* occur, the possibility of the bath interacting with the system causes the phase coherence between the $\ket{e}$ and $\ket{g}$ states to exponentially decay - giving rise to decoherence. To see why this is true, we note that this term is **non-Hermitian**. This means that the probability is deliberately not conserved.

- [ ] Add some more detailed explanation to this part, too wishy-washy at the moment ➕ 2026-04-16 


---
## Connections & Derivations
- **Prerequisites:** [[ ]]
- **Follow-up:** [[ ]]
- **Relevant Literature:** 
