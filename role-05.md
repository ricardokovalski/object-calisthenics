# Use apenas um ponto por linha

Esse “ponto” é o que você usa para chamar métodos em Java ou C#; no caso do PHP seria uma seta.

Facilita a leitura do código e reforça o Open-close principle.

Esta regra é o exemplo da Lei de Deméter: você nunca deve usar mais de um operador de objeto, ou seja, você não deve encadear chamadas de métodos.

> **_ATENÇÃO:_**  Há uma exceção. Ela não se aplica a Fluent Interfaces e a qualquer coisa que se implemente o Chaining Pattern (muito usado por exemplo em Query Builders).

[Anterior](/role-04.md) | [Próximo](/role-06.md)
