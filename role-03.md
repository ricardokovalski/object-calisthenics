# Envolva seus tipos primitivos

Essa regra na realidade é uma das mais simples, pois ela diz que você deve encapsular todos os tipos primitivos (int, float, bool e string) dentro dos objetos, prevenindo assim Primitive Obsession Anti-Pattern.

Essa técnica vêm de uma aplicação do DDD (Domain-Driven Design) chamada de Value Object, onde temos um objeto-valor pequeno, que irá cuidar de um tipo de dado específico.

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

[Anterior](/role-02.md) | [Próximo](/role-04.md)
