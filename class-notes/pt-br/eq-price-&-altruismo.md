---
layout: sub-page_pt-br
---

Uma pergunta pertinente em ecologia evolutiva é se podemos prever como características em indivíduos devem mudar entre uma geração e outra. Mas responder essa pergunta não é uma tarefa nenhum pouco fácil. Um início de resposta foi proposta por George R. Price em 1970 [[Ref. 1](https://doi.org/10.1038/227520a0)]. Vamos dar uma olhada nessa elaboração e discutir alguns resultados dela :monocle_face:.

# Equação de Price

Imagine uma população de $n$ indivíduos adultos, nesta população uma dada característica hereditária pode possuir $m$ valores diferentes, sendo cada valor dado por $z$. $z$ pode se referir ao tamanho do bico de uma ave, por exemplo, e $m$ englobar todos os tamanhos de bicos diferentes que esta espécie de aves tem. Ou ainda, $z$ pode se referir a um genótipo específico que resulta na expressão de uma característica. Entre uma geração e outra, os $n$ indivíduos geram $n'$ filhotes. Cada filhote possui um valor $z'$ para esta mesma característica herdável. Portanto, podemos definir a população total de "pais" e "filhos" nesta população, em termos de uma soma sobre todos os indivíduos que possuem cada valor possível de $z$ e $z'$. Desta forma, sendo $m$ valore possíveis de $z$, $n_1$ representa a quantidade de indivíduos que possuem o valor $z_1$ para a característica (lembrando que $z_1$ pode se referir diretamente ao valor da característica expressa, como no caso do bico das aves, ou um tipo de genótipo), $n_2$ é a quantidade de indivíduos que possuem o valor $z_2$ e assim por diante:

$$
\begin{align}
    & n := \sum_{i}^m n_i \\
    & n' := \sum_{i}^m n'_i.
\end{align}
$$

Se quisermos investigar como a distribuição de uma dada característica herdável $z$ muda entre gerações, é interessante definir as frequências nas quais cada valor possível de $z$ ocorre na população. Isto é, a fração do total de indivíduos que possui cada valor $i$ possível para $z$

$$
\begin{align}
    & q_i := \frac{n_i}{n} \\
    & q'_i := \frac{n'_i}{n'}.
\end{align}
$$

Pela própria definição, estas frequências quando somadas para todos os $i$, são iguais a 1. Sendo assim, podemos encará-las de forma que representem a probabilidade de que, ao sortearmos aleatóriamente um indivíduo em $n$ ou $n'$, este possua o valor $z_i$ ou $z'_i$ para a característica herdável em questão. Cada característica (ou genótipo, se preferir), confere ao indivíduo uma certa aptidão, que aqui será definida em termos da razão entre a quantidade de filhos com o valor $z_i$ e a quantidade de pais com este mesmo valor $z_i$. Ou seja, se a quantidade de filhos que nascem com $z_i$ aumentar, em relação à quantidade de pais, a característica tende a se tornar mais dominante na população.

$$
\begin{align}
    w_i := \frac{n'_i}{n_i}.
\end{align}
$$

Até o momento apenas trabalhamos com definições. Começamos agora a explorar como a característica $z_i$ muda entre a geração dos pais e dos filhos. Como vários indivíduos possuem valores de $z$ e $z'$ diferentes, $z$ possui uma distribuição na população, portanto torna-se útil nos atentarmos para a média de $z$ nas subpopulações de pais e filhos, denotada pelo valor esperado $E[z]$ (em estatística, dizer o valor esperado de uma variável aleatória é o mesmo que dizer a média da distribuição que descreve esta variável)

$$
\begin{align}
    & E[z] = \left \langle z \right \rangle = \sum_{i}^m q_i z_i \\
    & E[z'] = \left \langle z' \right \rangle = \sum_{i}^m q'_i z'_i,
\end{align}
$$

e de forma análoga, a aptidão média é representada por

$$
\begin{align}
    E[w] = \left \langle w \right \rangle = \sum_{i}^m q_i w_i.
\end{align}
$$

Agora, podemos reescrever $q_i w_i$ da seguinte forma, usando as definições de $q_i$ e $w_i$:

$$
\begin{align}
    q_i w_i = \frac{n_i}{n} \frac{n'_i}{n_i} = \frac{n'_i}{n} \underbrace{\frac{n_i}{n_i}}_{=1} = \frac{n'_i}{n} \underbrace{\frac{n'}{n'}}_{=1} = \frac{n'_i}{n'} \frac{n'}{n} = q'_i \frac{n'}{n}.
\end{align}
$$

E portanto

$$
\begin{align}
    \left \langle w \right \rangle = \frac{n'}{n} \underbrace{\sum_{i}^m q'_i}_{=1} = \frac{n'}{n},
\end{align}
$$

então $q_i w_i = q'_i \left \langle w \right \rangle$, uma vez que a soma em $q'_i$ é igual à 1 e a soma em $q_i w_i$ é igual a $\left \langle w \right \rangle$. Finalmente, se estamos supondo que $z_i$ possui relação com $w_i$, isto é, um dado valor para esta característica possui influencia na aptidão dos indivíduos, podemos calcular a covariância entre ambas as distribuições, a de $z_i$'s e de $w_i$'s

$$
\begin{align}
    \mathrm{cov}[w, z] := E[w z] - E[w]E[z] = \sum_{i}^m q_i w_i z_i - w z.
\end{align}
$$

Ao mesmo tempo, a mudança entre uma geração e outra no valor de $z_i$, isto é $\Delta z_i = z_i - z'_i$, multiplicado pelo fitness associado ào $i$-ésimo valor de $z$ é dado por

$$
\begin{align}
    E[w \Delta z] = \sum_{i}^m q_i w_i (z_i - z'_i) = \sum_{i}^m q_i w_i z_i - \sum_{i}^m q_i w_i z'_i.
\end{align}
$$

Aqui o leitor pode se encontrar confuso a respeito do significado de $w_i \Delta z_i$, esta grandeza nos informa a variação de $z_i$ entre uma geração e outra, associada à aptidão deste valor para a característica herdável. Discutirei mais sobre o significado deste termo posteriormente.

A soma das duas equações mostradas acima nos dão

$$
\begin{align}
    \mathrm{cov}[w, z] + E[w \Delta z] = \sum_{i}^m q_i w_i z_i - wz + \sum_{i}^m q_i w_i z_i - \sum_{i}^m q_i w_i z'_i = \sum_{i}^m q_i w_i z'_i - wz,
\end{align}
$$

e utilizando $q_i w_i = w q'_i$ reescrevemos

$$
\begin{align}
    \mathrm{cov}[w, z] + E[w \Delta z] = w\sum_{i}^m q'_i z'_i - wz = w z' - wz = w \Delta z.
\end{align}
$$

Chegamos então na equação de Price:

$$
\begin{align}
    \boxed{\Delta z = \frac{1}{w} \mathrm{cov}[w, z] + \frac{1}{w} E[w \Delta z]}.
\end{align}
$$

Esta equação afirma que a mudança na média de uma dada característica hereditária $z$ entre duas gerações é dada pela covariância entre os valores $z_i$ e $w_i$, somada à mudança esperada nos valores desta característica devido à aptidão. Quando a covariância entre os valores da característica e a aptidão é positiva, esta característica tende a aumentar na população, quando é negativa, ela tende a diminuir. O segundo termo $E[w \Delta z]$ representa o quanto de $\Delta z$ muda por fatores além da seleção, como deriva genética, viéses de mutação. Na formulação feita por Price em 1970, este termo foi chamado de "mudança ambiental".

# Regra de Hamilton

## Abordagem 1

A equação de Price vista anteriormente nos informa como o valor médio de características hereditárias muda entre gerações. Se supormos que mais do que algumas características físicas, mas também alguns comportamentos sociais são governados de forma hereditária, podemos mostrar como a equação de Price nos permite chegar à regra de Hamilton, proposta por Hamilton em 1964. E antes de começarmos vale uma grande ressalta aqui a respeito da simplificação assumida aqui, de que o comportamento social dos indivíduos em uma população é totalmente (ou ao menos majoritariamente) ditado pelo comportamento dos pais deste indivíduo, e fatores ambientais não. Isso claramente não é o caso de seres humanos e vários animais com comportamento social, portanto muita cautela aqui antes de usar isso como argumento para justificar suas crenças pessoais. O processo descrito aqui para chegar na regra de Hamilton é baseado na [ref. 3](https://doi.org/10.1093/bjps/axt016).

Vamos estudar aqui o caso do altruismo, a disposição de indivíduos de ajudarem outros,mesmo ao custo de sua própria sobrevivência ou reprodução. Como uma aproximação, vamos considerar que a aptidão de um indivíduo que possui um certo comportamento social $g_i$ é dado por uma relação linear

$$
\begin{align}
    w_i = \alpha_i - c g_i + b \left \langle g \right \rangle + \varepsilon
\end{align}
$$

Onde $\alpha_i$ é a aptidão base não relacionada com o comportamento social, e sim a outros fatores que influenciam a aptidão do indivíduo. $g$ dita a atitude social, podendo representar por exemplo um genótipo que resulta em no grau de comportamento social altruístico deste indivíduo. $c$ é o custo de aptidão associado à atitude social, $b$ é o ganho em aptidão associado ao grau de atitude social médio dos parceiros sociais de $g_i$. E por fim $\left \langle g \right \rangle$ é o grau de altruísmo médio da população, e $\varepsilon$ é uma variável aleatória, representando variações aleatórias e sem correlação com o indivíduo, mas que afetam sua aptidão.

É claro que expressar a aptidão de um indivíduo dessa forma já constitui uma suposição adotada. Nada nos garante que a relação entre aptidão e o grau de altruísmo é linear, qualquer um destes termos poderia ser diferente. Mas uma relação linear é sempre o mais simples possível, e sem nenhum argumento que justifique uma relação não linear, não há motivo para começar supondo o mais complexo.

Acoplando essa expressão de aptidão na equação de Price, obtemos

$$
\begin{align}
    \Delta g = \frac{1}{w} \left( \mathrm{cov}[g, \alpha] - c \mathrm{var}[g] + b \mathrm{cov}[g,\left \langle g \right \rangle] + \mathrm{cov}[g,\varepsilon] \right)
\end{align}
$$

Note que e equação de Price usada aqui inclui apenas o primeiro termo, o segundo foi deixado de fora pois estamos interessados apenas em investigar a permanência de comportamento altruístico por meios da seleção natural, e não outros mecanismos de seleção neutra. Por definição $\mathrm{cov}[g, \alpha] = 0$ e $\mathrm{cov}[g,\varepsilon] = 0$, já que $\alpha$ e $\varepsilon$ são totalmente independentes do genótipo altruístico e só dependem das demais características dos indivíduos e de componentes aleatórios, respectivamente. A equação de Price fica então

$$
\begin{align}
    \Delta g & = \frac{1}{w} \left( b\mathrm{cov}[g,\left \langle g \right \rangle] - c \mathrm{var}[g] \right) = \\
    & = \frac{1}{w} \left( b \frac{\mathrm{cov}[g,\left \langle g \right \rangle]}{\mathrm{var}[g]} - c \right)
\end{align}
$$

Uma vez que $\mathrm{var}[g]$ e $w$ não podem ser negativos, para o genótipo médio da população $g$ aumentar devido ao altruísmo, é necessário que

$$
\begin{align}
     & b \frac{\mathrm{cov}[g,\left \langle g \right \rangle]}{\mathrm{var}[g]} - c > 0 \Rightarrow \\
     & \frac{\mathrm{cov}[g,\left \langle g \right \rangle]}{\mathrm{var}[g]} > \frac{c}{b}
\end{align}
$$

A covariância entre o genótipo individual $g_i$ e o genótipo médio do grupo social $\left \langle g \right \rangle$, dividido pela variância no genótipo $g_i$ é o grau de parentesco entre os indivíduos que realizam a ação social e os que recebem.

# Referências e leituras

1. Price, G. R. (1970). Selection and Covariance. _Nature_, 227, 520–521. [https://doi.org/10.1038/227520a0](https://doi.org/10.1038/227520a0)

2. Price, G. R. (1972). Extension of covariance selection mathematics. _Annals of human genetics_, 35(4), 485-490. [https://doi.org/10.1111/j.1469-1809.1957.tb01874.x](https://doi.org/10.1111/j.1469-1809.1957.tb01874.x)

3. Birch, J. (2014). Hamilton’s rule and its discontents. _The British Journal for the Philosophy of Science._ [https://doi.org/10.1093/bjps/axt016](https://doi.org/10.1093/bjps/axt016)