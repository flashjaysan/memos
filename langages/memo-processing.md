# Mémo Processing

par *flashjaysan*

## Commandes

### Commentaires

Un commentaire est une section de code qui est ignoré lors de la compilation et de l'exécution.

- Les commentaires de fin de ligne s'écrivent avec deux slash `//`.
- Les commentaires de blocs s'encadrent par un slash étoile `/*` et une étoile slash `*/`.

```java
print("Hello, World!"); // ceci est un commentaire de fin de ligne
/* ceci
est un
commentaire
de bloc */
```

### Types de base

Le type `boolean` représente une valeur booléenne soit `true` (vraie) soit `false` (fausse).

```java
boolean booleen = true;
```

Le type `byte` représente un entier signé d'un octet (8 bits). Les valeurs peuvent aller de `-128` à `127`.

```java
byte entier8Bits = 100;
```

Le type `int` représente un entier signé de quatre octets (32 bits). Les valeurs peuvent aller de `-2147483648` à `2147483647`.

```java
int entier32Bits = 1000000000;
```

Le type `long` représente un entier signé de huit octets (64 bits). Les valeurs peuvent aller de `-9223372036854775808` à `9223372036854775807`. Utilisez le suffixe `L` pour représenter un littéral de type `long`.

```java
long entier64Bits = 1000000000000L;
```

Le type `float` représente un nombre à virgule flottante codé sur quatre octets (32 bits). Les valeurs peuvent aller de `-3.40282347E+38` à `3.40282347E+38`. Pour économiser les ressources, les fonctions de Processing utilisent ce type plutôt que le type `double`.

```java
float reel32Bits = 1.1;
```

Le type `double` représente un nombre à virgule flottante codé sur huit octets (64 bits). Les valeurs représentables sont très grandes mais prennent plus de place qu'un type `float`. Utilisez le suffixe `D` pour représenter un littéral de type `double`. Ce type définit par Java n'est pas utilisé par les fonctions de Processing.

```java
double reel64Bits = 1.1D;
```

Le type `char` représente un caractère codé sur deux octets (16 bits). Encadrez un caractère d'apostrophes `'` pour représenter un littéral de type `char`.

```java
char caractere = 'A';
```

Le type `String` représente une chaîne caractères. Encadrez une chaine de caractères de guillemets `"` pour représenter un littéral de type `String`.

```java
String chaine = "Hello, World!";
```

Le type `color` représente une couleur. Techniquement, il est codé en mémoire sous forme d'un nombre entier sur quatre octets (32 bits) dont chaque octet représente une composante de la couleur (alpha, bleu, vert, rouge).

Ce type peut être créé avec la fonction color qui prend trois ou quatres paramètres représenant les composantes rouges, vertes, bleues et alpha (opacité).

```java
color noir = color(0, 0, 0);// alpha == 255 par défaut
color blanc = color(255, 255, 255, 255);
```

La fonction `color` permet également de préciser un seul paramètre. Dans ce cas, les trois composantes rouges, vertes et bleues prennent la même valeur. Cela donne une couleur en niveaux de gris.

```java
color gris = color(155);
```

Il est également possible d'utiliser directement la notation hexadécimale pour définir une couleur.

```java
color rouge = #FF0000;
color vert = 0x00FF00FF;
```

Pour afficher une représentation textuelle de la couleur, utilisez la fonction `hex`.

```java
println(hex(couleur));
```

### Définir la taille de la fenêtre d'affichage

```java
size(largeur, hauteur);
```

Sans cette fonction, l'affichage est défini par défaut à 100x100 (ou plus exactement à 101x101).

### Obtenir les dimensions de la fenêtre

Les variables `width` et `height` contiennent respectivement la largeur et la hauteur (en pixels) de la fenêtre.

```java
rect(0, 0, width, height);
```

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

### Angles

Utilisez les valeurs `QUARTER_PI`, `HALF_PI`, `PI` et `TWO_PI` pour représenter des angles en radians.

```java
arc(50, 50, 100, 100, 0, TWO_PI);
```

Utilisez la fonction `radians` pour convertir des angles exprimés en degrés vers des angles exprimés en radians.

```java
arc(50, 50, 100, 100, 0, radians(360));
```

### Lignes et remplissage

Utilisez la fonction `strokeWeight` pour définir la largeur (en pixels) du contour des formes (par défaut `1`).

```java
strokeWeight(5);
```

Utilisez la fonction `strokeCap` pour définir la forme du bout des lignes. Les valeurs `SQUARE`, `PROJECT` et `ROUND` (par défaut) sont autorisées.

```java
strokeCap(SQUARE);
```

Utilisez la fonction `strokeJoin` pour définir la forme des lignes qui se touchent. Les valeurs `ROUND`, `BEVEL` et `MITTER` (par défaut) sont autorisées.

```java
strokeJoin(ROUND);
```

Utilisez la fonction `background` pour définir la couleur de fond de la fenêtre.

- Peut prendre une valeur entre `0` (noir) et `255` (blanc) pour des dégradés de gris.
- Peut prendre trois valeurs entre `0` (pas de couleur) et `255` (maximum de couleur) représentant les composantes rouges, vertes et bleues.
- Peut prendre un paramètre de type `color`.
- Peut prendre un paramètre de type `PImage`. Dans ce cas, la fonction affiche l'image sur le fond dans le coin supérieur gauche.

```java
background(155);
background(0, 0, 0);
background(couleur);
background(image);
```

**Remarque :** Il est possible de redimensionner une image à la taille de l'écran avec la méthode `resize`.

```java
image.resize(width, height);
```

Utilisez la fonction `fill` pour définir la couleur de remplissage des formes. Prend une valeur entre `0` (noir) et `255` (blanc) pour des dégradés de gris. Peut également prendre trois valeurs entre `0` (pas de couleur) et `255` (maximum de couleur) représentant les composantes rouges, vertes et bleues. Un quatrième paramètre correspondant à la transparence de la couleur peut être utilisé.

```java
fill(155);
fill(255, 255, 255);
fill(255, 0, 0, 255);
fill(couleur);
```

Utilisez la fonction `stroke` pour définir la couleur de contour des formes. Prend une valeur entre `0` (noir) et `255` (blanc) pour des dégradés de gris. Peut également prendre trois valeurs entre `0` (pas de couleur) et `255` (maximum de couleur) représentant les composantes rouges, vertes et bleues. Un quatrième paramètre correspondant à la transparence de la couleur peut être utilisé.

```java
stroke(155);
stroke(255, 255, 255);
stroke(255, 0, 0, 255);
stroke(couleur);
```

Utilisez la fonction `noStroke` pour désactiver l'affichage du contour des formes.

```java
noStroke();
```

Utilisez la fonction `noFill` pour désactiver l'affichage de l'intérieur des formes.

```java
noFill();
```

### Créer une couleur

```java
int couleur = color(niveauDeGris);
int couleur = color(niveauDeGris, composanteAlpha);
int couleur = color(composanteRouge, composanteVerte, composanteBleue);
int couleur = color(composanteRouge, composanteVerte, composanteBleue, composanteAlpha);
```

Les fonctions `red`, `green`, `blue` et `alpha` renvoient (sous forme d'entier de type `int`) les composantes rouges, vertes, bleues et alpha d'une couleur.

```java
int composanteRouge = red(rouge);
int composanteVerte = green(rouge);
int composanteBleue = blue(rouge);
int composanteAlpha = alpha(rouge);
```

### Dessiner un rectangle

```java
rect(x, y, largeur, hauteur);
```

### Dessiner un recangle aux bords arrondis

```java
rect(x, y, largeur, hauteur, rayonCoin);
```

### Dessiner un rectangle aux bords arrondis différents

```java
rect(x, y, largeur, hauteur, rayonCoin1, rayonCoin2, rayonCoin3, rayonCoin4);
```

### Dessiner un quadrilatère

```java
quad(x1, y1, x2, y2, x3, y3, x4, y4);
```

### Boucle de jeu

La fonction `setup` est appelée une seule fois au lancement du programme. Elle sert à initialiser l'état de départ du jeu. Appelez les fonctions d'initialisation graphique dans cette fonction.

```java
void setup()
{
    // initialisation
    size(640, 360);
    frameRate(60);
}
```

La fonction `draw()` constitue la boucle de jeu. Elle s'exécute indéfiniment après que la fonction `setup` ait été appelée.

```java
void draw()
{
    //boucle de jeu
}
```

La fonction `noLoop` stoppe la boucle de jeu. La fonction `draw` n'est plus appelée de manière répétée jusqu'à ce que la fonction `loop` relance la boucle de jeu.

```java
if (stop)
{
    noLoop();
}
else
{
    loop();
}
```

### Gestion de la souris

Les évènements de souris sont gérés par des fonctions callbacks. Pour fonctionner, la fonction `draw` doit être utilisée.

La fonction callback `mousePressed` est appelée automatiquement par Processing lorsqu'un bouton de souris vient d'être enfoncé.

```java
void mousePressed()
{
    println("Bouton de souris enfoncé.");
}
```

**Remarque :** La fonction `mousePressed` peut également recevoir un paramètre de type `MouseEvent` que vous pouvez utiliser pour déterminer certaines valeurs liées à l'évènement.

```java
void mousePressed(MouseEvent event)
{

}
```

La fonction callback `mouseReleased` est appelée automatiquement par Processing lorsqu'un bouton de souris vient d'être relaché.

```java
void mouseReleased()
{
    println("Bouton de souris relaché.");
}
```

**Remarque :** La fonction `mouseReleased` peut également recevoir un paramètre de type `MouseEvent` que vous pouvez utiliser pour déterminer certaines valeurs liées à l'évènement.

```java
void mouseReleased(MouseEvent event)
{

}
```

La fonction callback `mouseClicked` est appelée automatiquement par Processing lorsqu'un bouton de souris est enfoncé puis relaché.

```java
void mouseClicked()
{
    println("Clic de souris effectué.");
}
```

**Remarque :** La fonction `mouseClicked` peut également recevoir un paramètre de type `MouseEvent` que vous pouvez utiliser pour déterminer certaines valeurs liées à l'évènement.

```java
void mouseClicked(MouseEvent event)
{

}
```

La fonction callback `mouseMoved` est appelée automatiquement par Processing lorsque le pointeur de la souris est déplacé alors qu'aucun bouton n'est enfoncé.

```java
void mouseMoved()
{
    println("Souris déplacée.");
}
```

**Remarque :** La fonction `mouseMoved` peut également recevoir un paramètre de type `MouseEvent` que vous pouvez utiliser pour déterminer certaines valeurs liées à l'évènement.

```java
void mouseMoved(MouseEvent event)
{

}
```

La fonction callback `mouseDragged` est appelée automatiquement par Processing lorsque le pointeur de la souris est déplacé alors qu'un bouton est enfoncé.

```java
void mouseDragged()
{
    println("Souris glissée.");
}
```

**Remarque :** La fonction `mouseDragged` peut également recevoir un paramètre de type `MouseEvent` que vous pouvez utiliser pour déterminer certaines valeurs liées à l'évènement.

```java
void mouseDragged(MouseEvent event)
{

}
```

La fonction callback `mouseWheel` est appelée automatiquement par Processing lorsque la molette de la souris est manipulée. Elle reçoit en paramètre un objet de type `MouseEvent` contenant certaines valeurs liées à l'évènement.

```java
void mouseWheel(MouseEvent event)
{
    println("Molette utilisée.");
}
```

Les variables `mouseX` et `mouseY` représentent les coordonnées x et y de la position du pointeur de la souris dans la fenêtre.

```java
println(mouseX);
println(mouseY);
```
