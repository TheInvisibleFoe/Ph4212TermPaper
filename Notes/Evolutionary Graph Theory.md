We define games on networks, with some structure rather than just well mixed populations. Let us review how to construct such a graph.
## Graph
- A network is completely specified by the weight adjacency matrix,  $W = [w_{ij}]$, which is also a **stochastic matrix**.
- $W = [w_{ij}]$ is an $N \times N$ stochastic matrix where $w_{ij}$ is the probability that the $j^{th}$ member of the network is replaced by the $i^{th}$ member.
- $w_{ij} = 0$ if there is no directed edge from i to j.
- $W$ is a symmetric matrix if the Graph is a digraph.
- Since $W$ is a stochastic matrix , $\sum w_{ij} = 1$.

# Fixation probability of game in a network
