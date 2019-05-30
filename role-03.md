# Envolva seus tipos primitivos

Essa regra diz que você deve encapsular todos os tipos primitivos (int, float, bool e string) dentro dos objetos, prevenindo assim *Primitive Obsession Anti-Pattern*.

Essa técnica vêm de uma aplicação do DDD (*Domain-Driven Design*) chamada de Value Object, onde temos um objeto-valor pequeno, que irá cuidar de um tipo de dado específico.

## Exemplo

### Antes

```php
<?php

class Order
{
    public function notifyBuyer($email)
    {
        if (filter_var($email, FILTER_VALIDATE_EMAIL) === false) {
            throw new InvalidEmailException;
        }
        
        return $this->repository->sendEmail($email);
    }
}
```

### Depois

```php
<?php

class Email {

    public $email;
    
    public function __construct($email)
    {
        if (filter_var($email, FILTER_VALIDATE_EMAIL) === false) {
            throw new InvalidEmailException;
        }
        
        return $this->email = $email;
    }
}

class Order
{
    public function notifyBuyer($email)
    {
        return $this->repository->sendEmail(new Email($email));
    }
}
```

> **_ATENÇÃO:_** Um possível problema dessa abordagem é que ela adiciona complexidade à base de código. Na tradução dos Object Calisthenics, é colocado que todos os tipos primitivos devem ser envolvidos em classes, porém, sabemos que em PHP isso pode se tornar improdutivo e desnecessário, portanto, analise o quanto aquela entrada ou tipo pode sofrer mudança, se precisa de validação, normalização etc, só aplique-o se tiver uma real justificativa.

[Anterior](/role-02.md) | [Próximo](/role-04.md)
