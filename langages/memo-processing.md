# Mémo Processing

par *flashjaysan*

## Commandes

### Définir la taille de la fenêtre d'affichage

```java
size(largeur, hauteur);
```

Sans cette fonction, l'affichage est défini par défaut à 100x100.

### Fonctions d'affichage

```java
point(x, y);
line(x1, y1, x2, y2);
triangle(x1, y1, x2, y2, x3, y3);
quad(x1, y1, x2, y2, x3, y3, x4, y4);
rect(x, y, largeur, hauteur);
ellipse(x, y, largeur, hauteur);
arc(x, y, largeur, hauteur, angle_début, angle_fin);

```

Utilisez les valeurs `PI`, `QUARTER_PI`, `HALF_PI` et `TWO_PI` pour représenter des angles en radians.

Utilisez la fonction `radians` pour convertir des angles exprimés en degrés vers des angles exprimés en radians.

Utilisez la fonction `strokeWeight` pour définir la largeur (en pixels) du contour des formes (par défaut 1).

Utilisez la fonction `strokeCap` pour définir la forme du bout des lignes. Les valeurs `SQUARE`, `PROJECT` et `ROUND` (par défaut) sont autorisées.

Utilisez la fonction `strokeJoin` pour définir la forme des lignes qui se touchent. Les valeurs `ROUND`, `BEVEL` et `MITTER` (par défaut) sont autorisées.

Utilisez la fonction `background` pour définir la couleur de fond de la fenêtre. Prend une valeur entre 0 (noir) et 255 (blanc) pour des dégradés de gris. Peut également prendre trois valeurs entre 0 (pas de couleur) et 255 (maximum de couleur) représentant les composantes rouges, vertes et bleues.

Utilisez la fonction `fill` pour définir la couleur de remplissage des formes. Prend une valeur entre 0 (noir) et 255 (blanc) pour des dégradés de gris. Peut également prendre trois valeurs entre 0 (pas de couleur) et 255 (maximum de couleur) représentant les composantes rouges, vertes et bleues. Un quatrième paramètre correspondant à la transparence de la couleur peut être utilisé.

Utilisez la fonction `stroke` pour définir la couleur de contour des formes. Prend une valeur entre 0 (noir) et 255 (blanc) pour des dégradés de gris. Peut également prendre trois valeurs entre 0 (pas de couleur) et 255 (maximum de couleur) représentant les composantes rouges, vertes et bleues. Un quatrième paramètre correspondant à la transparence de la couleur peut être utilisé.

Utilisez la fonction `noStroke` pour désactiver l'affichage du contour des formes.

Utilisez la fonction `noFill` pour désactiver l'affichage de l'intérieur des formes.

