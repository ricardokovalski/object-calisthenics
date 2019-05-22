# Não use Else

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
