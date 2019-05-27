# Apenas um nível de identação por método

A ideia principal é que cada método faça apenas uma ação. Desse modo, estamos facilitando a leitura e a manutenção do código. Além de promovermos o Single Responsability Principle e evitarmos o efeito Hadouken.

Você pode extrair comportamentos para outros métodos garantindo um único nível de identação. Fazendo isso, você também está aplicando o Extract Method Pattern.

### Antes

```php
<?php

public function show($slug)
{
    $lesson = $this->repository->findBySlug($slug);
    
    if ($lesson) {
        if (!empty($lesson->thumb_url)) {
            $this->seo()->addImages($lesson->thumb_url);
        }
        
        if ($lesson->track) {
            $this->seo()->setTitle($lesson->title.' ['.$lesson->track->title.']');
        } else {
            $this->seo()->setTitle($lesson->title);
        }
        
        $this->seo()->setDescription($lesson->description);
        
        return $this->view('lessons::show')->with(compact('lesson'));
    }
    
    return redirect(route('lesson.index'));
}
```

### Depois

```php
<?php

public function show($slug)
{
    $lesson = $this->repository->findBySlug($slug);
    
    if ($lesson) {
        $this->addThumbToImages($lesson->thumb_url);
        $trackTitle = ! $lesson->track ? '' : '['.$lesson->track->title.']';
        $this->seo()->setTitle($lesson->title . $trackTitle);
        $this->seo()->setDescription($lesson->description);
        return $this->view('lessons::show')->with(compact('lesson'));
    }
    
    return redirect(route('lesson.index'));
}

protected function addThumbToImages($thumbURL)
{
    if (empty($thumbURL)) {
        return false;
    }
    
    return $this->seo()->addImages($thumbURL);
}
```

[Anterior](/README.md) | [Próximo](/role-02.md)
