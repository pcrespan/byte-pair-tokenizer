## Descrição
Este código é um exemplo simples de byte pair encoding, usado em LLMs como GPT, e que permite que palavras fora do vocabulário do dataset possam ser tokenizados normalmente.

Por exemplo, nesse código temos "someunknownPlace", que provavelmente seria considerado fora do vocabulário do modelo de linguagem, mas que nesse caso pode ser convertido por conta da quebra da palavra em tokens menores.

Inicialmente, é feito um pré processamento nas palavras, em que é colocado "</w>" em cada palavra para simbolizar seu fim. Após isso, é calculada a frequência de cada palavra no texto, e a frequência de cada letra é colocada em uma tabela de frequências. 

Com isso, os tokens (letras) mais comuns são unidos. Nesse caso, as duas letras mais comuns formariam um "par". Assim, um novo token é formado, e o número de ocorrências do mesmo é subtraído do valor total das ocorrências de cada letra que formava o par para o novo token.

O processo é repetido até que um critério de parada seja atingido, como o número de tokens ou o número de iterações.