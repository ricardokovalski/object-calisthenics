# Envolva suas collections em classes

A regra diz que se você tiver um conjunto de elementos e quiser manipulá-los, é necessário criar uma classe dedicada (collection) apenas para este conjunto. Assim, ao atualizar aquele valor, com certeza será em sua collection.

Seguindo o comportamento dessa regra, você deixa os comportamentos relacionados.

O maior objetivo dessa regra é aderir o Single Responsibility Principle e High Cohesion.

### Exemplo

```php
<?php

foreach ($customers as $customer) {
    if ($customer->isGoldAccount()) {
        $customer->addBonus(new Money('R$ 50,00'));
    }
}
```

Nesse exemplo queremos adicionar um bônus aos clientes do tipo gold. $customers é um array e por isso para modificar a coleção, precisamos iterá-la com um foreach e ainda internamente verificar se o tipo do cliente é gold.

Então se usarmos uma classe que envolva essa coleção de customers, ou seja, uma CustomerCollection e nessa classe existisse o método filterGoldAccounts para filtrar o tipo de cliente e o método addBonus para adicionar um bônus aos clientes, a usabilidade ficaria da seguitne forma:

```php
<?php

$customersCollection = new CustomersCollection;

$goldCustomers = $customersCollection->filterGoldAccounts();

$goldCustomers->addBonus(new Money('R$ 50,00'));

$goldCustomers->persists();
```
Assim, temos coleções que são específicas e inteligentes o suficiente para melhorar a usabilidade e evitar erros.

[Anterior](/role-03.md) | [Próximo](/role-05.md)
