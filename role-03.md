# Envolva seus tipos primitivos

Essa regra na realidade é uma das mais simples, pois ela diz que você deve encapsular todos os tipos primitivos dentro dos objetos, prevenindo assim Primitive Obsession Anti-Pattern.

Um int por conta própria, é um tipo sem significado. Quando se tem um método que um de seus parâmetros é um int, o nome do método precisa fazer todo o trabalho para expressar a intenção, ou então, o programador tem que perder um certo tempo tentando entender o intuito.

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
