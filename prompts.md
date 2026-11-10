# Modelos de prompt

Modelos que eu uso de verdade para estudar e programar com IA. Cada um tem quatro partes: contexto, tarefa, restrições e formato da resposta. Depois de usar, anoto o que ajustei.

## 1. Explicar um conceito

**Quando uso:** quando encontro algo novo no roadmap e não entendo.

**Modelo:**

```
Sou estudante de ADS e estou aprendendo JavaScript. Já sei [o que você já sabe].
Me explique [conceito].
Use linguagem simples. Se usar um termo técnico, explique. Não use frameworks.
Se o exemplo usar algo que eu ainda não sei, explique num comentário do código.
Responda neste formato:
1. Uma frase resumindo.
2. A definição técnica, como é usada no trabalho, seguida de uma explicação simples.
3. Uma analogia do dia a dia.
4. Um exemplo de código curto e comentado.
5. Um erro comum de iniciante e a boa prática correspondente.
6. Uma pergunta para eu testar se entendi, sem a resposta.
```

**Uso real:** "o que é uma API e para que serve uma chave de API" (09/11/2026). O que funcionou: as analogias, o exemplo de código comentado e as boas e más práticas. Na pergunta de teste, acertei as consequências de uma chave vazada, mas não como ela vaza: o código do front-end roda no navegador, e qualquer pessoa vê a chave apertando F12.

**O que ajustei:**
- Passei a usar só a lista do que eu sei, sem link: a IA não conseguiu abrir o link do meu repositório.
- Pedi para explicar num comentário o que eu ainda não sei: o exemplo usou async/await e JSON, que eu ainda não tinha estudado.
- Acrescentei a definição técnica usada no trabalho e a boa prática junto do erro comum.

## 2. Revisar meu código

**Quando uso:** quando termino um código e quero entender o que melhorar sem receber a resposta pronta.

**Modelo:**

```
Aja como um revisor de código. O código foi escrito por um estudante de ADS com nível [nível atual] de JavaScript e deve funcionar da seguinte maneira: [lógica do código ou bug encontrado].
Sua tarefa é revisar o código enviado e me apontar erros, boas e más práticas e o que eu devo manter, melhorar ou evitar. Aponte possíveis falhas, soluções melhores e comportamentos inesperados.
Nunca dê as respostas: me force a entender. Se eu não entender, use analogias simples e diretas (estradas, restaurantes, situações do dia a dia), a que melhor se encaixar na minha dúvida. Quando precisar me mostrar um exemplo, crie um código curto e comentado de outra situação parecida, nunca o meu código corrigido. Se a correção exigir uma função ou método que eu ainda não conheço, me diga o nome e mostre um exemplo em outra situação.
Classifique os erros assim: grave é o que quebra o código, dá resultado errado ou cria risco de segurança; médio é o que funciona, mas falha em algum caso; pequeno é nome, formatação ou legibilidade. Se não tiver certeza de que algo é um erro, diga que é uma suspeita.
Formato: na primeira resposta, mostre o total de erros separado por categoria e, em seguida, só o primeiro erro, indicando a linha ou o bloco. Siga sempre a ordem: erros graves, médios, pequenos e, por último, as boas práticas. Só mostre o próximo erro depois que eu corrigir o atual com sucesso. Depois de cada correção, me diga como testar se ela funcionou.

<codigo>
[cole o código aqui]
</codigo>
```

**O que ajustei antes do primeiro uso:**
- Tirei uma contradição: eu pedia para a IA nunca dar a resposta e, ao mesmo tempo, mostrar exemplos do meu erro. Agora os exemplos são de outra situação parecida.
- Defini o critério de cada categoria de erro: grave, médio e pequeno.
- Limitei a revisão ao código enviado, pedi a linha de cada erro e que a IA avise quando for só uma suspeita.
- Coloquei o código entre as tags `<codigo>` para separar os dados das instruções.

**Uso real:** revisão da função `registrarPrecos`, do meu projeto de automação da carteira (10/11/2026). Placar inicial: 0 graves, 3 médios (intervalo fixo, preço inválido gravado como preço e registro em fim de semana) e 1 pequeno (falta de comentário). Corrigindo um erro por vez, surgiram dois problemas novos: uma regressão, em que a correção do intervalo sumiu, e um `if` sem chaves que fazia a função sair sempre. Os dois só apareceram porque testei cada correção. O que mais me ajudou: os exemplos de outra situação, um erro por vez e os testes.

**O que ajustei depois do primeiro uso:**
- Pedi para a IA mostrar o nome e um exemplo de funções que eu ainda não conheço: sem isso eu travava, porque não tinha como adivinhar `getLastRow()` ou `getDay()`.
- Pedi para a IA dizer como testar cada correção: os testes pegaram uma regressão e um erro grave que eu não tinha previsto.
