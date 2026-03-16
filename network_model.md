---
layout: sub-page
---

# Political polarization in humans

On these notes, we want to study how political polarization arises in a group of humans, from a theoretical perspective. First of all, although I'll use the expression "political polarization", I'm referring to any type of ideological polarization, be it political or not. Perception of polarization is growing in many western democracies, with special attention to the United States [(Lelkes, Y. 2016)](https://doi.org/10.1093/poq/nfw005) (and also Brazil, yey! ([Samuels, D. et al. 2024](https://doi.org/10.1017/lap.2023.38) & [Franco, A. B. 2022](https://doi.org/10.1002/casp.2599))). As shown by Vítor Vasconcelos, Sara Constantino, Astrid Dannenberg and Simon Levin ([Vasconcelos, V. V. et al. 2021](https://doi.org/10.1073/pnas.2102153118)), partisian polarization leading to segregation is detrimental to coordination problems between groups of people. Christopher Tokita, Andrew Guess and Corina Tarnita showed using simulations and data from X[^1] that polarized networks are less efficient in diffusing information due to different beliefs of individuals on each group ([Tokita, C. K. 2021](https://doi.org/10.1073/pnas.2102147118)).

Ok so it becomes pretty clear that polarization is bad :(

On these notes, I want to investigate a model for describing the emergence of polarization in a society of individuals initially unpolarized. From now on I shall divide the concept of polarization into two categories:

> **I) Ideological polarization** refers to polarization of ideas and beliefs by those who live in our society. This may be visually represented by thinking of voters who strongly self-identify politically as left-leaning or right-leaning.
>
> **II) Social polarization** refers to the segregation of individuals from groups in our society. Two groups of friends that share almost no between-group interaction, while having a lot more in-group interaction.

## The model

Individuals have social connections on a network $N$ composed of the set of all connections a individual has, and their strengh $c_{ij}$. The higher the connection strengh between two individuals, the more likely they are to interact. For any two individuals, $c_{ij}$ is drawn from an exponential distribution, given that humans have few close friends compared to the total size of their social friendship network ([Dunbar, R. I. M. 2020](https://doi.org/10.1098/rspa.2020.0446)). Thus

$$
c_{ij} \sim \mathcal{E}\mathrm{xp} \left(\left \langle n_{ij} \right \rangle \right)
$$

where $\left \langle n_{ij} \right \rangle$ is the average total number of connections both individuals have, the higher the number of connections, the steeper the fall of the exponential distribution, resulting in rarer strong connections[^2]. Overall, the social network $N$ of the population is given by a [Barabasi-Albert (BA) network](https://en.wikipedia.org/wiki/Barab%C3%A1si%E2%80%93Albert_model). The BA network is characterized as being scale-free, which means that it has a power-law degree distribution, resulting in a lot of individuals having few friends, while some have large friendship connections.

Each individual $i$ has a belief $b_i^k$ on some topic $k$. Belief is assumed to be continuous, bounded to the interval from -1 to 1. That is $-1 \leq b_i^k \leq 1 \in \mathbb{R}$. The set of beliefs of the individual on a set of topics $\{b\}_i$ constitutes it's ideology and define it's position on the highly dimensional ideology space. That means that for each topic, the opinion (or belief) of an individual on that topic always allows the existance of an opposing view with the same intensity, namely $\forall \, x \in [-1,1]_{\mathbb{R}} \neq 0, \exists \, y \in [-1,1]_{\mathbb{R}} \neq 0$, such that $y = -x$.

Other individuals $j$ whose opinion's $b_j^k$ are close enough to the individual's opinion on the chosen topic for debate are tolarated and are understood as aligned with the individual's opinion on the topic. That is, if $d^k = |b_i^k - b_j^k|$ is the absolute distance between the opinion of the $i$-th and $j$-th individuals, if $d^k \leq \delta$, than both individuals see each other as having close enough aligned positions on the $k$-th topic. In this case, $\delta$ is the tolerance distance, which could in principle be unique to each individual and vary between topics ($\delta \rightarrow \delta_i^k$). Otherwise, if $d^k > \delta$, both individuals will try to convince each other of their opinion.

Each one has an ability to convince others, understood as the combined ability in communication and argumentation on the topic, represented by $o_i$. The persuasion $p_{ij}$ of the $i$-th individual over the $j$-th one is weighted by their connection strengh $c_{ij}$, where the social connection between individuals also represent their trust in each other. Thus

$$
p_{ij} = \gamma o_i + (1 - \gamma) c_{ij}
$$

the intrinsic ability of the individual $i$ to communicate it's view is sampled from a distribution that might represent how well the population overall is able to estabilish good, efficient and non-violent communications. For instance, if $o_i \sim \log \mathcal{N} (\alpha, \beta)$, we are assuming that overall, individuals have poor communications abilities (given the concentration of the distribution over small values for the lognormal), while a few individuals have high abilities to communicate their ideas. On the other side, if $o_i \sim \mathcal{N}(\alpha, \beta)$, we are assuming that the population has an average ability $\alpha$, with most individuals around this mean and the same number of individuals having abilities higher and smaller than $\alpha$, with standard deviation $\beta$.

On top of the ability of convincement, each individual has a convincement threshold, which depends on their belief on the topic. The higher their belief, the harder it is to convince them. Beyond that, the threshold is also influenced by a random variable $\varepsilon$ that represents personal variations and receptiveness to arguments and other views

$$
\tau_i^k = \xi b_i^k + (1 - \xi) \varepsilon_i
$$

where $\varepsilon_i \sim \mathcal{U}(0, 1)$.

These two parameters may be thought of in a parallel way to infectious disease spreading, where $p_{ij}$ is analogous to the infectivity of $i$ to $j$ and $\tau_i$ is the resistence of $i$ to be infected, meaning that $1 - \tau_i$ represents some sort of susceptibility. The higher an individual's belief on a given position of a topic, the more resistant it is to infection by ideas outside it's tolerance range.

If $d^k \leq \delta$, both individuals agree on their opinions and strenghen their connection ($c_{ij}$ increases), at the same time as they reinforce each other's belief's ($b_i^k$ and $b_j^k$ get more extreme). On the other hand, if $d^k > \delta$ a debate happens with the following 4 possible outcomes:

- $i$ convinces $j$ if $p_{ij} > \tau_j$. Under this outcome the opinion of $j$ approaches that of $i$ ($b_j^k$ comes closer to the value of $b_i^k$).
- $j$ convinces $i$ if $p_{ji} > \tau_i$. Under this outcome the opinion of $i$ approaches that of $j$ ($b_i^k$ comes closer to the value of $b_j^k$).
- They both find common ground if $p_{ij} > \tau_j$ and $p_{ji} > \tau_i$. Both opinions move closer to each other ($b_i^k$ and $b_j^k$ get closer together on the ideological space).
- They disagree and can't reach common ground if $p_{ij} < \tau_j$ and $p_{ji} < \tau_i$. On this case, both opinions become more extreme and the connectivity between individuals decreases ($c_{ij}$ decreases).

These four outcomes are represented in the following result matrix

| | $p_{ji} < \tau_i$ | $p_{ji} > \tau_i$ |
|:---:|:---:|:---:|
| $p_{ij} < \tau_j$ | $|b_i^k|$ and $|b_j^k|$ increase while $c_{ij}$ decrease | $b_i^k$ approaches $b_j^k$ |
| $p_{ij} > \tau_j$ | $b_j^k$ approaches $b_i^k$ | $b_i^k$ and $b_j^k$ approach each other |

Opinion formation of the $i$-th individual is also modulated according to social network perception according to https://arxiv.org/pdf/2308.02755

$$
\frac{db_i}{dt} \propto \tanh \left(\frac{a}{N_i} \sum_{k \in V_i}^{N_i} b_j c_{ij}(t) \right)
$$

where $a$ is the strengh of the saturation function $\tanh$ and $V_i$ is the set of vertexes (nodes) connected to the $i$-th vertex. Or in other words, is the social connections of the $i$-th individual.

[^1]: Former Twitter, which was a much better name actually, but who cares
[^2]: I think this might be debatable, maybe there is a better metric for the decay constant of the distribution than $\left \langle n_{ij} \right \rangle$