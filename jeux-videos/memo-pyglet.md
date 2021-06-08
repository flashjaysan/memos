# Mémo pyglet

*par flashjaysan* 

## introduction

pyglet est une bibliothèque multimédia et de fenêtrage pour Python destiné au développement de jeux et autres applications visuellement riches. pyglet supporte le fenêtrage, la gestion des évènements de l’interface utilisateur, les graphismes OpenGL, le chargement d’images de de vidéos, et la lecture de sons et de musiques. pyglet fonctionne sur windows, OS X et Linux.

**Attention !** Le système de coordonnées du module pyglet est celui utilisé en mathématiques : Le coin inférieur gauche de la fenêtre est situé aux coordonnées `0, 0` et l’axe Y est orienté vers le haut.

## Installer pyglet

Ouvrez un terminal et saisissez la commande suivante :

```
pip install pyglet
```

## Importer le module

En tête de votre fichier source importez le module `pyglet` :

```python
import pyglet
```

## Créer une fenêtre

Pour créer une fenêtre, utilisez le code suivant :

```python
window = pyglet.window.Window()
```

Ajoutez la ligne suivante à la fin de votre code pour empêcher la fermeture de la fenêtre :

```python
pyglet.app.run()
```

Vous pouvez paramétrer la taille de la fenêtre en passant les dimensions :

```python
window = pyglet.window.Window(width=640, height=360)
```

Ou créer un affichage plein écran :

```python
window = pyglet.window.Window(fullscreen=True)
```

Voici la signature complète du constructeur avec ses valeurs par défaut :

```python
window = pyglet.window.Window(width=None,
                             height=None,
                             caption=None,
                             resizable=False,
                             style=None,
                             fullscreen=False,
                             visible=True,
                             vsync=True,
                             display=None,
                             screen=None,
                             config=None,
                             context=None,
                             mode=None)
```

Attachez à cet objet les évènements que vous souhaitez gérer :

```python
@window.event
def on_draw():
   window.clear()
```

## Afficher un texte

Utilisez le code suivant pour créer un objet Label représentant un texte :

```python
label = pyglet.text.Label('Hello, world',
                         font_name='Times New Roman',
                         font_size=36,
                         x=window.width // 2,
                         y=window.height // 2,
                         anchor_x='center',
                         anchor_y='center')
```

Puis, ajoutez un appel à la méthode `draw` dans la fonction `on_draw` :

```python
@window.event
def on_draw():
   window.clear()
   label.draw()
```

## Afficher une image

Vous devez d’abord importer le fichier image de référence. Pour cela, utilisez le code suivant :

```python
image = pyglet.resource.image('nom_du_fichier_image')
```

Puis, ajoutez un appel à la méthode `blit` dans la fonction `on_draw` :

```python
@window.event
def on_draw():
   window.clear()
   image.blit(0, 0)
```

## Lire un son ou une musique

Vous devez d’abord importer le fichier audio de référence. Pour cela, utilisez le code suivant :

```python
music = pyglet.resource.media('nom_du_fichier_audio')
```

**Remarque :** Vous pouvez lire sans problème les fichiers audio au format `.wav` mais pour les formats `.mp3` ou `.ogg`, vous devez installer le module `AVbin`.

Par défaut, les fichiers audio sont lus en streaming depuis leur emplacement sur disque. Si votre fichier est de taille réduite, vous pouvez l’importer directement en mémoire :

```python
sound = pyglet.resource.media('nom_du_fichier_audio', streaming=False)
```

Pour lire le son ou la musique, appelez la méthode `play` de l’objet :

```python
music.play()
sound.play()
```

## Gestion du clavier

Pour gérer le clavier, commencez par importer l’objet `key` :

```python
from pyglet.window import key
```

Puis utilisez la fonction suivante pour gérer les entrées clavier :

```python
@window.event
def on_key_press(symbol, modifiers):
   if symbol == key.A:
       print('La touche A a été enfoncée.')
   elif symbol == key.LEFT:
       print('La touche gauche a été enfoncée.')
   elif symbol == key.ENTER:
       print('La touche Entrée a été enfoncée.')
```

Consultez la documentation de `pyglet.window.key` pour les constantes clavier.

## Gestion de la souris

Pour gérer la souris, commencez par importer l’objet `mouse` :

```python
from pyglet.window import mouse
```

Puis utilisez la fonction suivante pour gérer la souris :

```python
@window.event
def on_mouse_press(x, y, button, modifiers):
   if button == mouse.LEFT:
       print('Le bouton gauche de la souris a été enfoncé.')
```
