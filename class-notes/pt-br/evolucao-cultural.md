---
layout: sub-page_pt-br
---

Fitness of learners:

$$
\begin{align}
    W_L = W_0 + D(1 - 2p_e) - C
\end{align}
$$

where $W_0$ is the baseline fitness regardless of the learning strategy, $D$ is the gain in fitness from learning the best strategy for the given environment, $p_e$ is the probability of not learning the best strategy and $C$ is the cost of learning. For imitators we have

$$
\begin{align}
    W_I = W_0 + D\left[2 \frac{(1-m)(1-p_e)(1-q)}{1 - q(1-m)} - 1\right]
\end{align}
$$

where $m$ is the migration probability from one environment $i$ to another environment $j$ where the best strategy is different and $q$ is the fraction of the population that is composed by imitators.


## Appendix 2 model

Fitness of learners:

$$
\begin{align}
    W_L = W_0 + D - C
\end{align}
$$

where $W_0$ is the baseline fitness regardless of the learning strategy, $D$ is the gain in fitness from learning the best strategy for the given environment and $C$ is the cost of learning. For imitators we have

$$
\begin{align}
    W_I = W_0 + D\left[2 \frac{1 - q^n + q^n \gamma}{1 - q^n (1 - 2\gamma)} - 1\right]
\end{align}
$$

where $\gamma$ is the probability that the environment switches from state 1 to 2, favoring the other behavior, and $q$ is the fraction of the population that is composed by imitators, that imitate any learner between $n$ observed individuals.