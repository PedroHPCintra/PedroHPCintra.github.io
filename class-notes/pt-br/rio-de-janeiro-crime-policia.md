---
layout: sub-page_pt-br
---

Apparent evidence in favor of the hypothesis that more police action leads to less crime -> contrasting evidence when this is modeled on mechanisms

$$
\begin{align}
    & \frac{d P}{dt} = \alpha H(t-\tau) \\
    & \frac{d H}{dt} = \gamma(t) H(t) - \delta(t) P(t) H(t)
\end{align}
$$

$\delta$ is the police effectiveness, $\alpha$ is the police sensitivity to criminal increase, $\tau$ is the response delay and finally, $\gamma(t)$ is the propensity of crime to increase with time, as a result of expanding criminal organizations and impunity of criminals. The criminal propensity and police effectiveness parameters may change with time as criminals respond to police action over time. For instance

$$
\begin{align}
    & \gamma(t) = \frac{\gamma_{+}}{1 + e^{-b_1(t - t_c)}} + \gamma_0 \\
    & \delta(t) = \frac{\delta_0 - \delta_{-}}{1 + e^{b_2 (t - t_c)}} + \delta_{-}
\end{align}
$$

In reality, things might be more like

$$
\begin{align}
    & \frac{d P}{dt} = \alpha H(t-\tau) \\
    & \frac{d H}{dt} = \gamma(t) H(t) \left[ 1 - \frac{H(t)}{H_{\max}} \right] - \delta(t) P(t) H(t) + \underbrace{\cdots}_{\text{social effects}}
\end{align}
$$