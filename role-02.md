# Não use Else

Por quê? Porque não serve para nada. Porque você não precisa e também nunca precisou.

Negue todo o possível em seu método. Dessa forma assumimos retornos antecipados e definimos um fluxo de trabalho padrão.

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

[Anterior](/role-01.md) | [Próximo](/role-03.md)
