# Mémo PHP

_par flashjaysan_

## Introduction

## Balise PHP

Le code PHP s'intègre dans du code HTML dans une balise spéciale commençant par `<?php` suivi du code PHP et terminant par `?>`.

```php
<?php echo 'Hello, World!' ?>
```

## Ajouter du texte au document

Utilisez la fonction `echo`.

```php
<?php echo 'texte' ?>
```

Un raccourci permet d'éviter d'appeler la fonction.

```php
<?= 'texte' ?>
```

**Remarque :** Pour de gros blocs de texte, il est préférable de le placer en dehors des balises PHP.

```php
<?php if ($expression == true): ?>
  Ceci sera affiché si l'expression est vrai.
<?php else: ?>
  Sinon, ceci sera affiché.
<?php endif; ?>
```
