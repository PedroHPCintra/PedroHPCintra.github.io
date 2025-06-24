---
layout: sub-page_pt-br
---

# Pair-Approximation Logistic Growth

## System Description

We have a lattice where each site can be:
- Empty (0) 
- Occupied (1)

**Reactions:**
1. **Birth**: Occupied sites produce offspring at rate $b$, dispersed randomly to $z$ neighboring sites
2. **Crowding death**: Occupied sites die at rate $1 + \delta \times$(number of occupied neighbors)
3. **Natural death**: Occupied sites die independently at rate $\gamma$

![prob-eq](https://pedrohpcintra.github.io/assets/img/class_notes/Neighborhood.png)

## Master Equation

Let $P(\mathbf{n}, t)$ be the probability of configuration $\mathbf{n} = (n_1, n_2, \ldots, n_N)$ at time $t$, where $n_i \in \{0,1\}$ is the state of site $i$.

$$\frac{dP(\mathbf{n}, t)}{dt} = \sum_{\mathbf{n}'} [W(\mathbf{n}|\mathbf{n}') P(\mathbf{n}', t) - W(\mathbf{n}'|\mathbf{n}) P(\mathbf{n}, t)]$$

**Transition rates $W(\mathbf{n}'|\mathbf{n})$:**

1. **Birth transition** ($0 \to 1$ at site $i$):
   $$
   W(\mathbf{n} + \mathbf{e}_i|\mathbf{n}) = b \sum_{j \in \mathcal{N}(i)} n_j \cdot \frac{1}{z} \quad \text{if } n_i = 1
   $$

2. **Crowding death** ($1 \to 0$ at site $i$):
   $$
   W(\mathbf{n} - \mathbf{e}_i|\mathbf{n}) = \left(1 + \delta \sum_{j \in \mathcal{N}(i)} n_j\right) n_i
   $$

3. **Natural death** ($1 \to 0$ at site $i$):
   $$
   W(\mathbf{n} - \mathbf{e}_i|\mathbf{n}) = \gamma n_i
   $$

where $\mathcal{N}(i)$ is the neighborhood of site $i$ and $\mathbf{e}_i$ is the unit vector for site $i$.

## Moment Equations

Taking expectations and defining:
- $\rho_1 = \langle n_i \rangle$ (density of occupied sites)
- $\rho_{11} = \langle n_i n_j \rangle$ for neighbors $i,j$ (density of occupied pairs)
- $\rho_{10} = \langle n_i (1-n_j) \rangle$ for neighbors $i,j$ (density of 10 pairs)

From the master equation:

$$\frac{d\rho_1}{dt} = \langle \frac{dn_i}{dt} \rangle$$

**Birth contribution:**

$$
\frac{b}{z} \sum_{j \in \mathcal{N}(i)} \langle n_j \rangle = \frac{b}{z} \cdot z \cdot \rho_0 \cdot P(\text{neighbor is occupied | site i is empty})
$$

Using conditional probabilities: $P(\text{neighbor is occupied | site i empty}) = q_{1|0}$

So the birth rate for empty sites is: $b q_{1|0} \rho_0 = b q_{1|0} (1-\rho_1)$

**Crowding death contribution:**
$$
-\left \langle \left(1 + \delta \sum_{j \in \mathcal{N}(i)} n_j\right) n_i \right \rangle = -(1 + \delta z q_{1|1})\rho_1
$$

**Natural death contribution:**
$$-\gamma \langle n_i \rangle = -\gamma \rho_1$$

Therefore:
$$\boxed{\frac{d\rho_1}{dt} = bq_{1|0}(1-\rho_1) - (1 + \delta z q_{1|1} + \gamma)\rho_1}$$

## Pair Equation Derivation

For the pair density $\rho_{11}$:

$$\frac{1}{2}\frac{d\rho_{11}}{dt} = \left \langle \frac{d(n_i n_j)}{dt} \right \rangle \text{ for neighbors } i,j$$

**Birth contributions:**
Each occupied site produces offspring at rate $b$, sending it to one of $z$ neighbors with equal probability $1/z$.

For an 11 pair $(i,j)$ to be created by birth:
- An occupied neighbor $k \in \mathcal{N}(i), k \neq j$ gives birth to empty site $i$ (probability $1/z$ per birth event)
- An occupied neighbor $k \in \mathcal{N}(j), k \neq i$ gives birth to empty site $j$ (probability $1/z$ per birth event)

The rate of creating 11 pairs from 10 pairs is:
$b \cdot \frac{1}{z} \cdot (z-1) \cdot \rho_{10} \cdot P(\text{other neighbors occupied | in 10 pair})$

This simplifies to: $b[1 + (z-1)q_{1|0}]\rho_{10}$

**Death contributions:**
Each site in an 11 pair dies at rate $(1 + \delta \times \text{occupied neighbors} + \gamma)$

For a site in an 11 pair, it has 1 occupied neighbor for sure (its pair partner), plus $(z-1)q_{1|1}$ expected occupied neighbors among the remaining $(z-1)$ neighbors.

Total death rate: $(1 + \delta[1 + (z-1)q_{1|1}] + \gamma)\rho_{11}$

$$\frac{1}{2}\frac{d\rho_{11}}{dt} = \frac{2b(z-1)}{z} \rho_{10} - (1 + \delta[1 + (z-1)q_{1|1}] + \gamma)\rho_{11}$$

Using $q_{1|0} = \rho_{10}/\rho_0 = \rho_{10}/(1-\rho_1)$:

$$\boxed{\frac{1}{2}\frac{d\rho_{11}}{dt} = \frac{b}{z}[1 + (z-1)q_{1|0}]\rho_{10} - (1 + \delta[1 + (z-1)q_{1|1}] + \gamma)\rho_{11}}$$

## Final Pair-Approximation Equations

$$\frac{d\rho_1}{dt} = bq_{1|0}(1-\rho_1) - (1 + \delta z q_{1|1} + \gamma)\rho_1$$

$$\frac{1}{2}\frac{d\rho_{11}}{dt} = \frac{b}{z}[1 + (z-1)q_{1|0}]\rho_{10} - (1 + \delta[1 + (z-1)q_{1|1}] + \gamma)\rho_{11}$$

where:
- $q_{1|0} = \rho_{10}/(1-\rho_1)$
- $q_{1|1} = \rho_{11}/\rho_1$ 
- $\rho_{10} = \rho_1 - \rho_{11}$

---

# Two-Species Competition Model: Pair-Approximation Derivation

## System Description

We have a lattice where each site can be:
- Empty (0) 
- Occupied by species 1 (1)
- Occupied by species 2 (2)

**Parameters for species $i$ ($i = 1,2$):**
- $b_i$: birth rate
- $\gamma_i$: natural death rate  
- $\delta_{ii}$: intraspecific crowding coefficient
- $\delta_{ij}$: interspecific crowding coefficient ($i \neq j$)

**Reactions:**
1. **Birth**: Species $i$ produces offspring at rate $b_i$, dispersed randomly to one of $z$ neighboring sites
2. **Natural death**: Species $i$ dies independently at rate $\gamma_i$
3. **Intraspecific crowding**: Species $i$ dies from crowding with species $i$ neighbors at rate $\delta_{ii} \times$ (number of species $i$ neighbors)
4. **Interspecific crowding**: Species $i$ dies from competition with species $j$ neighbors at rate $\delta_{ij} \times$ (number of species $j$ neighbors)

## State Variables and Notation

**Densities:**
- $\rho_0$: density of empty sites
- $\rho_1$: density of sites occupied by species 1
- $\rho_2$: density of sites occupied by species 2
- $\rho_0 + \rho_1 + \rho_2 = 1$

**Pair densities:**
- $\rho_{ij}$: density of neighboring pairs where first site is type $i$, second is type $j$
- By symmetry: $\rho_{ij} = \rho_{ji}$

**Conditional probabilities:**
- $q_{j|i} = \rho_{ij}/\rho_i$: probability neighbor is type $j$ given focal site is type $i$

## Master Equation

Let $P(\mathbf{n}, t)$ be the probability of configuration $\mathbf{n} = (n_1, n_2, \ldots, n_N)$ at time $t$, where $n_k \in \{0,1,2\}$ is the state of site $k$.

$$\frac{dP(\mathbf{n}, t)}{dt} = \sum_{\mathbf{n}'} [W(\mathbf{n}|\mathbf{n}') P(\mathbf{n}', t) - W(\mathbf{n}'|\mathbf{n}) P(\mathbf{n}, t)]$$

**Transition rates $W(\mathbf{n}'|\mathbf{n})$:**

1. **Birth transition** ($0 \to i$ at site $k$):
   $$W(\mathbf{n} + i\mathbf{e}_k|\mathbf{n}) = b_i \sum_{j \in \mathcal{N}(k)} \mathbf{1}_{n_j = i} \cdot \frac{1}{z} \quad \text{if } n_k = 0$$

2. **Death transitions** ($i \to 0$ at site $k$):
   $$W(\mathbf{n} - i\mathbf{e}_k|\mathbf{n}) = \left[\gamma_i + \delta_{ii} \sum_{j \in \mathcal{N}(k)} \mathbf{1}_{n_j = i} + \delta_{i\bar{i}} \sum_{j \in \mathcal{N}(k)} \mathbf{1}_{n_j = \bar{i}}\right] \mathbf{1}_{n_k = i}$$

where $\bar{i}$ denotes the other species ($\bar{1} = 2$, $\bar{2} = 1$).

## Single-Species Density Equations

For species 1 density:

$$\frac{d\rho_1}{dt} = \left \langle \frac{d\sum_k \mathbf{1}_{n_k = 1}}{dt} \right \rangle$$

**Birth contribution:**
Each empty site receives species 1 offspring at rate:
$$b_1 \sum_{j \in \mathcal{N}(k)} \mathbf{1}_{n_j = 1} \cdot \frac{1}{z} = \frac{b_1}{z} \times z \times P(\text{neighbor is 1 | site is 0}) = b_1 q_{1|0}$$

Total birth rate: $b_1 q_{1|0} \rho_0 = b_1 q_{1|0}(1 - \rho_1 - \rho_2)$

**Death contributions:**
- Natural death: $\gamma_1 \rho_1$
- Intraspecific crowding: $\delta_{11} z q_{1|1} \rho_1$  
- Interspecific crowding: $\delta_{12} z q_{2|1} \rho_1$

Therefore:
$$\boxed{\frac{d\rho_1}{dt} = b_1 q_{1|0}(1 - \rho_1 - \rho_2) - (\gamma_1 + \delta_{11} z q_{1|1} + \delta_{12} z q_{2|1})\rho_1}$$

By symmetry, for species 2:
$$\boxed{\frac{d\rho_2}{dt} = b_2 q_{2|0}(1 - \rho_1 - \rho_2) - (\gamma_2 + \delta_{22} z q_{2|2} + \delta_{21} z q_{1|2})\rho_2}$$

## Pair Density Equations

We need equations for all pair types: $\rho_{11}$, $\rho_{22}$, $\rho_{12}$, $\rho_{01}$, $\rho_{02}$

### Intraspecific pairs: $\rho_{11}$

$$\frac{1}{2}\frac{d\rho_{11}}{dt} = \text{Birth rate creating 11 pairs} - \text{Death rate destroying 11 pairs}$$

**Birth contributions:**
- 01 pair becomes 11 when species 1 gives birth to the empty site
- Rate: $b_1 [1 + (z-1)q_{1|0}] \rho_{01}$

**Death contributions:**
Each site in 11 pair dies at rate:
$$\gamma_1 + \delta_{11}[1 + (z-1)q_{1|1}] + \delta_{12}(z-1)q_{2|1}$$

Therefore:
$$\boxed{\frac{1}{2}\frac{d\rho_{11}}{dt} = b_1[1 + (z-1)q_{1|0}]\rho_{01} - [\gamma_1 + \delta_{11}(1 + (z-1)q_{1|1}) + \delta_{12}(z-1)q_{2|1}]\rho_{11}}$$

### Interspecific pairs: $\rho_{12}$

$$\frac{1}{2}\frac{d\rho_{12}}{dt} = \text{Birth rate creating 12 pairs} - \text{Death rate destroying 12 pairs}$$

**Birth contributions:**
- 02 pair becomes 12 when species 1 gives birth to the empty site: $b_1[1 + (z-1)q_{1|0}]\rho_{02}$
- 01 pair becomes 12 when species 2 gives birth to the empty site: $b_2[1 + (z-1)q_{2|0}]\rho_{01}$

**Death contributions:**
- Species 1 site dies: $[\gamma_1 + \delta_{11}(z-1)q_{1|1} + \delta_{12}(1 + (z-1)q_{2|1})]\rho_{12}$
- Species 2 site dies: $[\gamma_2 + \delta_{22}(z-1)q_{2|2} + \delta_{21}(1 + (z-1)q_{1|2})]\rho_{12}$

Therefore:
$$\boxed{\frac{1}{2}\frac{d\rho_{12}}{dt} = b_1[1 + (z-1)q_{1|0}]\rho_{02} + b_2[1 + (z-1)q_{2|0}]\rho_{01} - \text{Death terms}}$$

where Death terms = $[\gamma_1 + \delta_{11}(z-1)q_{1|1} + \delta_{12}(1 + (z-1)q_{2|1})] + [\gamma_2 + \delta_{22}(z-1)q_{2|2} + \delta_{21}(1 + (z-1)q_{1|2})]$

### Similar equations for $\rho_{22}$, $\rho_{01}$, $\rho_{02}$

By symmetry:
$$\boxed{\frac{1}{2}\frac{d\rho_{22}}{dt} = b_2[1 + (z-1)q_{2|0}]\rho_{02} - [\gamma_2 + \delta_{22}(1 + (z-1)q_{2|2}) + \delta_{21}(z-1)q_{1|2}]\rho_{22}}$$

## Constraint Relations

- $\rho_0 + \rho_1 + \rho_2 = 1$
- $\rho_{01} + \rho_{11} + \rho_{21} = z\rho_1$ 
- $\rho_{02} + \rho_{12} + \rho_{22} = z\rho_2$
- $\rho_{00} + \rho_{10} + \rho_{20} = z\rho_0$
- $\rho_{12} = \rho_{21}$ (by symmetry)

This gives us a closed system for competitive dynamics between two species!