---
title: title
date:
tags:
  - 
---
# Sequence Space
We can define something called a sequence space. Consider such a space where the proteins are arranged in such a way that the nearest neighbours differ by a single amino acid. We can then represent this using a $n$bit sequence. Consider the case of genes. Represent all the same length nucleotides($L$) in such a way that they differ from the nearest neighbour in only position. If arranged on a lattice, we shall get $4^L$ many points. For our ease, we can convert this to a binary sequence of $2^{2L}$. The distance metric on these spaces is called the **Hamming Metric** or the **Manhattan Metric**. It basically is the number of places where two binary sequences differ.![[Pasted image 20260502051009.png]]
# Fitness Landscapes

Consider a $L$ dimensional sequence space with $2^L$ points in them. Then we can assign each genome *fitness* value. Thus we get the **Fitness Landscape** of the $L$ length genome to be in $L+1$ dimensions. The evolutionary process traverses this landscape to reach the peak. This fitness landscape represents the mapping from genotype to phenotype. **One generally defines the quasispecies equation in the context of the fitness landscape**. See [[Rate Equations]].

# Mutation matrix for point mutations

One can easily model point mutations in binary sequences. Suppose for any position, the probability of mutation is given by $u$ and the probability of the sequence getting copied correctly is given by $1-u$. Then denote the Hamming distance between $i,j$ as $h_{ij}$. The mutation matrix elements are then given by,
$$
	q_{ij}= u^{h_{ij}}(1-u)^{L-h_{ij}}
$$
- Point mutations are changing from base to the other, the sequence length remains constant.
- Insertions and deletions are not allowed, since then the sequence space gets changed.

# Adaption 
Adaption basically means that the species can find the maxima of the fitness landscape and travel there, on its evolutionary trajectory. *It is able to localize near the peak*. The jumping from one peak to the other is dictated by the mutation rate $u$. For low mutation rates, we do not see the species traversing the entire landscape. For higher mutation rates, the species is able to change its genomic sequence to travel to the peak. However, as one increases the mutation rate is more and more likely that the species can mutate back to a lower fitness. Thus there is a critical mutation threshold $u_{c}$. This is called the **error threshold**. This is the threhold below which the fittest species cannot survive can be calculated for a very simple model.
- Consider a population with genome length $L$. Consider only the all $0$ binary string to the fittest variant or the master variant with fitness $f_{0}$.
- Consider all other variants to have fitness $1$. 
- Assume that $f_{0}>1$. 
- Consider the rate of mutation of any $0$ to a $1$ is u. Then the dupliction rate of the master sequence is given by $(1-u)^L$. 
- **Assume that there is no back mutation from a non master variant to the master variant.**
The mutation matrix is easily given by ,
$$
	Q = \begin{bmatrix}
q = (1-u)^L & 1-q \\
0 & 1
\end{bmatrix}
$$
Then the master equation is written as 
$$
	\begin{align}
		\dot{x}_{0}  &=x_{0}(f_{0}q-\phi) \\
		\dot{x}_{1} &= x_{0}f_{0}(1-q)+x_{1} - \phi x_{1}
	\end{align}
$$
The average frequency is then given by $\phi= f_{0} x_{0} +x_{1}$. The one variable equation can be written as ,
$$
	\dot{x}_{0}=x_{0}[f_{0} q-1-x_{0}(f_{0}-1)]
$$
Suppose that $f_{0}q <1$, then the frequency $f_{0}$ shall converge to $0$, meaning that the fittest variant cannot survive. Thus provided $f_{0} q>1$, the fixed point of this equation is then given by,
 $$
 x^*  = \frac{f_{0}q-1}{f_{0}-1}
 $$
	  Thus we need $f_{0} q >1$. We can get the error rate threshold by taking the $\log$ of this inequality, and assuming small mutation rates $u\ll {1}$,
	  $$
		\begin{align}
			&\log f_{0} > -L \log(1-u)  \\
		  \approx & u < \frac{\log f_{0}}{L}
		\end{align}
	  $$
	  Since log is a slowly growing function, under the assumption that $f_{0}$ is neither too large nor too small, we can approximate $\log f_{0} \approx 1$.
  
![[Pasted image 20260502231035.png]]