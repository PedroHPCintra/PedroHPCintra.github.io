---
layout: sub-page_pt-br
---

Se você já estudou dinâmica de populações, seja em ecologia ou epidemiologia, você já deve ter se deparado com o modelo logístico. Um dos primeiros modelos apresentados na descrição de um crescimento populacional. E assim como eu, você provavelmente se deparou com uma equação diferencial nesse formato

$$
\begin{align}
    \frac{\mathrm{d}N}{\mathrm{d}t} = rN \left(1 - \frac{N}{k} \right)
\end{align}
$$

onde $k$ é a capacidade de suporte da população; isto é, o valor máximo que ela pode atingir, $r$ é a taxa de crescimento e $N$ é o valor da população em um certo instante de tempo. O que essa equação nos diz é que a taxa de variação no tempo, de uma população sujeita apenas à limitação de recursos (sem sofre predação ou outras interações com outras populações) cresce rapidamente mas tende a se estabilizar em um valor máximo, ditado pelas condições ambientais.

Mas ok, e de onde essa equação veio? Você talvez tenha visto uma construção que começa a partir de um crescimento exponencial, e então adiciona a limitação por recursos para chegar ao modelo logístico. Eu não gosto muito dessa derivação (aos mais preciosistas que queiram arugmentar se isso é ou não uma derivação, estou simplificando a linguagem aqui para tentar elaborar algo mais coloquial), pois ela não nos mostra de forma clara que tipo de premissas assumimos a respeito dos indivíduos que compõe essa população. Para isso, precisamos montar essa equação, partindo da dinâmica individual. Esté é meu objetivo aqui.

A transição entre a dinâmica de indivíduos para o comportamento de população é para mim um fenômeno extraordinário, talvez pelo meu histórico como um físico, eu tenha me apegado e encontrado uma certa beleza em observar descrições individuais e simples resultar em comportamentos macroscópicos complexos. Para os leitores físicos, eu tendo a pensar na transição entre o formalismo de operadores da mecânica quântica para o formalismo padrão da mecânica clássica, ao tomarmos a média dos operadores em um sistema de muitas partículas. Aqui a coisa não será tão diferente, matematicamente falando.

Mas chega de enrolação, vamos lá. Aqui irei supor uma dinâmica que, a primeira vista, pode enfurecer muitos dos meus amigos biológos, mas peço paciência pois tentarei justificar as suposições aqui feitas. A **primeira suposição** é a de que **a única interação que ocorre é entre indivíduos consumidores e seus recursos**, ou seja, estamos ignorando a predação, competição interespecífica e até mesmo a reprodução sexuada dentro da prórpia população. É claro que este é um cenário longe da realidade, mas temos que começar em algum lugar. Foi ignorando a resistência do ar que Galileu começou a descrever o movimento dos corpos.

Como consequência da primeira suposição, a **segunda suposição** é que **os indivíduos se reproduzem assexuadamente**. Não é atoa que as observações que melhor batem com a dinâmica logística são aquelas feitas em laboratório com microorganismos (um dos primeiros experimentos avaliando o crescimento logístico foi em 1934 por G. F. Gause, [Struggle for Existence](http://193.204.79.40/wp-content/uploads/2015/12/gause1934.pdf)).

Uma vez que estamos interessados apenas em descrever a dinâmica dos consumidores do recurso, focaremos neles. Sendo assim, em um certo instante de tempo, 4 coisas diferentes podem ocorrer:

- Um indivíduo $X$ pode se reproduzir de forma que teremos então $X + X$. Representamos isso da forma

$$
\begin{align}
    X \underset{b}{\rightarrow} X + X
\end{align}
$$

- Um indvíduo $X$ pode morrer por causas naturais (velhice, fome, doença, etc).

$$
\begin{align}
    X \underset{d}{\rightarrow} \empty
\end{align}
$$

- Dois indivíduos podem "brigar" por um recurso ou até mesmo por espaço, de forma que apenas um deles sobreviva

$$
\begin{align}
    X + X \underset{\alpha}{\rightarrow} X
\end{align}
$$

- Nada acontecer

Aqui $b$ é a taxa com a qual indivíduos se reproduzem. Está taxa é proporcional à quantidade de recurso disponível para cada indivíduo e a probabilidade de um indivíduo encontrar recurso. Mais tarde discutirei mais a respeito destas taxas. $d$ é a taxa de morte por causas naturais e $\alpha$ a taxa com a qual indivíduos morrem devido à competição.

Vale notar aqui que deixamos aqui implícita a **3ª premissa** do modelo: **Não há mutações**, ou seja, todos os indivíduos são iguais. Em termos ecológicos, podemos dizer que todos os indivíduos possuem a mesma aptidão (aqui estou usando aptidão como uma tradução para o _fitness_).

**As coisas agora ficaram mais matemáticas. :nerd_face:** Afim de obter uma descrição populacional destes indivíduos, nos perguntamos qual é a probabilidade de que, entre os instantes de tempo $t$ e $t + \Delta t$, observemos $N$ indivíduos nesta população. De forma mais "física" dizemos que o sistema está no estado $N$. Alguns físicos talvez possam pensar algo como "pera aê :raised_eyebrow: isso não parece com a terminologia que se usa para descrever o estado de um sistema em mecânica quântica?" e quem pensou isso está completamente certo. Se você não pensou, tudo bem a vida já tem coisa demais para pensarmos.

Bem, é claro que muitas coisas podem ocorrer em um intervalo de tempo $\Delta t$, porém algumas são mais prováveis do que outras. Como assim? Bem, vejamos... se $b$, $d$ e $\alpha$ são taxas para a ocorrência de cada cenário, a probabilidade de que cada um deles sozinho ocorra em um certo intervalo $\Delta t$ é dada pela quantidade de indivíduos no início deste intervalo, multiplicada pela taxa de ocorrência (também chamada de taxa de transição) e o intervalo de tempo em questão.  Por exemplo, a chance de que alguém se reproduza durante $\Delta t$ e a população vá para o valor $N$ é $(N-1) b \Delta t$. Se você parar para pensar, faz sentido que quanto mais indivíduos na população, maior a chance de algum deles se reproduzir, assim como essa chance também deve aumentar quanto maior for o intervalo $\Delta t$, ou maior for a taxa $b$.

Entretanto, para quem a população saia de $N-1$ indivíduos em $t$ e vá para $N$ indivíduos em $t + \Delta t$, devido apenas à reprodução, somente um indivíduo deve se reproduzir. Sendo assim, a chance $P$ de que isso ocorra se resume a probabilidade de um indivíduo se reproduzir E todos os outros não se reproduzirem. Se a chance de reprodução de um indivíduo é $b \Delta t$, a chance de que um indivíduo não se reproduza é $1 - b \Delta t$. Portanto

$$
\begin{align}
    P_{N-1 \rightarrow N}^{r} = (N-1)b \Delta t \left(1 - b \Delta t \right)^{N-2}
\end{align}
$$

Agora vamos imaginar como ficaria a probabilidade de que 2 indivíduos se reproduzissem. Nesse caso, a população precisaria estar, no instante de tempo $t$, com $N-2$ indivíduos e dois deles precisariam se reproduzir. Após a primeira reprodução, seria necessária uma segunda, agora com a população em $N-1$ e um intervalo de tempo restante $\Delta t' < \Delta t$. Assim, podemos dizer que a probabilidade $P$ de que o sistema saia do estado $N -2 $ e vá para $N$ durante $\Delta t$, apenas por reprodução, é

$$
\begin{align}
    P_{N-2 \rightarrow N}^{r} = (N-2)(N-1)b^2 \Delta t \Delta t' \left(1 - b \Delta t\right)^{N-3} .
\end{align}
$$

Caso a reprodução seja simultânea $\Delta t' = \Delta t$ e a população em ambas as reproduções é a mesma, portanto

$$
\begin{align}
    P_{N-2 \rightarrow N}^{r} = \left[(N-2) b \Delta t \right]^2 \left(1 - b \Delta t\right)^{N-3} .
\end{align}
$$

Podemos brincar com diversos cenários e inumeras formas nas quais a população pode estar em um nível $N' \neq N$ e chegar em $N$ entre os momentos $t$ e $t + \Delta t$.

> Aqui é importante notar que para calcular estas probabilidades eu tive que introduzir sutilmente a **4ª premissa** de que **os eventos são independentes**; ou seja, o que ocorre com seu vizinho pouco importa a você.

Note que para qualquer evento neste intervalo, há termos na probabilidade que dependem de $\left(\Delta t\right)^m$. Uma vez que iremos considerar intervalos de tempo pequenos, de forma que $\Delta t \rightarrow 0$, probabilidades com maiores potências de $\Delta t$ se tornam cada vez menos prováveis. Por causa disso, consideramos apenas as contribuições dos eventos únicos na dinâmica populacional, chamamos isso de aproximação de primeira ordem.

Voltemos nossa atenção para a pergunta: Qual é a probabilidade de que observemos a população com $N$ indivíduos após o intervalo de $t$ até $t + \Delta t$?

Como já sabemos os 4 possíveis eventos que os indivíduos em nossa população podem fazer, as possibilidades são

1. No momento $t$, o sistema já estava no estado $N$, e não mudou de estado durante o intervalo $\Delta t$;
    
2. No tempo $t$, o sistema estava com $N+1$ indivíduos e um indivíduo morreu por causas naturais, levando o sistema ao estado $N$;
    
3. Novamente, no tempo $t$ o sistema estava com $N+1$ indivíduos, porém um deles morreu devido à competição por recursos com seus vizinhos;
    
4. A população em $t$ era de $N-1$ indivíduos e um deles se reproduziu e gerou um novo integrante.

A probabilidade de transição para o item 2 $ d (N+1) \Delta t \left( 1 - d N \Delta t \right)^N = d (N+1) \Delta t + \mathcal{O}(\Delta t^2)$. De forma análoga para o item 3 $ \alpha (N+1) \Delta t + \mathcal{O}(\Delta t^2)$. Podemos representar a probabilidade total $P_{n+1 \rightarrow n} = (d + \alpha) (N + 1) \Delta t + \mathcal{O}(\Delta t^2)$.

Para o item 4, escrevemos diretamente $b(N-1) \Delta t + \mathcal{O}(\Delta t^2)$. E finalmente, o item 1 pode ser visto como 1 menos a probabilidade de 2, 3 e 4 ocorrerem.

Portanto, podemos escrever a probabilidade de observar o sistema com $n$ indivíduos, após um intervalo $\Delta t$ como

$$
\begin{align}
    \nonumber
    P(N;t+\Delta t) & = \underbrace{\overbrace{P(N-1;t)}^{\text{prob. estar em N-1 no instante t}} b (N-1) \Delta t}_{\text{prob. reprodução}} + \\
    \nonumber
    & + \underbrace{\overbrace{P(N+1;t)}^{\text{prob. estar em N+1 no instante t}} (d + \alpha)(N+1) \Delta t}_{\text{prob. morte}} + \\
    \nonumber
    & + \underbrace{\overbrace{P(N;t)}^{\text{prob. estar em N no instante t}} (1 - bN\Delta t)(1 - dN \Delta t)(1 - \alpha N \Delta t)}_{\text{prob. nada acontece}} + \\
    \nonumber
    & + \underbrace{\mathcal{O}(\Delta t^2)}_{\text{outros termos de ordem maior ou igual a } \Delta t^2}
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

E aqui parece que só deixamos as coisas mais confusas. A resposta para nossa pergunta parece depender da probabilidade de outros estados, que por sua vez tem suas próprias equações de probabilidade. A resposta parece longe e improvável, como se estivessemos adentro em um longo túnel escuro sem fim. Porém, como já dizia Tio Iroh em Avatar:

> "Às vezes, a vida é como este túnel escuro, você não pode sempre ver a luz no final do túnel, mas se você continuar em movimento, você chegará a um lugar melhor."

Ao invés de se perguntar então sobre a chance de que a população esteja em um determinado nível, faz mais sentido se perguntar como essa chance muda conforme o tempo passa. Para isso, dividimos a probabilidade por $\Delta t$ e como mencionado anteriormente, tomamos o limite $\Delta t \rightarrow 0$.

$$
\begin{align}
    \frac{\mathrm{d}}{\mathrm{d}t}P(N;t) = -P(N;t)(b+d+\alpha)n + P(N-1;t)b(N-1) + P(N+1;t)(N+1)(d + \alpha)
\end{align}
$$

Aaahh vejam só, uma equação diferencial! Felizmente elas são muito mais tratáveis e como dizia Steven Strogatz:

> "Desde Newton, a humanidade percebeu que as leis da natureza são sempre expressas na língua das equações diferenciais"

