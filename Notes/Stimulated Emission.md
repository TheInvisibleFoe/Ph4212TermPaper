---
title: Stimulated Emission
date: 2026-04-15
lastmod: 2026-04-15
tags:
  - concept
  - status/1
  - quantum
  - qft
  - einstein
  - optics
aliases: []
publish: true
anki-status: status/1
anki-last-sync:
---
> [!summary] TL;DR
> Stimulated Emission is an interesting phenomena, where a system decays from an energetic state to a less energetic state due to an external photon coupling to it. The crucial phenomena is that the photon radiated from the system due to this event is *identical to the original external photon* in all ways - it has the same polarization, phase, direction of propagation, etc.

# Semiclassical treatment
Let us treat the atom (imagine the atom to be the system here, it could be anything else like a crystalline defect, say) as a fully quantized system. On the other hand, let us treat the interacting electromagnetic field classically as an oscillating electric field.

## The Interaction Hamiltonian
Let the the eigenstates of the system be $\ket{1}$ (with energy $E_{1}$) and $\ket{2}$ (with energy $E_{2}$). The unperturbed Hamiltonian is labelled $H_{0}$, such that,
$$
	H_{0} \ket{n} = E_{n} \ket{n} 
$$
The energy of the transition is given by: $\hbar \omega_{21}=E_{2}-E_{1}$.

We now expose this atom to a monochromatic, linearly polarized electromagnetic wave. We make an assumption of the *wavelength of the light being much larger than the atomic radius*, and thus the spatial variation of the electric field across the atom is negligible. Formally, this is known as the **dipole approximation**.

Classically, such an electric field is given by,
$$
	\vec{E}(t) = \vec{E_{0}} \cos(\omega t)
$$
(with all the terms having the usual meaning)

The interaction Hamiltonian $H'(t)$ is the energy of the atomic electric dipole,
$$
	\vec{d} = - e \vec{r}
$$
In this field, we have:
$$
	H'(t) = - \vec{d} \cdot \vec{E}(t) = e \vec{r} \cdot \vec{E}_{0} \cos(\omega t)
$$
^eq:interaction:hamiltonian

The transition dipole matrix element between the two available states can be defined as,
$$
\mu_{21} = \bra{2}-e\vec{r}\ket{1}  
$$

^eq:label

### An aside on how the dipole approximation helps apply perturbation

Why do we need this "dipole matrix element"? In the unperturbed Hamitonian, the two states of the system are orthogonal to each other and do not "mix". To force the transition, we introduced the perturbing Hamiltonian $H'(t)$. **Time-Dependent Perturbation Theory** (TDPT) tells us that the rate at which probability "flows" from the state $\ket{1}$ to $\ket{2}$ (say) is dictated entirely by the off-diagonal matrix elements of the perturbation operator in the basis of the unperturbed states. Thus, we need to evaluate the following integral,
$$
\bra{2} H'(t) \ket{1} = \int \psi^*_{2}(\vec{r})(-e\vec{r} \cdot \vec{E}(t))\psi_{1}(\vec{r}) d^3r
$$

^eq:off_diag_TDPT

Since the macroscopic electric field is considered uniform across the time atomic volume due to our previous assumptions, we can pull it out of the integral,
$$
\bra{2} H'(t)\ket{1} = \vec{E}(t) \cdot \int \psi_{2}^*(\vec{r})(-e\vec{r})\psi_{1} d^3r = \vec{E}(t) \cdot \vec{\mu}_{21}
$$

^eq:req_dipole_matrix

This shows us why this particular quantity is essential in this approximation - it is the fundamental coupling constant between the specific atomic transition and the external field.

Note that also outright gives us an important selection rule that applies here. Notice that the integral for $\vec{\mu}_{21}$ is only non-zero if the integrand is even. $\vec{r}$ is odd of course, which means that $\psi_{2}^*\psi_{1}$ must be odd too, which in turn implies that $\psi_{1}$ and $\psi_{2}$ must be of opposite parity.

In terms of orbitals, it can be though of as a $s \to p$ transition due to photons being valid, while an $s \to d$ transition is invalid due to parity rules stated above. The former is called a **dipole-allowed** transition, and the latter is called **dipole-forbidden**

### Coming back to TDPT application to the problem
Now, the state of the system $\ket{\psi(t)}$ evolves as a superposition of the unperturbed eigenstates of the system,
$$
\ket{\psi(t)}  = c_{1}(t)e^{ -iE_{1}t/\hbar } + c_{2}(t)e^{ -iE_{2}t/\hbar }
$$

^eq:state_time

If we plug this state into the time-dependent Schrodinger Equation,
$$
	i \hbar \frac{d}{dt} \ket{\psi} = (H_{0}+H')\ket{\psi} 
$$
We will get coupled differential equations for the probability amplitudes $c_{1}(t)$ and $c_{2}(t)$.

Now, let us first assume the atom to be in the lower state initially (i.e. $c_{1}(0)=1,c_{2}(0)=0$) the first-order TDPT correction gives us a rate of change of the amplitude in the upper state to get,
$$
	\frac{dc_{2}}{dt} = \frac{1}{i\hbar} \bra{2} H'(t) \ket{1} e^{ i\omega_{21}t }
$$
We substitute in the interaction Hamiltonian and expanding the cosine term there to combine the exponentials, we arrive at the crucial expression:
$$
\frac{dc_{2}}{dt} = - \frac{\vec{\mu}_{21} \cdot \vec{E}_{0}}{2i\hbar} (e^{ i(\omega_{21}+\omega)t } + e^{ i(\omega_{21}-\omega)t }) 
$$

^eq:rate_of_change_amp

We can see that there is a rapidly oscillating term with $\omega_{21}+\omega$, and a slow oscillating term $\omega_{21}-\omega$ (assuming that our external field is near resonance with the energy gap of the system). This can be easily identified as a lock-in-esque situation, and this can lead us to the next obvious approximation.

### The Rotating Wave Approximation (RWA)
The first exponential term, with the fast oscillation, essentially averages to 0 over a meaningful integration time. The second term survives such an integration.

So, on integration from $t=0$ to some time $t$, we can write:
$$
c_{2}(t) \approx \frac{\vec{\mu}_{21}\cdot\vec{E}_{0}}{2\hbar}\left[ \frac{e^{ i(\omega_{21}-\omega)t } - 1}{\omega_{21}-\omega} \right]
$$

^eq:RWA_amp

This is called the **Rotating-Wave Approximation**

The probability of finding the atom in the excited state $\ket{2}$ after a time $t$ is given by $P_{1\to 2}(t) = |c_{2}(t)|^2$:
$$
P_{1 \to 2}(t) = \frac{|\vec{\mu}_{21}\cdot\vec{E}_{0}|^2}{\hbar^2} \frac{\sin^2\left( \frac{(\omega_{21}-\omega)t}{2} \right)}{(\omega_{21}-\omega)^2}
$$

^eq:prob_in_2

But this tells us about stimulated absorption, and *not* stimulated emission. To get to the associated probabilities for the $2 \to 1$ transition, we simply run the exact same calculation but with the initial conditions swapped (i.e. $c_{2}(t) = 1, c_{1}(t)=0$), and the sign on the frequency flipped (i.e. $\omega_{12}=\omega_{21}$). Using RWA there, we keep the *other* half of the cosine (the $-i\omega t$ part).

Note that the dipole transition matrix elements are Hermitian, as the position operator is Hermitian. As the resulting probabilities of the transitions depend only on $|\mu|^2$, we can see,
$$
	P_{1 \to 2}(t) = P_{2 \to 1}(t)
$$
i.e. the transition probabilities for excitation and decay are exactly the same. This implies that the transition occurs exactly in phase with the oscillating electric field - as if the electric field is "shaking" the atom from excited to ground state and vice-versa.


> [!NOTE] Einstein $B$ coefficients
> Note that the entire calculation done above was based on a coherent driving electromagnetic wave. If we were to do this for thermal radiation fields interacting with the system, we would need to integrate with the spectral energy density $\rho(\omega)$ of the radiation field instead. Following through with this will lead to an expression for the Einstein $B$ coefficients, as they are described in [[Spontaneous Emission]]. This derivation is skipped here, for now.

It might also be of interest to note that [[Spontaneous Emission]] still occurs when $\vec{E}_{0}=0$ , i.e. in vacuum. In a fully quantum mechanical treatment, where the electromagnetic field is also considered to be quantized, the vacuum fluctuation contribution keeps the emission transition rate non-zero even when there are no photons present. 


---
## Connections & Derivations
- **Prerequisites:** [[ ]]
- **Follow-up:** [[ ]]
- **Relevant Literature:** 
