---
title: Maser
date: 2026-04-14
lastmod: 2026-04-14
tags:
  - concept
  - status/1
  - maser
  - optics
  - quantum
aliases: []
publish: true
anki-status: status/1
anki-last-sync:
---
> [!summary] TL;DR
> MASER is an abbreviation for Microwave Amplification by Stimulated Emission of Radiation. This note will lay out the theory (based on relevant phenomena) and perhaps some instrumental realizations of the MASER.

# What does a Maser do?
The Maser is a device that produces *coherent electromagnetic waves in the Microwave regime* through *amplification by stimulated emission.

# Operation of a Maser
The Maser operates on the exact same fundamental quantum mechanical principles as a laser, except the fact that it emits in the microwave region of the electromagnetic spectrum rather than the optical or infrared regions.

> [!NOTE] Invention of the Maser
> Invented by Charles Townes, Mikolay Basov, and Alexander Prokhorov in the 1950s, the Maser provided the critical proof of concept for macroscopic quantum oscillators.

## Core Concepts: Rate Equations and Population Inversion
To understand how an electromagnetic signal can be amplified via stimulated emission, we must look at the interaction(s) between an electromagnetic field and a quantized system.

Consider a two-level system to begin with. Let the lower and higher energy states have the energy eigenvalues $E_{1}$ and $E_{2}$ respectively, with $E_{2} > E_{1}$. The energy-gap between them is give by $\Delta E = E_{2}-E_{1} = \hbar \omega$, where $\hbar$ is the reduced Planck's constant, and $\omega$ is some frequency.

When this system is in thermal equilibrium at some temperature $T$, the relative populations $N_{1}$ and $N_{2}$ in the lower and upper states respectively are governed by the Boltzmann distribution:

$$
\begin{equation}
	\frac{N_{2}}{N_{1}} = \exp\left( - \frac{\hbar \omega}{k_{B}T} \right)
\end{equation}
$$

^eq:1

Since the exponential term always satisfies $\exp\left( -\frac{\hbar \omega}{k_{B}T} \right) < 1$, we have a situation where the lower state is always more populated than higher state (i.e. $N_{1} > N_{2}$) under equilibrium conditions.

Now, the dynamics of the upper state population is crucial to the interaction of a resonant radiation field of spectral energy density $\rho(\omega)$ is described by the equation:

$$
\begin{equation}
	\frac{dN_{2}}{dt} = -A_{21}N_{2} - B_{21}\rho(\omega)N_{2} + B_{12}\rho(\omega)N_{1}
\end{equation}
$$

^eq:einsteinRate

Here, we have:
- $A_{21}$: Called the "Einstein Coefficient for [[Spontaneous Emission]]".
- $B_{21}$: Coefficient for [[Stimulated Emission]]
- $B_{12}$: Coefficient for Stimulated Absorption.
Note that in the two-level system the probabilities of absorption and stimulated emission are symmetric, i.e. $B_{12} = B_{21} = B$. Thus, excluding the spontaneous emission contribution we have:

$$
\begin{equation}
	\left( \frac{d \text{Photons}}{dt} \right)_{\text{stim}} \propto B \rho(\omega)(N_{2}-N_{1}) 
\end{equation}
$$

^eq:stimEmission

Notice that for the signal to be amplified rather than attenuated as it passes through this medium, the net stimulated emission rate must be positive. This can only happen if we have $N_{2}>N_{1}$ - a **non-equilibrium** state called a *population inversion*.

> [!NOTE] Why is Stimulated Emission required?
> Note that if a two-level system in the excited state decays via stimulated emission due to coupling with a photon - the emitted radiation from the decay will be an **exact copy of the original photon**. This means that the emitted photon will have the same phase, frequency, polarization, and direction of propagation.
> Obviously, all of this is essential to the formation of the coherent output of a laser-like device and on top of that it results in an amplification of the source photon if the system is in population inversion.

### The Impossibility of the Two-Level Continuous Inversion
Quantum Optics predicts a fundamental constraint: **It is not possible to achieve a steady-state population inversion in a simple two-level atomic system using continuous, incoherent pumping**. This is a problem, as we would need to *already* have a coherent source to be able to pump the two-level system into a suitable steady-state population inversion.

To understand why this is so, we consider a single atom that acts like a two-level system. If we use an external incoherent energy source to pump the atomic system, the population of the excited state will initially rise as expected. However, as the excited state becomes populated, the pumping radiation will simultaneously begin inducing stimulated emission - which will drive the system back to ground state again. The cross-sections of both absorption and stimulated emission events are identical, and thus the system will necessarily eventually reach a state of optical saturation - the populations in both the excited state and the ground state becomes equal. This makes a two-level maser a physical impossibility.

### Three-Level Architecture
To circumvent the limitation of optical saturation, the system must incorporate *at least* one more energy level. Now, we have three non-degenerate states:
- A ground state
- An excited state
- **An intermediate, metastable state**

The achievement of population inversion in such a three-level system relies on a sequence of transition rates between these states:
1. An external energy source (hereafter, the pump) strongly drives the population from the ground state to the uppermost excited state.
2. Once in the pump state, the system undergoes a rapid, *non-radiative* relaxation process to the intermediate metastable state. The critical feature of the metastable state is that the spontaneous decay rate back to the ground is *relatively low*.
3. Since the system enters the metastable state at a faster rate than it can leave it, population accumulates in the metastable state. At sufficient pumping strength, the population of the metastable state rapidly exceeds the population in the ground state and thus gives us steady-state population inversion between the intermediate and ground states.

Once we have achieved the population inversion, any external photon possessing an energy that exactly matches the gap between the intermediate and the ground state will trigger a cascade of stimulated emission. If such a system were to be closed inside a [[Resonant Cavity]], the emitted photons would bounce back-and-forth through the medium and stimulate further emission on each pass-through. This feedback loop generates an intense, coherent, macroscopic radiation field - which is exactly what the maser produces.

### Derivation to demonstrate the working principle
Let us define three energy levels: $E_{1}<E_{2}<E_{3}$. The total number of atoms in a particular state is given by $N_{i}$, where $i$ is the index for that level. Note that we fix the number of atoms available as:
$$
N = N_{1}+N_{2}+N_{3}
$$

#### Defining the transition rates
There are two distinct types of transitions:
1. **Stimulated Transitions** (denoted by $W$ here): These are stimulated by external electromagnetic fields. $W_{p}$ is the pumping rate between the levels $1$ and $3$. Since stimulated emission and absorption probabilities are symmetric, we have $W_{13} = W_{31} = W_{p}$. Let $W_{s}$ denote the signal transition rate between levels $1$ and $2$.
2. **Intrinsic Relaxation Rates** (denoted here with $\Gamma$): These are the transition in the system that aim to restore thermal equilibrium. In a solid-state system at microwave frequencies, spontaneous photon emission (Given by the Einstein $A$ coefficient, which scales as $\omega^3$, $\omega$ being the frequency associated with the transition) is for all practical purposes nearly zero. Therefore, these $\Gamma_{ij}$ relaxation process are almost entirely non-radiative in character and can be seen as processes that involve the absorption or emission of photons.

#### Setting up rate equations
We need to track the time evolution of the populations $\{N_{i}\}$. Since we have rates of transitions, the most direct way to do this would be to formulate a system of coupled differential equations:

$$
\begin{align}
	\frac{dN_{3}}{dt} =  W_{p}(N_{1} - N_{3}) - (\Gamma_{32} + \Gamma_{31}) N_{3} + \Gamma_{23}N_{2} + \Gamma_{13}N_{1}\\ \\
	\frac{dN_{2}}{dt} = \Gamma_{32}N_{3} - (\Gamma_{23}+\Gamma_{21})N_{2}+\Gamma_{12}N_{1}-W_{s}(N_{2}-N_{1}) \\
	\frac{dN_{1}}{dt} = W_{p}(N_{3}-N_{1})+\Gamma_{31}N_{3}+\Gamma_{21}N_{2}-(\Gamma_{13}+\Gamma_{12})N_{1}+W_{s}(N_{2}-N_{1})
\end{align}
$$

^eq:temp

Remember that we have the constraint of $N = N_{1}+N_{2}+N_{3}$, and thus one of the equations is redundant.

#### Steady-State and Pump Saturation
Let us evaluate the system at steady-state (i.e. assume $\frac{dN_{i}}{dt} = 0 \forall i$). Let us also assume that the incoming microwave signal is initially entirely negligible (i.e. $W_{s} = 0$).

Now, we apply a *strong* pump field - this means that the stimulated pump rate is much greater than the natural relaxation rates ($W_{p}\gg \Gamma_{ij}$). Notice that the only way that the $N_{3}$ rate equation would ever be balanced under both of these assumption would be if $N_{1} \approx M_{3}$ and thus the first term on the RHS vanishes (and takes along the large $W_{p}$ factor). Let us define $N_{1} \approx N_{3} \equiv n$.

Substituting these conditions into the rate equation for $N_{2}$, we get:
$$
0 = \Gamma_{32}n - (\Gamma_{23}+\Gamma_{21})N_{2} + \Gamma_{12}n
$$

Rearranging,
$$
N_{2} = n \frac{\Gamma_{32}+\Gamma_{12}}{\Gamma_{21}+\Gamma_{23}}
$$

#### Condition for Population Inversion
The aim is to amplify a signal across the $E_{2}\to E_{1}$ transition in this system. The necessary condition for this stimulated emission to outpace absorption is $\Delta N = N_{2}-N_{1} > 0$ (the usual population inversion condition). Plugging in the expressions derived above,
$$
\Delta N = N_{2} - n = n\left[ \frac{\Gamma_{23}+\Gamma_{12}}{\Gamma_{21}+\Gamma_{23}} - 1 \right]
$$

This simplifies to:
$$
\Delta N = n\left[ \frac{\Gamma_{32}+\Gamma_{12}-\Gamma_{21}-\Gamma_{23}}{\Gamma_{21}+\Gamma_{23}} \right]
$$

For the $\Delta N>0$ condition to be satified, we must have:
$$
\Gamma_{32}+\Gamma_{12} > \Gamma_{21}+\Gamma_{23} \tag{$1$}
$$


^66b5a7

#### What physically satisfies the population inversion condition?
To proceed further, let us consider this system without any signal or pumping, at thermal equilibrium. Applying detailed balance there:
$$
\Gamma_{ij}N_{i}^{eq} = \Gamma_{ji}N_{j}^{eq}
$$

Where $N_{i}^{eq}$ represents the equilibrium population of the $i$th level.
We know that this equilibrium population is proportional to the Boltzmann factor:
$$
N_{i}^{eq} \propto \exp\left( -\frac{E_{i}}{k_{B}T} \right)
$$

This essentially means that the probability of an upward transition (via, say, the absorption of a phonon) is much less probable as compared to the probability of a downward transition.
We have:
$$
\begin{align}
	\Gamma_{12} = \Gamma_{21} \exp\left( -\frac{\hbar \omega_{21}}{k_{B}T} \right) \\
	\Gamma_{23} = \Gamma_{32} \exp\left( -\frac{\hbar \omega_{32}}{k_{B}T} \right)
\end{align}
$$

^eq:temp

which follow directly from the last equation. Here, as before, $\omega_{ij}$ refers to the frequency associated with the transition $i\to j$ or the other way. Putting these thermodynamic constraints back into the original [[#^66b5a7]] :
$$
\Gamma_{32}+\Gamma_{21}\exp\left( -\frac{\hbar \omega_{21}}{k_{B}T} \right) > \Gamma_{21}+\Gamma_{32}\exp\left( -\frac{\hbar \omega_{32}}{k_{B}T} \right)
$$

Rearranging,
$$
\Gamma_{32}\left[ 1-\exp\left( -\frac{\hbar \omega_{32}}{k_{B}T} \right) \right] > \Gamma_{21}\left[ 1-\exp\left( -\frac{\hbar \omega_{21}}{k_{B}T} \right) \right]
$$

This is the exact condition required. At sufficiently high temperatures, we could do a first order approximation by using $\exp (-x) \approx 1 - x$. Then, we get,
$$
\Gamma_{32}\omega_{32}>\Gamma_{21}\omega_{21}
$$

This approximate inequality condition is easy to interpret - It requires that the relaxation rate of $3\to2$ must be significantly faster than the relaxation rate of $2\to 1$. Once this is satisfied, any incident photon that is resonant with $\hbar \omega_{21}$ will trigger an avalanche of stimulated emission (in a resonator cavity, of course).

---
## Connections & Derivations
- **Prerequisites:** [[ ]]
- **Follow-up:** [[ ]]
- **Relevant Literature:** 
