# Não use Else

Por quê? Porque não serve para nada. Porque você não precisa e também nunca precisou.

O conceito dessa regra é o early return, que emprega o uso do “retorne seu valor o quanto antes”.

Sempre trabalhe com o return (ou continue), sabendo que ao cair em um return/continue o código abaixo não será executado o que ajuda na remoção do “else” ao inverter ou até modificar a validação antes usada.

## Primeiro Exemplo

### Antes

```php
<?php

protected function index()
{
    if ($this->security->isGranted('ADMIN')) {
        $view = 'admin.pages.index';
    } else {
        $view = 'home.pages.access_denied';
    }
    
    return view($view);
}
```

### Depois

```php
<?php

protected function index()
{
    if ($this->security->isGranted('ADMIN')) {
        return view('admin.pages.index');
    }
    
    return view('home.pages.access_denied');
}
```

## Segundo exemplo

### Antes

```php
<?php

foreach ($members as $member) {
    if ($member->paid()) {
        $report[] = [$member->name => 'Paid'];
    } else {
        $report[] = [$member->name => 'Not Paid'];
    }
}
```

### Depois

```php
<?php

foreach ($members as $member) {
    if ($member->paid()) {
        $report[] = [$member->name => 'Paid'];
        continue;
    }
    $report[] = [$member->name => 'Not Paid'];
}
```

[Anterior](/role-01.md) | [Próximo](/role-03.md)
