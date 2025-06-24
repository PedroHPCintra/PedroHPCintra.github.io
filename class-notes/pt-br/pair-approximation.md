---
layout: sub-page_pt-br
---

# _Pair Approximation_ - Modelo Logístico

## Descrição do sistema

Considere uma rede na qual cada sítio pode possuir dois estados:
- Vazio (0) 
- Ocupado (1)

**Reações:**
1. **Nascimento (0 $\rightarrow$ 1)**: Sítios ocupados produzem novos indivíduos com uma taxa $b$, que são enviados aleatoriamente para um dos $z$  sítios vizinhos ao sítio focal, independente do estado da vizinhança $\mathcal{N}(i)$
2. **Morte natural (1 $\rightarrow$ 0)**: Sítios ocupados morrem de forma natural, independente do estado da rede, com uma taxa $\gamma$
3. **Morte por aglomeração (1 $\rightarrow$ 0)**: Sítios ocupados morrem devido à aglomeração (que leva à competição por recursos) com uma taxa $1 + \delta \times$(n° de vizinhos ocupados)

![Neighborhood](https://pedrohpcintra.github.io/assets/img/class_notes/Neighborhood.png)

## Equação Mestra

Seja $P(\vec{n}, t)$ a probabilidade de que a rede tenha a configuração $\vec{n} = (n_1, n_2, \ldots, n_N)$ no instante $t$, onde $n_i \in \{0,1\}$ é o estado do sítio $i$.

$$\frac{dP(\vec{n}, t)}{dt} = \sum_{\vec{n}'} [W(\vec{n}|\vec{n}') P(\vec{n}', t) - W(\vec{n}'|\vec{n}) P(\vec{n}, t)]$$

**Taxas de transição $W(\vec{n}'|\vec{n})$:**

1. **Nascimento** ($0 \to 1$ no sítio $i$):
   $$
   W(\vec{n} - \hat{e}_i|\vec{n}) = b \sum_{j \in \mathcal{N}(i)} n_j \cdot \frac{1}{z} \quad \text{if } n_i = 0
   $$

2. **Aglomeração** ($1 \to 0$ no sítio $i$):
   $$
   W(\vec{n} + \hat{e}_i|\vec{n}) = \left(1 + \delta \sum_{j \in \mathcal{N}(i)} n_j\right) n_i
   $$

3. **Morte natural** ($1 \to 0$ no sítio $i$):
   $$
   W(\vec{n} + \hat{e}_i|\vec{n}) = \gamma n_i
   $$

onde $\mathcal{N}(i)$ é a vizinhança do sítio $i$ e $\hat{e}_i$ é o vetor unitário do sítio $i$.

## Equações para médias

Tomando o valor esperado:
- $\rho_1 = \langle n_i \rangle$ (densidade de sítios ocupados)
- $\rho_{11} = \langle n_i n_j \rangle$ para vizinhos $i,j$ (densidade de pares ocupados)
- $\rho_{10} = \langle n_i (1-n_j) \rangle$ para vizinhos $i,j$ (densidade de pares 10)

A partir da equação mestra:

$$\frac{d\rho_1}{dt} = \left \langle \frac{dn_i}{dt} \right \rangle$$

**Contribuição do nascimento:**

$$
\frac{b}{z} \sum_{j \in \mathcal{N}(i)} \langle n_j (1 - n_i) \rangle = \frac{b}{z} \cdot z \cdot \rho_{10}
$$

Usando a probabilidade condicional:
$$
P(\text{vizinho ocupado | sítio i está vazio}) = q_{1|0} = \frac{\rho_{10}}{\rho_0} \Rightarrow
$$
$$
\Rightarrow \rho_{10} = q_{1|0} \rho_0
$$

Portanto a taxa de nascimento fica: $b q_{1|0} \rho_0 = b q_{1|0} (1-\rho_1)$

**Contribuição da aglomeração:**
$$
-\left \langle \left(1 + \delta \sum_{j \in \mathcal{N}(i)} n_j\right) n_i \right \rangle = -(1 + \delta z q_{1|1})\rho_1
$$

**Contribuição da morte natural:**
$$-\gamma \langle n_i \rangle = -\gamma \rho_1$$

portanto:
$$\boxed{\frac{d\rho_1}{dt} = bq_{1|0}(1-\rho_1) - (1 + \delta z q_{1|1} + \gamma)\rho_1}$$

Esta equação depende de $\rho_{11}$, poís $q_{1|1} = \rho_{11}/\rho_{1}$. Para conseguirmos resolver o sistema sem invocar a aproximação de campo médio, precisamos de uma equação para a frequência de pares $\rho_{11}$.

## Derivação da equação de pares

Para a densidade de pares $\rho_{11}$:

$$\frac{1}{2}\frac{d\rho_{11}}{dt} = \left \langle \frac{d(n_i n_j)}{dt} \right \rangle \text{ para vizinhos } i,j$$

**Contribuição do nascimento:**

Cada sítio ocupado produz filhotes a uma taxa $b$, enviado-os para um dos $z$ vizinhos com igual probabilidade $1/z$.

Para que um par $(1,1)$ seja criado a partir do nascimento:
- Um vizinho ocupado $k \in \mathcal{N}(i), k \neq j$ gera um filho no sítio vazio $i$ (probabilidade $1/z$ a cada evento de nascimento)
- Um vizinho ocupado $k \in \mathcal{N}(j), k \neq i$ gera um filho no sítio vazio $j$ (probabilidade $1/z$ a cada evento de nascimento)

![Neighborhood-2](https://pedrohpcintra.github.io/assets/img/class_notes/Neighborhood_2.png)

A taxa com a qual pares $(1,1)$ são criados a partir de pares $(1,0)$ tem uma contribuição do sítio já previamente conhecido no estado $1$ $b/z$, mais a contribuição dos demais $z-1$ sítios em $\mathcal{N}(i)$ que estiverem no estado $1$:

$$
\frac{b}{z} \rho_{10} \left[ 1 + (z-1) \cdot P(\text{outros sítios ocupados | par (1,0)}) \right]
$$

Assumindo de forma simplificada que $P(\text{outros sítios ocupados | par (1,0)}) = P(\text{outros sítios ocupados | sítio focal = 0}) = q_{1|0}$ chegamos ao resultado

$$
\frac{b}{z}[1 + (z-1)q_{1|0}]\rho_{10}
$$

No final das contas estamos assumindo que a informação que um dos vizinhos do sítio focal $0$ é um sítio $1$ não muda de forma significante a probabilidade condicional de que outros sítios na vizinhança esteja ocupada.

**Contribuições de morte:**

Cada sítio $(1,1)$ morre com uma taxa $(1 + \delta \times \text{vizinhos ocupados} + \gamma)$

Para um sítio $(1,1)$, há com certeza ao menos 1 vizinho ocupado (o outro par), mais $(z-1)q_{1|1}$ outros vizinhos ocupados esperados nos $(z-1)$ vizinhos. Aqui aplicamos a mesma aproximação anterior, de que a probabilidade condicional $q_{1|(1,1)}$ é aproximadamente igual à $q_{1|1}$.

$$
(1 + \delta[1 + (z-1)q_{1|1}] + \gamma)\rho_{11}
$$

$$\boxed{\frac{1}{2}\frac{d\rho_{11}}{dt} = \frac{b}{z}[1 + (z-1)q_{1|0}]\rho_{10} - (1 + \delta[1 + (z-1)q_{1|1}] + \gamma)\rho_{11}}$$

## Equações finais

$$
\begin{align}
   & \frac{d\rho_1}{dt} = bq_{1|0}(1-\rho_1) - (1 + \delta z q_{1|1} + \gamma)\rho_1 \\
   & \frac{1}{2}\frac{d\rho_{11}}{dt} = \frac{b}{z}[1 + (z-1)q_{1|0}]\rho_{10} - (1 + \delta[1 + (z-1)q_{1|1}] + \gamma)\rho_{11}
\end{align}
$$

onde:
- $q_{1\|0} = \rho_{10}/(1-\rho_1)$
- $q_{1\|1} = \rho_{11}/\rho_1$ 
- $\rho_{10} = \rho_1 - \rho_{11}$