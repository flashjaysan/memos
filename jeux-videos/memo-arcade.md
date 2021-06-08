# Mémo arcade

*par flashjaysan*

Le module `arcade` est une bibliothèque destinée à l’apprentissage de la programmation et à la création de jeux vidéos. Il est basé sur le module pyglet et OpenGL.

**Attention !** Le système de coordonnées du module arcade est celui utilisé en mathématiques : L’origine du système est situé dans le coin inférieur gauche de la fenêtre et l’axe Y augmente vers le haut.

## Installation

Pour installer le module `arcade`, tapez la commande suivante dans votre console système :

```python
pip install arcade
```

Si vous utilisez Pycharm, vous pouvez également utiliser le menu `File > Settings...`, puis dans la section `Project:nom_du_projet > Project Interpreter` cliquer sur le bouton `+` et saisir `arcade` dans la barre de recherche, cliquer sur la bibliothèque `arcade` et enfin cliquer sur le bouton `Install Package`.

## Importer le module arcade

Insérez en tête de votre fichier source la ligne suivante :

```python
import arcade
```

## Créer une fenêtre

Pour créer une fenêtre, utilisez le code suivant :

```python
arcade.open_window(largeur_écran, hauteur_écran, ‘titre_fenêtre’)
```

- `largeur_écran` correspond à la largeur de la fenêtre (en pixels).
- `hauteur_écran` correspond à la hauteur de la fenêtre (en pixels).
- `titre_fenêtre` correspond à la chaîne de caractère qui apparaîtra dans la barre de titre de la fenêtre.

Ajoutez ensuite la ligne suivante pour empêcher que la fenêtre ne se ferme aussitôt l’exécution commencée :

```python
arcade.run()
```

**Conseil :** Définissez les dimensions de la fenêtre comme des constantes que l'on pourra par la suite utiliser dans le programme :

```python
import arcade

SCREEN_WIDTH = 640
SCREEN_HEIGHT = 360

arcade.open_window(SCREEN_WIDTH, SCREEN_HEIGHT, 'Game')

arcade.run()
```

## Créer une couleur

Définissez une nouvelle couleur comme ceci :

```python
couleur = constante_couleur
```

constante_couleur est une constante parmi celles-ci :

http://arcade.academy/arcade.color.html

Vous pouvez visualisez leur rendu :

https://www.webpagefx.com/web-design/color-picker/color-chart/

Vous pouvez également utilisez trois valeurs RGB entre parenthèses (un tuple) :

```python
couleur = (rouge, bleu, vert)
```

- `rouge` correspond à la valeur de la composante rouge de la couleur (comprise entre 0 et 255).
- `vert` correspond à la valeur de la composante verte de la couleur (comprise entre 0 et 255).
- `bleu` correspond à la valeur de la composante bleue de la couleur (comprise entre 0 et 255).

Une quatrième valeur (comprise entre 0 et 255) peut être passée pour représenter l'opacité de la couleur (son alpha). Plus la valeur est basse, plus la couleur est transparente. Par défaut, cette valeur vaut 255.

## Remplir la fenêtre d’une certaine couleur

Par défaut, la couleur de fond est blanche. Choisissez une couleur de fond avec le code suivant :

```python
arcade.set_background_color(couleur)
```

- `couleur` correspond à une couleur définie précédemment ou à la volée.

**Attention !** Si vous définissez une couleur directement avec des valeurs RGB, pensez à les encadrer de parenthèses (un tuple) à l’intérieur des parenthèses d’appel de la fonction `set_background_color` :

```python
arcade.set_background_color((0, 0, 0))
```

Vous devez ensuite appeler les fonctions suivantes avant d’appeler la fonction `run` :

```python
arcade.start_render()
arcade.finish_render()
```

## Afficher un point

Utilisez le code suivant pour afficher un point :

```python
arcade.draw_point(position_x, position_y, couleur, taille)
```

- `position_x` correspond à la position horizontale du point (en pixels).
- `position_y` correspond à la position verticale du point (en pixels).
- `couleur` correspond à la couleur du point.
- `taille` correspond à la taille du point (en pixels).

**Remarque :** Si vous modifiez la taille du point, il sera affiché comme un carré dont le centre correspond à la position spécifiée.

## Afficher plusieurs points

Utilisez le code suivant pour afficher plusieurs points :

```python
liste_de_points = ((position_x_point_1, position_y_point_1),
                   (position_x_point_2, position_y_point_2),
                   ...
                   (position_x_point_n, position_y_point_n))
arcade.draw_points(liste_de_points, couleur, taille)
```

- `liste_de_points` correspond à une séquence de couple de coordonnées des points à afficher (en pixels). C'est un tuple de tuples.
- `couleur` correspond à la couleur du point.
- `taille` correspond à la taille du point (en pixels).

**Remarque :** Si vous modifiez la taille des points, ils seront affichés comme des carrés dont le centre correspond à la position spécifiée.

## Afficher un rectangle

```python
# Different way to draw a rectangle
# Center rectangle at (100, 520) with a width of 45 and height of 25
arcade.draw_rectangle_filled(100, 520, 45, 25, arcade.color.BLUSH)

# Rotate a rectangle
# Center rectangle at (200, 520) with a width of 45 and height of 25
# Also, rotate it 45 degrees.
arcade.draw_rectangle_filled(200, 520, 45, 25, arcade.color.BLUSH, 45)


# Draw a point at (50, 580) that is 5 pixels large
arcade.draw_point(50, 580, arcade.color.RED, 5)

# Draw a line
# Start point of (75, 590)
# End point of (95, 570)
arcade.draw_line(75, 590, 95, 570, arcade.color.BLACK, 2)

# Draw a circle outline centered at (140, 580) with a radius of 18 and a line
# width of 3.
arcade.draw_circle_outline(140, 580, 18, arcade.color.WISTERIA, 3)

# Draw a circle centered at (190, 580) with a radius of 18
arcade.draw_circle_filled(190, 580, 18, arcade.color.WISTERIA)

# Draw an ellipse. Center it at (240, 580) with a width of 30 and
# height of 15.
arcade.draw_ellipse_filled(240, 580, 30, 15, arcade.color.AMBER)

# Draw text starting at (10, 450) with a size of 20 points.
arcade.draw_text("Simpson College", 10, 450, arcade.color.BRICK_RED, 20)
```
