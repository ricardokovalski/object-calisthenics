# Não abrevie

São incontáveis as vezes em que nós abrimos um código e encontramos uma variável $i.

Por mais comum que seja encontrarmos essa variável em vários projetos em funções de iterações, imagine entender o que seria a variável $n ou $x.

E por mais tentador que seja abreviarmos nomes de variáveis, classes ou métodos, lute contra essa tentação! As abreviações podem ser confusas e tendem a esconder problemas maiores.

Analisar o motivo de estar abreviando é uma ótima solução. Será que isso pode estar acontecendo por estar digitando a mesma palavra várias vezes? Se for verdade, talvez você deva reanalisar seu código para remover duplicações.

Outro caso recorrente é quando os nomes dos seus métodos ou variáveis estão ficando longos; isso pode ser um sinal de que sua classe esteja fazendo coisas que não pertencem a ela.

Dica importante: Sempre tente manter nome de suas classes, métodos ou variáveis, com apenas duas palavras, e que essas palavras não sejam repetitivas.

Considere uma classe com o nome Profile. Um método dessa classe não tem nenhuma necessidade de se chamar createProfile. Basta chamá-lo de create, pois podemos invocá-lo com profile->create(), mantendo uma representação clara do que será realizado.
