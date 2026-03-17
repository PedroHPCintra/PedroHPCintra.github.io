---
layout: sub-page
---

If you have ever studied the mathematical dynamics of populations, be it in ecology or epidemiology, you have probably seen the logistic growth model. It is one of the first models studied in the description of population growth. Then, I imagine that just like me, you probably seen a differential equation like this one (if you haven't that's also ok)

\\[
\begin{align}
    \frac{\mathrm{d}N}{\mathrm{d}t} = rN \left(1 - \frac{N}{k} \right)
\end{align}
]\\

where $k$ is the carrying capacity of the population, i. e., the maximum value that it can reach, given the limitations of the environment, $r$ is the growth rate and $N$ is the population size on a given moment in time (more formally, one would write $N(t)$ to highlight the fact that $N$ is a function of time). What this equation is telling us is that the rate of change for a population only subjected to the limitations in resources (no predation or interactions with other populations) is proportional to the number of individuals in the population and constrained by the carrying capacity of the environment.

Well nice, but where does this equation came from? You maybe have seen a construction that begins with an exponential growth to then add a term related to resource limitation in order to arrive at the logistic model. I'm not a big fan of this derivation (some readers may argue that this is not a formal derivation, but I'm simplifying the language here to make this more coloquial), because it does not shows us explicitly what are the kinds of assumptions we make with respect to the individuals that make up this population. In order to get this clearly, we must build the equation from the individual dynamics. **This is my objective here.**

The transition from individual dynamics to population behavior is for me an extraordinary phenomenon. Perhaps due to my background as a physicist, I have grown attached to and found a certain beauty in observing simple individual descriptions resulting in complex macroscopic behaviors. For the physicist readers, I tend to think of the transition from the operator formalism of quantum mechanics to the standard formalism of classical mechanics, when taking the average of operators in a many-particle system. Here things won't be so different, mathematically speaking.

But enough chatting, let's go. Here I will assume dynamics that, at first glance, may infuriate many of my biologist friends, but I ask for patience as I will try to justify the assumptions made here. The **first assumption** is that **the only interaction that occurs is between consumer individuals and their resources**, that is, we are ignoring predation, interspecific competition and even sexual reproduction within the population itself. Of course this is a scenario far from reality, but we have to start somewhere. It was by ignoring air resistance that Galileo began to describe the motion of bodies after all.

As a consequence of the first assumption, the **second assumption** is that **individuals reproduce asexually**. It is no coincidence that the observations that best match logistic dynamics are those made in the laboratory with microorganisms (one of the first experiments evaluating logistic growth was in 1934 by G. F. Gause, [Struggle for Existence](http://193.204.79.40/wp-content/uploads/2015/12/gause1934.pdf)).

Since we are only interested in describing the dynamics of resource consumers, we will focus on them. Thus, at a certain brief period of time, 4 different things can occur:

- An individual $X$ can reproduce asexually resulting in $X + X$. We represent this as

$$
\begin{align}
    X \underset{b}{\rightarrow} X + X
\end{align}
$$

- An individual $X$ can die from natural causes (old age, disease, etc.).

$$
\begin{align}
    X \underset{d}{\rightarrow} 0
\end{align}
$$

- Two individuals can "fight" for a resource or even for space, such that only one of them survives (here we are implictly stating that space or resource is limited, if we want to make a clear argument for which of the two we are referring to, we need to work on the specific form of the rate $\alpha$)

$$
\begin{align}
    X + X \underset{\alpha}{\rightarrow} X
\end{align}
$$

- Nothing happens

Here $b$ is the rate at which individuals reproduce. This rate is proportional to the amount of resource available per individual and the probability of an individual finding a resource. I will discuss more about these rates later. $d$ is the death rate from natural causes and $\alpha$ the rate at which individuals die due to competition.

It is worth noting here that we leave implicit the **3rd assumption** of the model: **There are no mutations and the rates for each process do not depend on the characteristics of the individual**, that is, all individuals are equal. In ecological terms, we can say that all individuals have the same fitness.

**Things are now going to get more mathematical :nerd_face:**. In order to obtain a population description of these individuals, we ask ourselves what is the probability that, between time instants $t$ and $t + \Delta t$, we observe $N$ individuals in this population. In more "physics-like" terms we say that the system is in state $N$. Some physicists might think something like "wait a minute :raised_eyebrow: doesn't this look like the terminology used to describe the state of a system in quantum mechanics?" and whoever thought that is completely right. If you didn't think that, that's fine, life already has too many things to think about.

Well, of course many things can occur in a time interval $\Delta t$, but some are more probable than others. What do I mean? Well, let's see... if $b$, $d$ and $\alpha$ are rates for the occurrence of each scenario, the probability that each one of them alone occurs in a certain interval $\Delta t$ is given by the number of individuals at the beginning of this interval, multiplied by the occurrence rate and the time interval in question. For example, the chance that someone reproduces during $\Delta t$ and the population goes to the value $N$ is $(N-1) b \Delta t$. If you stop to think about it, it makes sense that the more individuals in the population, the greater the chance of one of them reproducing, just as this chance should also increase the larger the interval $\Delta t$, or the larger the rate $b$. The $(N-1)$ in the beginning of the expression is to say that one $t$ we had $(N-1)$ individuals, and thus after $\Delta t$ we got to $N$.

However, for the population to leave $N-1$ individuals at $t$ and go to $N$ individuals at $t + \Delta t$, due only to reproduction, only one individual must reproduce. Therefore, the chance $P$ that this occurs boils down to the probability of one individual reproducing while all the others do not reproduce. If the chance of reproduction of a single individual is $b \Delta t$, the chance that an individual does not reproduce is $1 - b \Delta t$. Therefore

$$
\begin{align}
    P_{N-1 \rightarrow N}^{r} &= \underbrace{(N-1)b \Delta t}_{\text{one of the N-1 reproduces}} \times \overbrace{\left(1 - b \Delta t \right)^{N-2}}^{\text{all the other N-2 don't}}
\end{align}
$$

for example, if we want the chance that through reproduction, the population reaches $N = 4$ at $t + \Delta t$, we will then have

$$
\begin{align}
    P_{3 \rightarrow 4}^{r} &= 3b \Delta t \times \left(1 - b \Delta t \right)^{2} = \\
    \nonumber
    & = 3b\Delta t \times \left(1 - 2b\Delta t + b^2\Delta t^2 \right) = \\
    \nonumber
    & = 3b\Delta t - 6b^2 \left(\Delta t \right)^2 + 3b^3 \left(\Delta t \right)^3 
\end{align}
$$

and this polynomial in $\Delta t$ increases more and more as $N$ increases. Great, it seems we have a completely intractable description, how would anyone expect us to calculate such a polynomial in a case where $N = 10000$ for example? :angry:

To our happiness, the wonders of calculus will save us. But I'll leave our hero for later.

And you might be thinking, "Well, well, well, but you yourself said that many things can happen in this time interval. What if two individuals reproduce?" Let's look at exactly that now. In this case, the population would need to have $N-2$ individuals at time $t$, and two of them would need to reproduce (remembering here that we only want to consider events that contribute to the population having $N$ individuals at $t + \Delta t$). After the first reproduction, a second reproduction would be necessary, now with the population at $N-1$ and a remaining time interval $\Delta t' < \Delta t$. Thus, we can say that the probability $P$ that the system will leave the state $N - 2$ and go to $N$ during $\Delta t$, only through reproduction, is

$$
\begin{align}
    P_{N-2 \rightarrow N}^{r} = \underbrace{(N-2)b \Delta t}_{\text{1ª reproduction}} \overbrace{(N-1) b \Delta t'}^{\text{2ª reproduction}} \underbrace{\left(1 - b \Delta t\right)^{N-3}}_{\text{Nobody else reproduces}}.
\end{align}
$$

If both reproductions happen at the same time, then $\Delta t' = \Delta t$ and the equation becomes

$$
\begin{align}
    P_{N-2 \rightarrow N}^{r} = \left[(N-2) b \Delta t \right]^2 \left(1 - b \Delta t\right)^{N-3} .
\end{align}
$$

We can keep playing with different scenarios and various numbers and forms in which the population may initially be on $N' \neq N$ and then arrive at $N$ between the instants $t$ and $t + \Delta t$.

> Here is important to note that in order to compute these probabilities, I had to subtly introduce the **4th assumption** that **events are independent**; that is, what happens to your neighbor is of no interest to you.

Note that for any event in this interval, there are terms in the probability that depend on $\left(\Delta t\right)^m$. Since we will consider small time intervals, such that $\Delta t \rightarrow 0$, probabilities with higher powers of $\Delta t$ become increasingly less likely. For example, in the case of a single reproduction, to reach a population of $N = 4$, we calculate the probability of this event as the equation

$$
\begin{align}
    P_{3 \rightarrow 4}^{r} = 3b\Delta t - 6b^2 \left(\Delta t \right)^2 + 3b^3 \left(\Delta t \right)^3 
\end{align}
$$

and the chances that this happens by means of two reproductions is

$$
\begin{align}
    P_{2 \rightarrow 4}^{r} &= 4b^2\left(\Delta t \right)^2 \left(1 - b \Delta t\right) = \\
    \nonumber
    & = 4b^2\left(\Delta t \right)^2 - 4b^3\left(\Delta t \right)^3
\end{align}
$$

Note that only the single-reproduction event has a contribution of $\Delta t$. This means that as $\Delta t \rightarrow 0$, this term becomes much larger than all the others, and therefore $P_{3 \rightarrow 4}^{r} \gg P_{2 \rightarrow 4}^{r}$. In other words, **if we look at a sufficiently short time interval, the chance of two events occurring becomes much smaller than the chance of only one of them occurring.**

> Before we continue, let's pause for a moment to think about this. If we consider a time interval of 1 month, what do you think is more likely: that only one child will be born in Brazil during that interval, or that many children will be born? Certainly, in one month, it is more likely that several thousand children will be born in Brazil than just one (in fact, in 2022, approximately 200,000 births occurred each month according to [noticias.uol.com.br](https://noticias.uol.com.br/cotidiano/ultimas-noticias/2024/03/27/criancas-nascidas-2022-brasil.htm)).
>
> But let's reduce this interval to 1 day. I believe it's reasonable to assume that the chance of more than one child being born is still greater than the chance of only one child being born. But surely, the chance of 200,000 being born is also much smaller. And what if the interval is 1 minute? What is the chance that two babies will be born in Brazil during that one minute? Is that chance greater than the chance of only one being born?
>
> As we look at shorter and shorter time intervals, multiple or even simultaneous events become increasingly rare.

Because of this, we only consider the contributions of unique events in population dynamics; we call this a **first-order approximation.**

Let's turn our attention to the question: What is the probability that we will observe the population with $N$ individuals after the interval from $t$ to $t + \Delta t$?

Since we already know the 4 possible events that individuals in our population can undergo, the possibilities are:

1. At time $t$, the system was already in state $N$, and did not change state during the interval $\Delta t$;

2. At time $t$, the system had $N+1$ individuals and one individual died of natural causes, bringing the system to state $N$;

3. Again, at time $t$ the system had $N+1$ individuals, but one of them died due to competition for resources with its neighbors;

4. The population at $t$ was $N-1$ individuals and one of them reproduced and generated a new member.

The transition probability for item 2 is $d(N+1)\Delta t\left(1 - dN\Delta t\right)^N = d(N+1)\Delta t + \mathcal{O}(\Delta t^2)$. Here we pack all terms that have a contribution of the power of $\Delta t$ greater than or equal to 2 as _"terms of order $\mathcal{O}$ greater than or equal to $\Delta t^2$"_. Analogously for item 3, the probability of occurrence is $\alpha(N+1)\Delta t + \mathcal{O}(\Delta t^2)$. We can represent the total probability $P_{n+1 \rightarrow n} = (d + \alpha) (N + 1) \Delta t + \mathcal{O}(\Delta t^2)$.

For item 4, we write directly $b(N-1) \Delta t + \mathcal{O}(\Delta t^2)$. And finally, item 1 can be seen as 1 minus the probability of 2, 3, and 4 occurring, since at least one of the 4 must occur.

Therefore, we can write the probability of observing the system with $N$ individuals, after an interval $\Delta t$ as

$$
\begin{align}
    \nonumber
    P(N;t+\Delta t) & = \overbrace{P(N-1;t)}^{\text{prob. be in N-1 at t}} \underbrace{b (N-1) \Delta t}_{\text{prob. reproduction}} + \\
    \nonumber
    & + \overbrace{P(N+1;t)}^{\text{prob. be in N+1 at t}} \underbrace{(d + \alpha)(N+1) \Delta t}_{\text{prob. death}} + \\
    \nonumber
    & + \overbrace{P(N;t)}^{\text{prob. be in N at t}} \underbrace{(1 - bN\Delta t)(1 - dN \Delta t)(1 - \alpha N \Delta t)}_{\text{prob. nothing happens}} + \\
    \nonumber
    & + \underbrace{\mathcal{O}(\Delta t^2)}_{\text{other terms of order equal or greater than } \Delta t^2}
\end{align}
$$

$$
\begin{align}
    \nonumber
    P(N;t+\Delta t) & = P(N;t)(1 - bN \Delta t - dN \Delta t - \alpha N \Delta t) + \\
    \nonumber
    & + P(N-1;t)b(N-1) \Delta t +\\
    \nonumber
    & + P(N+1;t)(d + \alpha)(N+1) \Delta t + \\
    \nonumber
    & + \mathcal{O}(\Delta t^2)
\end{align}
$$

Here it seems we only made things worse :fearful:. The answer to our question seems to depend on the probability of all other configurations, that should have their own probabilities. The answer seems far and unlikely, as if we were in a dark tunel without end. However, as uncle Iroh once said in Avatar, the legend of Aang:

. "Sometimes, life is like this dark tunnel, you can't always see the light at the end of the tunnel, but if you keep going, you'll get to a better place"

Our hero without cape, calculus, appears now! Yet, before invoking it, we must understand what does this dark scary equation for $P(N;t + \Delta t)$ is telling us. The image below shows what we have in our hands:

![prob-eq](https://pedrohpcintra.github.io/assets/img/class_notes/master_eq_scheme_en-us.png)

On this image we have 3 dimensions. The vertical one represents the probability $P(N)$ that the population is on the state $N$. Lower bars indicate lower probability. The other two axes on "the ground" indicate the time dimension and the specific state $N$. At the instant $t$, we notice that there are several values for $N$, with probabilities $P(N)$ greater than 0. When chosing one of these values of $N$, we compute the value for the probability of this value at time $t + \Delta t$ according to the equation above. On the image, there are two arrows indicating that $P(N+1;t)$ and $P(N-1;t)$ also afect the result of $P(N;t + \Delta t)$, as highlighted by the equation. We can then think that $P(N;t+\Delta t)$ depends on the probabilities that the population is at $N+1$, $N-1$ and $N$ at time $t$. Each probability is weighted by the chance that reproductions and deaths occur (or not). If we want to compute how this whole distribution changes from one moment to another, we need to compute $P(N;t+\Delta t)$ for all values of $N$.

Then, instead of asking ourselves about the chance that the population IS in a given value, it makes more sence to ask how this probability changes over time.
> Frequently in nature, it is easier to explain why things change then to explain why they are in the exact way they are now.

To achieve that, we divide the probability by $\Delta$ and move the term $P(N;t)$ to the left-hand side of the equation, obtaining the rate of change for the probability over time

$$
\begin{align}
    \frac{P(N;t+\Delta t) - P(N;t)}{\Delta t} &= -P(N;t)(b+d+\alpha)n + P(N-1;t)b(N-1) \\
    \nonumber
    & + P(N+1;t)(N+1)(d + \alpha) + \mathcal{O}(\Delta t),
\end{align}
$$

and as mentioned before, we are going to take the limit $\Delta t \rightarrow 0$, so that our rate of change represents "instantaneous" rates of change.

$$
\begin{align}
\lim_{\Delta t \rightarrow 0} \frac{P(N;t+\Delta t) - P(N;t)}{\Delta t} = \frac{\mathrm{d}}{\mathrm{d}t}P(N;t),
\end{align}
$$

finally, we obtain

$$
\begin{align}
\boxed{
    \frac{\mathrm{d}}{\mathrm{d}t}P(N;t) = -P(N;t)(b+d+\alpha)n + P(N-1;t)b(N-1) + P(N+1;t)(N+1)(d + \alpha)
}
\end{align}
$$

Aaahh look at this, a differential equation! Happly they are much more solvable and as Steven Strogatz once said:

> "Since Newton, humanity has learned that the laws of nature are often expressed in the language of differential equations"

In fact this is exactly the **master equation** of this system!


Entretanto, essa equação é mais uma vez complicada demais, poís a probabilidade parar um estado $N$ depende da probabilidade de $N$, $N+1$ e $N-1$. E as probabilidades de $N+1$ e $N-1$ vão depender das probabilidades de $N+2$, $N$, $N-1$ e $N-2$, $N$ e $N-1$, respectivamente; e assim por diante. No fim teremos um sistema de sei la quantas centenas de ou milhares de equações diferenciais acopladas. Isso pode até ser solúvel para $N$ baixos, se estabelecermos um limite máximo para a distribuição de probabilidades de $N$, mas rapidamente se torna impraticável para $N$ altos.

E se então nos perguntarmos a respeito do comportamento médio :thinking:? E se ao invés de nos preocuparmos com a distribuição de probabilidades de $N$ em um dado instante $t$, nos perguntarmos qual é o valor médio de $N$ naquele instante? Aqui entra a nossa **5ª premissa**, a de que **nosso sistema é homogêneo o suficiente de forma que a média seja representativa da população inteira**. Esse calculo do valor médio de $N$ é representado na imagem que mostrei a pouco, pelas linhas fortes que mostram o valor de $\left \langle N \right \rangle$ nos instantes $t$ e $t + \Delta t$. Ou seja, o que estamos fazendo aqui é assumindo que a variação temporal deste valor médio é descritivo da variação temporal da distribuição inteira. Para uma distribuição discreta, tal qual a distribuição de valores de população $N$, a média é calculada através de

$$
\begin{align}
    \left \langle N \right \rangle = \displaystyle \sum_{N} N P(N;t) .
\end{align}
$$

Aqui a notação $\left \langle N \right \rangle$ significa _o valor médio de_ $N$. Leitores físicos provavelmente estão acostumados a esta notação e novamente peço desculpas aos amigos e amigas biológos pela possível confusão na mente de vocês com notações novas, mas pela minha formação acho a escrita dessa forma muito mais fluída e fácil.

Iremos tornar a equação mestra em uma equação diferencial para o valor médio de $N$. Multiplicando a equação mestra por $N$ e somando sobre todos os estados, obtemos

$$
\begin{align}
    \frac{\mathrm{d}}{\mathrm{d}t} \left \langle N \right \rangle & = - (b + d+ \alpha) \sum_{N} N^2 P(N;t) + \\
    \nonumber
    & + b \sum_{N} N^2 P(N-1;t) - \\
    \nonumber
    & - b \sum_{N} N P(N-1;t) + \\
    \nonumber
    & + (d + \alpha) \sum_{N} N^2 P(N+1;t) + \\
    \nonumber
    & + (d+\alpha) \sum_{N} N P(N+1;t)
\end{align}
$$

E agora parece que a situação piorou ainda mais. Antes tinhamos um sistema de equações acoplado e agora temos uma equação diferencial com vários somatórios??? Mas confiem no processo. Se pudermos deixar os somatórios no formato $\displaystyle \sum_{N} N P(N;t)$, poderemos escrever tudo apenas em termos das médias de $N$, já que essa soma é justamente a definição da média. O primeiro termo da equação diferencial já tem esse formato, e portanto nos atentaremos ao segundo. Se fizermos uma renomeação dos índices no somatório, passando de uma soma em $N$ para uma soma em um nov índice $M$, tal que $M = N - 1$, reescrevemos

$$
\begin{align}
    b \sum_{N} N^2 P(N-1;t) = b \sum_{M} (M+1)^2 P(M;t)
\end{align}
$$

Porém, $M$ é apenas um índice de soma e podemos nomeá-lo da forma como quisermos. Por isso iremos renomeá-lo novamente para $N$, de forma que

$$
\begin{align}
    b \sum_{N} N^2 P(N-1;t) = b \sum_{N} (N+1)^2 P(N;t)
\end{align}
$$

Isso pode parecer um truque sem sentido e talvez mágico para alguns, então permitam-me fazer um pause em nossa derivação afim de explicar o que ocorre aqui (quem não quiser ver pode continuar lendo após o ---).

---
O que fizemos aqui na prática foi mover o somatório em 1 índice para trás. Isso pode soar um movimento ilegal e freestyle, mas peguemos um exemplo prático:

Suponha $P(0) = 0.05$, $P(1) = 0.15$, $P(2) = 0.3$, $P(3) = 0.3$, $P(4) = 0.15$, $P(5) = 0.05$ e $P(N>5) = 0$. Nesse caso

$$
\begin{align}
\nonumber
& \sum_{N} N^2 P(N-1) = \\
& = \sum_{N=0}^\infty N^2 P(N-1) = 0\times P(-1) + 1^2 \times P(0) + \cdots + 6^2 \times P(5) + \cdots
\end{align}
$$

naturalmente todos os termos que envolvem $P(6)$ em diante serão nulos, bem como o primeiro termo por envolver $P(-1) = 0$. O resultado desta soma é $13.7$. Poís bem, façamos uma mudança no índice de tal forma que $M$ agora é $N-1$. Neste caso

$$
\begin{align}
\nonumber
& \sum_{N=0}^\infty N^2 P(N-1) = \\
& \sum_{M=-1}^\infty (M+1)^2 P(M) = 0^2\times P(-1) + 1^2 \times P(0) + \cdots + 6^2 \times P(5) + \cdots
\end{align}
$$

Note que o somatório é o mesmo, inclusive o resultado continua sendo o mesmo $13.7$. Isso poís a relação entre os termos da soma ainda é a mesma, como você mesmo pode verificar escrevendo termo a termo da soma.

---

Expandindo o termo do somatório recém encontrado, podemos escrever

$$
\begin{align}
    b \sum_{N} (N+1)^2 P(N;t) & = b \sum_{N} N^2 P(N;t) + 2 b \sum_{N} N P(N;t) + b \underbrace{\sum_{N} P(N;t)}_{=1} = \\
    \nonumber
    & = b \sum_{N} N^2 P(N;t) + 2 b \sum_{N} N P(N;t) + b,
\end{align}
$$

onde na última linha utilizamos a normalização $ \sum_{N} P(N;t) = 1$. O somatório no terceiro termo fica

$$
\begin{align}
    b \sum_{N} N P(N-1;t) & = b \sum_{N} (N+1) P(N;t) = b \sum_{N} N P(N;t) + b
\end{align}
$$

Analogamente para as somas envolvendo $P(N+1;t)$, fazemos a mudança de índice $M = N+1$ e obtemos, após a renomeação de $M$

$$
\begin{align}
    (d + \alpha) \sum_{N} N^2 P(N+1;t) & = (d + \alpha) \sum_{N} (N-1)^2 P(N;t) = (d + \alpha) \sum_{N} N^2 P(N;t) - \\
    \nonumber
    & - 2 (d + \alpha) \sum_{N} N P(N;t) + (d + \alpha)
\end{align}
$$

$$
\begin{align}
    \nonumber
    (d + \alpha) \sum_{N} N P(N+1;t) & = \\
    (d + \alpha) \sum_{N} (N-1) P(N;t) & = (d + \alpha) \sum_{N} N P(N;t) - (d + \alpha)
\end{align}
$$

Juntando tudo, a equação mestra fica escrita como

$$
\begin{align}
    \frac{\mathrm{d}}{\mathrm{d}t} \left \langle N \right \rangle & = - (b + d+ \alpha) \sum_{N} N^2 P(N;t) + b \sum_{N} N^2 P(N;t) + 2 b \sum_{N} N P(N;t) + \\
    \nonumber
    & + b - b \sum_{N} N P(N;t) - b + (d + \alpha) \sum_{N} N^2 P(N;t) - \\
    \nonumber
    & - 2 (d + \alpha) \sum_{N} N P(N;t) + (d + \alpha) + (d + \alpha) \sum_{N} N P(N;t) - (d + \alpha)
\end{align}
$$

$$
\begin{align}
    \boxed{\frac{\mathrm{d}}{\mathrm{d}t} \left \langle N \right \rangle = b \sum_{N} N P(N;t) - d \sum_{N} N P(N;t) - \alpha \sum_{N} N P(N;t)}
\end{align}
$$

Veja que caso $b$, $d$ e $\alpha$ sejam constantes, podemos escrever

$$
\begin{align}
    \nonumber
    &\frac{\mathrm{d}}{\mathrm{d}t} \left \langle N \right \rangle = (b - d- \alpha) \sum_{N} N P(N;t)\\
    & \frac{\mathrm{d}}{\mathrm{d}t} \left \langle N \right \rangle = \underbrace{(b - d- \alpha)}_{r} \left \langle N \right \rangle,
\end{align}
$$

e essa equação se torna a mesma equação do crescimento exponencial, com a diferença que o termo de mortalidade é agora adicionado de um fator devido à competição por recursos, e ao invés de $b > d$ ser a condição necessária para o crescimento exponencial, precisamos ter $b > d + \alpha$. Ou seja, a taxa de reprodução da população precisa ser maior do que a soma da taxa de mortalidade por causas naturais com a taxa de mortalidade por competição intraespecífica.

Porém a taxa de mortalidade por competição de recursos é proporcional à probabilidade de que outro indivíduo adquira o recurso antes, levando o primeiro à fome. Naturalmente a chance de que isso ocorra é proporcional ao numero de indivíduos. Portanto em uma descrição mais realística a competição por recursos depende da quantidade de indivíduos na população. Quanto menos indivíduos, menor a necessidade de competir com vizinhos por comida, água, espaço, etc. Acontece que essa depêndencia pode assumir muitas formas, e muito provavelmente não ocorre de forma linear.Entretanto, pegando o espírito da aproximação de primeira ordem mencionado anteriormente, aproximamos a dependência da taxa de competição com a população por $\alpha = \alpha_0 N$. Isto é, a competição por recursos aumenta linearmente com o aumento da população. Apenas com essa melhoria, mantendo a taxa de mortalidade por causas naturais e a natalidade fixas, obtemos

$$
\begin{align}
    \frac{\mathrm{d}}{\mathrm{d}t} \left \langle N \right \rangle & = b \sum_{N} N P(N;t) - d \sum_{N} N P(N;t) - \alpha_0 \sum_{N} N^2 P(N;t) = \\
    \nonumber
    & = b \left \langle N \right \rangle - d \left \langle N \right \rangle - \alpha_0 \left \langle N^2 \right \rangle .
\end{align}
$$

que parece ser a equação diferencial de um modelo logístico, porém note que está equação envolve a média de $N^2$, isto é, o segundo momento estatístico da distribuição de probabilidades para os estados possíveis do sistema. Precisamos ser capazes de encontrar $\left \langle N^2 \right \rangle$ para poder solucionar esta equação. Poderíamos refazer todo o processo para encontrar uma equação que descreva a variação temporal de $\left \langle N^2 \right \rangle$, e substituir a integral desta equação no último termo. Porém, está equação iria depender do terceiro momento estatístico $\left \langle N^3 \right \rangle$. Não ajudaria muito.

A aproximação de campo médio também supõe no fundo que todos os momentos estatísticos de ordem maior que 1 são dados em termos do primeiro momento estatístico (a média). Logo

$$
\begin{align}
    \boxed{\frac{\mathrm{d}}{\mathrm{d}t} \left \langle N \right \rangle = b \left \langle N \right \rangle - d \left \langle N \right \rangle - \alpha_0 \left \langle N \right \rangle^2 = \left \langle N \right \rangle \left[ \underbrace{(b-d)}_{r} - \alpha_0 \left \langle N \right \rangle \right]}
\end{align}
$$

Esta é a equação conhecida para um crescimento logístico!

No fundo, o que a aproximação de campo médio está dizendo nesta equação é que a variância na distribuição de probabilidade dos estados $N$, em um dado instante $t$, é nula. $\mathrm{Var}[N] = \left \langle N^2 \right \rangle - \left \langle N \right \rangle^2 = 0 \Rightarrow \left \langle N^2 \right \rangle = \left \langle N \right \rangle^2$. Caso a variância não seja nula, podemos reescrever a equação como

$$
\begin{align}
    \frac{\mathrm{d}}{\mathrm{d}t} \left \langle N \right \rangle = b \left \langle N \right \rangle - d \left \langle N \right \rangle - \alpha_0 \left( \left \langle N^2 \right  \rangle + \mathrm{Var}[N] \right) 
\end{align}
$$

Ou seja, a presença de uma variação na distribuição de probabilidade de estados do sistema, naturalmente provoca uma diminuição no valor esperado de $N$ para um dado instante de tempo $t$. A estocasticidade não apenas provoca flutuações em torno da média, como também é capaz de mudar o próprio valor esperado de população $t$ tempo após o início da dinâmica.

E agora que chegamos ao fim dessa derivação, e encontramos a tão famosa equação diferencial do modelo logístico, vamos parar para ver algumas coisas:

A primeira delas é que tivemos que assumir 5 premissas para chegar nela:

1. Os indivíduos só interagem com sua comida e entre si.
2. A reprodução ocorre de forma assexuada.
3. Todos os indivíduos são iguais e possuem a mesma aptidão.
4. Eventos de morte, reprodução ou competição que ocorrem com um indivíduo, não dependem do que ocorre com os outros indivíduos.
5. O sistema é espacialmente homogêneo.

Somado a isso há a suposição de que a variância na distribuição de probabilidade de estados de $N$ é nula. E que a taxa de competição é linearmente dependente da população $\alpha = \alpha_0 N$.

Muita coisa teve que ser suposta como verdade para chegarmos nessa equação. Em laboratório, é muito mais fácil atingir estes requerimentos, o que torna a verificação dessa equação muito mais papável. Isso não torna a equação inútil na vida real fora do laboratório, ela serve como a base para descrever o comportamento das populações em nível mais básico. Podemos por exemplo, dividir a população em machos $M$ e fêmeas $F$ e assumir uma reprodução sexuada, eliminando uma das premissas. Cada uma delas pode ser atacada individualmente para aproximar o modelo da realidade.

## Mas para que serve um modelo?

Seu único e exclusivo fim é descrever a realidade com a melhor exatidão possível? Ou ele serve como uma ferramenta para entender o papel de diversos mecanismos que atuam em um sistema? Se a sua resposta tender ao primeiro caso, então receio que nenhum modelo (seja matemático ou não) irá lhe satisfazer. Já no segundo caso, começamos a ver o papel do modelo logístico, ao observarmos um sistema que obedece de forma razoável o comportamento descrito pelo modelo logístico, podemos dizer que as 5 premissas são satisfeitas? Não, mas podemos afirmar que os outros mecanismos que sem dúvida estão presentes talvez não sejam dominantes na vida dos indivíduos que compõe esta população.

Como um exemplo, trarei o leitor para a minha área de formação, a física. Quando aprendemos física no ensino médio, sempre desprezamos a resistência do ar. Porque? Porque passar 3 anos aprendendo fórmulas e leis que não descrevem aquilo que encontramos todos os dias? Há dois motivos para isso, no meu ver. O primeiro está relacionado à dificuldade, é muito mais fácil começar pelo mais simples (e já vemos o trauma que isso causa em muitos alunos). Incluir a resistência do ar em, digamos, o lançamento parabólico de objetos, envolve resolver uma equação diferencial de 2ª ordem

$$
\begin{align}
    \frac{\mathrm{d}\vec{v}}{\mathrm{d}t} = -\vec{g} - \frac{1}{2} \rho C_d A \vec{v}^2,
\end{align}
$$

na qual eu acho razoável argumentar que alunos de ensino médio não possuem a maturidade para compreender e interpretar. O segundo motivo está relacionado aos mecanismos. Sim, claro que o ar está sempre presente, mas não é ele que determina majoritariamente a trajetória de uma bolinha atirada no ar na maioria das vezes. Quem determina isso é a força gravitacional. A resistência do ar ocupa um papel muito pequeno nestes casos, de forma que ensinar os alunos equações e fórmulas que envolvam-na se torna mais uma distração do que é realmente mais importante e mais geral do que uma adição valiosa para o saber do aluno sobre o funcionamento do mundo.

O modelo logístico faz esse mesmo papel na ecologia. Ele é a 2ª lei de Newton para a ecologia, ele é o caso ecológico da mecânica sem resistência do ar, rotação, carga elétrica e tudo mais. Mas é através dele que notamos alguns comportamentos gerais.

E por fim, no caso da resistência do ar, a descrição é tão boa sem ela, que muitas vezes nem precisamos considerá-la. Em cenários ecológicos o mesmo ocorre, algumas interações entre indivíduos podem estar sempre presentes, mas dependendo da escala de tempo e precisão que nos interessa, elas se tornam desprezíveis.