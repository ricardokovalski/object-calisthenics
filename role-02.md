# Não use Else

A ideia principal é: Negue todo o possível em seu método antes. Dessa forma assumimos retornos antecipados e definimos um fluxo de trabalho padrão.

### Antes

```php
<?php

protected function indexAction()
{
    if ($this->security->isGranted('ADMIN')) {
        $view = 'admin/index.html.twig';
    } else {
        $view = 'home/access_denied.html.twig';
    }
    
    return $this->render($view);
}
```

### Depois

```php
<?php

protected function indexAction()
{
    if ($this->security->isGranted('ADMIN')) {
        return $this->render('admin/index.html.twig');
    }
    
    return $this->render('home/access_denied.html.twig');
}
```
