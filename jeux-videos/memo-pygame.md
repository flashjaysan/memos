# Mémo pygame

*par flashjaysan*

## Installation

```python
pip install pygame
```

**Remarque :** Sur Windows, vous aurez peût-être besoin d'exécuter la commande en étant administrateur.

## Préparation

- Créez un fichier source `main.py` à l'emplacement de votre choix.
- Vous pouvez faire référence à des ressources (sprites, sons, etc...) depuis cet emplacement.
- Importez le module pygame :

```python
import pygame
```

- Initialisez le module pygame :

```python
pygame.init()
```

## Définir le titre et l'icône de la fenêtre

```python
pygame.display.set_caption(titre, icone)
```

```python
pygame.display.set_caption(titre)
```

## Définir les dimensions de la fenêtre

```python
surface_ecran = pygame.diplay.set_mode(largeur, hauteur)
```

## Charger une image

```python
fond = pygame.image.load(chemin)
```

## Lancer la boucle de jeu

```python
running = True

while running:
    pass
```

## Afficher une image

```python
surface_ecran.blit(fond, (x, y))
```

## Rafraîchir l'affichage

```python
pygame.display.flip()
```

## Gérer les événements

```python
for event in pygame.event.get():
    pass
```

### Gérer la fermeture de fenêtre

```python
if event.type == pygame.QUIT:
    running = False
    pygame.quit()
```

```python

```

```python

```

```python

```

```python

```

```python

```

```python

```

```python

```

```python

```

```python

```

```python

```

```python

```

```python

```

```python

```

```python

```

```python

```

```python

```


