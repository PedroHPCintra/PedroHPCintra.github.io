---
layout: sub-page_pt-br
---

# :thinking: Vacinados morrem mais?

Já em Maio de 2021, poucos meses após o inicio da vacinação contra a COVID-19 no Brasil, começamos a ver algumas matérias comentando sobre o [aumento de casos e óbitos em idosos vacinados](https://www.correiobraziliense.com.br/cidades-df/2021/05/4925148-cresce-o-numero-de-casos-de-covid-19-entre-idosos-vacinados.html). Imediatamente isso gera preocupação e duvidas. Se a vacina funciona, então porque a maior parte dos casos estão ocorrendo naqueles que se vacinaram?

Acontece que isso é normal, inclusive esperado, e não mostra nenhuma ineficácia na proteção das vacinas. Como nenhuma vacina tem 100% de eficácia, é normal que algumas pessoas sejam infectadas mesmo vacinadas, as chamadas _breakthrough infections_ em inglês. Se minha vacina tem uma eficácia de 90%, após eu vacinar 100 pessoas, 10 delas ainda vão poder ser infectadas mesmo vacinadas. Agora, se eu vacinar 200 pessoas, 20 delas podem ser infectadas ainda. Ou seja, quanto mais pessoas eu vacino, mais casos entre os vacinados eu vou ver. Se eu vacinar a população inteira, 100% dos casos vão ser infecções _breakthrough_. Portanto, ver notícias como "O numero de casos entre os vacinados aumentou" é apenas consequência de estarmos vacinando mais pessoas (e protegendo mais também).

Imaginem um cenário lindo onde 100% da população está vacinada com uma vacina 99.99% eficaz em prevenir óbitos. É claro que, já que a vacina não é 100% eficaz, e todo mundo ta vacinado, todos os óbitos vistos serão em vacinados, apesar de serem MUITO menores.

Podemos inclusive descrever o quanto casos/hospitalizações/óbitos de breakthrough (aqueles que afetam pessoas já vacinadas) vão representar do total de casos/hospitalizações/óbitos quantitativamente. Isso depende principalmente da % de pessoas já vacinadas e da efetividade ($V_E$) da vacina em prevenir o desfecho específico

$$ B(f_{v}|V_{E}) = \frac{f_{v} (1 - V_E)}{f_v (1 - V_E) + (1 - f_v)} $$

onde

$$
\begin{equation}
    V_E = \frac{1}{d_v} \sum_{j=1}^M \sum_{i=1}^N w_{ij} p_{ij}
\end{equation}
$$

sendo $d_v$ a disposição de vacinados a se exporem ao vírus, em comparação a não vacinados, $w_{ij}$ é a prevalência de uso da vacina $i$ na faixa etária $j$, $p_{ij}$ é a eficácia da vacina $i$ na faixa etária $j$ e $f_v$ é a fração da população que já foi vacinada.