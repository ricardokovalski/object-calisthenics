# Não use Getters ou Setters

No primeiro momento pode parecer uma regra bem estranha, no entanto, a ideia é bem básica. Você retira os getters e setters para poder adicionar decisões no próprio objeto. Qualquer decisão baseada inteiramente no estado de um objeto deve ser feita diretamente nele.

São muitos os benefícios quando aplicamos essa ideia. Reduzimos a duplicação de regras e damos uma melhor compreensão àquele objeto.

Também enriquecemos nosso objeto com lógica e métodos mais valiosos e significativos, não apenas o usando como uma classe com apenas dados.

### Antes

```php
<?php

class Buyer {

    protected $name;
    protected $purchases;
    
    public function getName() {/**/}
    public function setName($name) {/**/}
    
    public function getPurchases() {/**/}
    public function setPurchases($purchases) {/**/}
}
```

### Depois

```php
<?php

class Buyer {

    protected $name;
    protected $purchases;

    public function addNewPurchase()
    {
        $this->purchases++;
    }
}
```

[Anterior](/role-08.md)
