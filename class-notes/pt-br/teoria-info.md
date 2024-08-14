---
layout: sub-page_pt-br
---

# Teoria da informação e Wordle

Você talvez já tenha visto ou jogado o jogo _wordle_, ou o _termo_ (a versão pt-br do _wordle_). É um jogo onde todos os dias uma palavra secreta é escolhida, eu objetivo é adivinhar a palavra, em no máximo 6 tentativas, com base em algumas dicas. Você começa chutando uma palavra qualquer (só podem ser palavras de 5 letras) e o jogo te diz se as letras da palavra que você chutou existem na palavra secreta, se não existem, e se estão na mesma posição que você colocou.

Por exemplo, se a palavra é **beijo** e seu primeiro chute é **jeito**, o jogo irá de dizer que o **j** está na palavra secreta, porém em outra posição; o **e** está na palavra secreta e está na posição correta; o **i** também, o **t** não está na palavra secreta; e o **o** está e também está na posição correta, assim como o **ei**. O jogo diz isso colorindo a posição de cada palavra para você, tipo assim:

> Tentativa: **jeito** \
> Feedback: $\color{yellow}{j}\color{green}{ei}\color{grey}{t}\color{green}{o}$

Com essa informação, você chuta uma nova palavra. Tente jogar uma partida aqui: [termo.pt](https://termo.pt/index.html)

Acontece que no primeiro chute, você não tem nenhuma informação sobre a palavra secreta, então vem a pergunta: **Existe uma palavra que é um chute inicial melhor do que outras?**

A princípio pode parecer que não, a resposta pode ser qualquer palavra e a chance de que você acerte no primeiro chute é ínfima. De acordo com o [repositório de palavras da língua portuguesa do IME-USP](https://www.ime.usp.br/~pf/dicios/), há 5481 palavras com cinco letras na língua portuguesa brasileira, excluindo nomes de cidades. Portanto existe 1 em 5481 chances de você acertar a palavra de primeira, supondo que todas as 5841 palavras estão inclusas como possíveis respostas para o jogo.

Mas o nosso objetivo no primeiro chute não deve ser acertar de primeira, mas sim escolher a palavra que nos de as informações mais uteis para pensarmos em qual deve ser a palavra secreta. Por exemplo, sabemos que muitas palavras do português possuem a letra **a** e **e**, enquanto pouquíssimas possuem a letra **x**. Saber quais letras estão inclusas ou não, é uma informação valiosa. Então voltamos à pergunta: **Existe uma palavra que é um chute inicial melhor do que outras?** Ou melhor ainda, **existe uma palavra que nos dê mais informação do que outras?**

O meu objetivo aqui nesse texto é mostrar que sim, e encontrar qual é a melhor palavra para servir de chute inicial no _termo_ usando teoria da informação. Antes vale dizer que estas anotações são praticamente uma tradução do vídeo [Solving Wordle using information theory](https://youtu.be/v68zYyaEmEA?si=Xzmcv4gRc4jS0xxv), do canal [3Blue1Brown](https://www.youtube.com/@3blue1brown). Se você é confortável com inglês, acredito que valha mais a pena assistir ao vídeo do que ler esse texto, aqui estarei basicamente aplicando o que é mostrado no vídeo para o _termo_ ao invés do _wordle_, ou seja, usando português ao invés de inglês.

## O melhor chute inicial

Se você já jogou _termo_ na época em que ele foi uma febre, você provavelmente tinha uma palavra favorita que gostava de usar nas primeiras tentativas.

Para quantificarmos qual o melhor chute inicial, vamos supor que inicamos com a palavra **beijo**. Não sabemos qual é a palavra secreta, e portanto não sabemos qual será o feedback que o jogo nos dará. E se o feedback for por exemplo:

:red_circle: :yellow_circle: :yellow_circle: :red_circle: :red_circle:

Ou seja, as letras **e** e **i** estão na resposta final, porém em posições diferentes, enquanto que as demais não estão. Essa informação nos permite eliminar muitas palavras, como "bomba", já que sabemos que **b** não está contido na resposta. Na verdade, sobram 293, das 5481 palavras. E se o feedback do jogo fosse outro, por exemplo

:red_circle: :large_blue_circle: :yellow_circle: :red_circle: :red_circle:

Nesse caso restariam 142 palavras.