# Generative Network Models

This notebook implements and analyzes classic **generative models** for complex networks. These models aim to replicate key properties of real-world networks, such as small-world behavior, scale-free distributions, and clustering dynamics.

##  Overview

This notebook covers the following models:

- **Watts-Strogatz model** — Small-world networks
- **Barabási–Albert model** — Scale-free networks (preferential attachment)
- **Power-law fitting** — Statistical validation of scale-free behavior
- **Clustering & degree dynamics** — Additional empirical insights

Each section implements the model from scratch, includes visualization and analysis, and tests its alignment with theoretical properties.

---

##  Requirements

The notebook uses the following Python packages:

- `networkx`
- `matplotlib`
- `numpy`
- `scipy`
- `tqdm`

---

##  Task Breakdown

###  Task 1: Watts-Strogatz Model

- **Goal**: Simulate a small-world network using rewiring on a ring lattice.
- **Implementation**:
  - `ring_lattice(n, k)`: Generates a regular ring lattice.
  - `rewire(G, node, k, p)`: Rewires a given node’s edges with probability `p`.
  - `watts_strogatz_graph(n, k, p)`: Full small-world graph generator.

 *Observation*: The model transitions from regular (p ≈ 0) to random (p ≈ 1) networks.

---

###  Task 2: Average Path Length in WS Model

- **Goal**: Track how average shortest path length changes as a function of rewiring.
- **Implementation**:
  - `smallworld_path_len(n, k, p)`: Computes the average path length per rewiring step.

 *Theory Check*:
- At p ≈ 0: `L ~ N/2k` (regular)
- At p ≈ 1: `L ~ log(N)/log(k)` (random)

---

###  Task 3: Barabási–Albert Model (Preferential Attachment)

- **Goal**: Model scale-free networks with power-law degree distribution.
- **Implementation**:
  - `attach(G, targets)`: Connects a new node preferentially.
  - `barabasi_albert_graph(n, m)`: Builds the BA graph from scratch.

 *Observation*: Degree distribution follows power-law — many low-degree, few high-degree nodes.

---

###  Task 4: Power-law Distribution Fitting

- **Goal**: Fit power-law to degree distribution using MLE and assess fit.
- **Implementation**:
  - `power_law_cdf(k, alpha, kmin)`
  - `mle_power_law_params(data, kmin)`
  - `estimate_power_law(data)`

 *Metric*: KS-statistic is used to test the goodness of fit.

---

###  Task 5: Clustering Coefficient Dynamics

- **Goal**: Analyze how clustering coefficient evolves during graph growth.
- **Implementation**:
  - `generate_clustering_coef(n, m)`: Tracks clustering as nodes are added.

 *Insight*: Clustering decreases as the network grows.

---

###  Task 6: Degree Dynamics of Initial Nodes

- **Goal**: Observe how degrees of early nodes evolve in the BA model.
- **Implementation**:
  - `generate_degree_dynamics(n, m)`: Plots degree over time for initial nodes.

 *Result*: Early nodes gain higher degrees — "the rich get richer."
