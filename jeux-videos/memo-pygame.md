# Mémo pygame

*par flashjaysan*

## Présentation

pygame est une bibliothèque pour Python destiné au développement de jeux vidéos.

**Remarque :** Le système de coordonnées de pygame inverse l'axe vertical par rapport au système classique mathématique. Les valeurs augmentent donc vers le bas.

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
dimensions = largeur, hauteur
surface_ecran = pygame.diplay.set_mode(dimensions)
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

## Quitter proprement

```python
pygame.quit()
```

## Squelette de base

```python
import pygame


pygame.init()
resolution = (640, 360)
window = pygame.display.set_mode(resolution)
pygame.display.set_caption('Title')
is_running = True
while is_running:
    pygame.time.delay(33)
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            is_running = False
pygame.quit()
```

## Afficher un rectangle

```python
white_color = 255, 255, 255
black_color = 0, 0, 0
position_x = 0
position_y = 0
width = 100
height = 50
rectangle = (position_x, position_y, width, height)
window.fill(black_color)
pygame.draw.rect(window, white_color, rectangle)
pygame.display.update()
```

## Déplacer un rectangle avec le clavier

```python
speed = 5
keys_pressed = pygame.key.get_pressed()
if keys_pressed[pygame.K_LEFT]:
    position_x -= speed
if keys_pressed[pygame.K_RIGHT]:
    position_x += speed
if keys_pressed[pygame.K_UP]:
    position_y -= speed
if keys_pressed[pygame.K_DOWN]:
    position_y += speed
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


