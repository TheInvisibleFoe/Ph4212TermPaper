---
title: Open Quantum Systems and Thermalization
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
> Once we have an understanding of how to separate quantum work from quantum heat, we are required to address the mechanisms of heat exchange in quantum systems that are interacting with the surroundings.

An isolated quantum system evolves *unitarily* according to the Schrodinger equation, which is entirely reversible and preserves the entropy of the system. To exchange heat, entropy must change, so this is clearly not how the system would evolve if it were to interact with the environment/thermal bath.

# Open Quantum Systems
In real systems, like the TLS example described in [[Quantum Heat and Work - TLS Example]], the TLS is never truly isolated. It is embedded in an environment (say, a crystal lattice) that is constantly interacting with the TLS.

Mathematically, we can describe this situation using a total Hamiltonian that is written in the following way:
$$
	H_{\text{tot}} = H_{S} \otimes I_{B} + I_{S} \otimes H_{B} + H_{\text{int}}
$$
Term by term, these are:
- $H_{S}$: Isolated spin Hamiltonian on Spin Hilbert Space
- $I_{B}$: Identity operator on thermal bath Hilbert Space
- $I_{S}$: Identity operator on the Spin Hilbert Space
- $H_{B}$: Hamiltonian of the bath on the thermal bath Hilbert Space
- $H_{\text{int}}$: Interaction Hamiltonian between the spin and the bath

The bath is obviously considered to have an enormous number of degrees of freedom, and thus tracking the entire system is not possible. Instead, we can *trace out* the bath degrees of freedom to track only the reduced density matrix of the system in question:
$$
	\rho_{S}(t) = \mathrm{Tr}_{B}[\rho_{\text{tot}}(t)]
$$
This tracing is precisely what destroys the unitary and reversible nature of the evolution. The systems dynamics are now irreversible, and this allows entropy to increase and thermalization to occur.

# [[The Lindblad Master Equation]]
Under the assumptions:
- The bath is large
- The bath is thermal
- The bath is *memoryless*: This is the **Markovian Approximation**, which basically means that the bath quickly forgets any information it absorbs from the system.

The evolution of the reduced density matrix for the spin-1/2 system is now given by the **Lindblad (or, GKLS) Master Equation**. This is the fundamental equation of motion for quantum thermodynamics:
$$
	\frac{d\rho}{dt} = - \frac{i}{\hbar}[H_{S},\rho] + \mathcal{D}[\rho] 
$$
There are now two parts that are contributing to the system's evolution in time:
1. **Unitary Commutator**: The $-\frac{i}{\hbar}[H_{S},\rho]$ term is the standard and exactly the same as it shows up on the von Neumann equation of motion. It drives the **coherent, reversible dynamics** of the spin.
2. **The Dissipator**: The $\mathcal{D}[\rho]$ is a non-unitary term that accounts for the irreversible jumps that are caused by the bath, in the system.

## The Dissipator
The dissipator is normally defined in terms of specific **"jump operators"** ($L_{k}$) that describe the allowed interactions between the system and the bath, scaled by their corresponding transition rates ($\gamma_{k}$):
$$
	\mathcal{D}[\rho] = \sum_{k}\gamma_{k} \left( L_{k}\rho L_{k}^{\dagger} - \frac{1}{2}\{L_{k}^{\dagger}L_{k},\rho\} \right)
$$
Here, $\{A, B\} = AB + BA$ is the anti-commutator.
More details can be found on the dedicated note [[The Lindblad Master Equation]]

# Thermalizing the Two-Level System
To deal with a concrete example here, we use [[Quantum Heat and Work - TLS Example]]. Let us plug the TLS system into the Lindblad equation. The bath, in this case, can induce two types of jumps:
1. Emission (Spin flips down): The system goes from $\ket{\uparrow}$ to $\ket{\downarrow}$, emitting a phonon into the bath in the process. The jump operator is the lowering operator, $L_{-} = \sigma_{-}=\ket{\downarrow}\bra{\uparrow}$. Let us define the rate of this jump process to be $\Gamma_{\downarrow}$.
2. Absorption (Spin slips up): The system absorbs a phonon, jumping from $\ket{\downarrow}$ to $\ket{\uparrow}$. The jump operator is the raising operator, $L_{+} = \sigma_{+} = \ket{\uparrow}\bra{\downarrow}$. We define the rate of this jump process to be $\Gamma_{\uparrow}$.

Substituting these into the dissipator, we can calculate the rate of change for the diagonal matrix elements (i.e. $p_{1}$ and $p_{2}$) nicely. The unitary part vanishes, and we are left with:
$$
	\frac{dp_{2}}{dt} = - \Gamma_{\downarrow}p_{2} + \Gamma_{\uparrow}p_{1}
$$
**This is explicitly the equation that defines the heat flow**,
$$
	\frac{dQ}{dt} = E \cdot \frac{dp_{2}}{dt}  
$$

# The Detailed Balance Condition
The bath does not just induce random jumps in the system - it acts to drive the system towards thermal equilibrium at its temperature $T$ (say).

Again, resorting to the example described in [[Quantum Heat and Work - TLS Example]], we note that in the steady-state limit (i.e. $t \to \infty$), the populations of the states must stop changing, or $\frac{dp_{2}}{dt} = 0$. Setting this to zero, we can easily get to,
$$
	\frac{p_{2}}{p_{1}} = \frac{\Gamma_{\uparrow}}{\Gamma_{\downarrow}}
$$
For this to be true thermal bath, we must have this steady-state population ratio to be exactly the Boltzmann distribution. Therefore, the jump rates are now fixed nicely as,
$$
	\frac{\Gamma_{\uparrow}}{\Gamma_{\downarrow}} = \exp\left( - \frac{E}{k_{B}T} \right)
$$
(reminder, $E$ is the energy gap of this TLS)

This is called the **Kubo-Martin-Schwinger (KMS)** condition for detailed balance. As long as we have $T>0$, the downward rate $\Gamma_{\downarrow}$ is always higher than the upward rate $\Gamma_{\uparrow}$. This makes sense - as the downward transition can happen due to both stimulated *and* spontaneous emission.

---
## Connections & Derivations
- **Prerequisites:** [[ ]]
- **Follow-up:** [[ ]]
- **Relevant Literature:** 
