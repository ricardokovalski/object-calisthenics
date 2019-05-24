# Use apenas um ponto por linha

Esse “ponto” é o que você usa para chamar métodos em Java ou C#; no caso do PHP seria uma seta.

Esta regra é o exemplo da Lei de Deméter: você nunca deve usar mais de um operador de objeto, ou seja, você não deve encadear chamadas de métodos.

Porém, existe uma exceção. Ela não se aplica a Fluent Interfaces e a qualquer coisa que se implemente o Chaining Pattern (muito usado por exemplo em Query Builders).

> **_NOTE:_**  The note content.
