- `print(texte1, texte2, ...)` : Affiche les textes, à la suite du dernier texte affiché par cette fonction.
- `printAt(x, y, texte)` : Affiche le texte à une position précise.
- `nomVariable = input(message)` : Affiche un message et récupère la saisie de l'utilisateur depuis le clavier.
- `textWidth(texte)` : Largeur en pixels d'un texte.
- `update()` : Echange les tampons d'affichage.
- `sleep(duree)` : Met l'exécution du programme en pause `duree` secondes.
- `ink(couleur)` : Définit la nouvelle couleur de dessin.
- `random(entier)` : Génère un entier aléatoire compris dans l'intervalle `[0, nombre[`.
- `textSize(taille)` : Définit la taille de texte à dessiner.
- `nomVariable = valeur` : Affecte la `valeur` à la variable `nomVariable`.
- `clear(couleur)` : Efface la surface d'affichage avec la `couleur`.
- `""` : Chaine vide.
- `=` : affectation.
- `nomVariable += valeur` : Equivalent à `nomVariable = nomVariable + valeur`.
- `nomVariable -= valeur` : Equivalent à `nomVariable = nomVariable - valeur`.
- `nomVariable *= valeur` : Equivalent à `nomVariable = nomVariable * valeur`.
- `nomVariable /= valeur` : Equivalent à `nomVariable = nomVariable / valeur`.
- `+` : addition.
- `-` : soustraction.
- `*` : multiplication.
- `/` : division.
- `mod` : reste de division.
- `%` : reste de division.
- `==` : égalité.
- `!=` : inégalité.
- `<` : inférieur.
- `<=` : inférieur ou égal.
- `>` : supérieur.
- `>=` : supérieur ou égal.
- `circle(centreX, centreY, rayon, nombreSegments, couleur, estContour)` : Affiche un cercle.
- `box(x, y, largeur, hauteur, couleur, estContour)` : Affiche un rectangle.
- `gwidth()` : Largeur de l'écran.
- `gheight()` : Hauteur de l'écran.
- `or` : OU logique.
- `and` : ET logique.
- `not` : NON logique.
- `!` : NON logique.
- `^` : XOR logique.
- `&` : ET binaire.
- `|` : OU binaire.
- `~` : inversion de bits.
- `<<` : décalage de bits vers la gauche.
- `>>` : décalage de bits vers la droite.
- `nomVariable = {rouge, vert, bleu, opacite}` : Définit une couleur RGBA.
- `controls(indice)` : Informations de l'état du controlleur `indice`.
- `controle(indice).a` : Booléen indiquant si la touche `A` du controlleur `indice` est enfoncée.
- `controle(indice).b` : Booléen indiquant si la touche `B` du controlleur `indice` est enfoncée.
- `controle(indice).x` : Booléen indiquant si la touche `X` du controlleur `indice` est enfoncée.
- `controle(indice).y` : Booléen indiquant si la touche `Y` du controlleur `indice` est enfoncée.
- `controle(indice).zl` : Booléen indiquant si la touche `ZL` du controlleur `indice` est enfoncée.
- `controle(indice).zr` : Booléen indiquant si la touche `ZR` du controlleur `indice` est enfoncée.
- `controle(indice).lx` : Indique la valeur horizontale `[-1, 1]` du stick de gauche du controlleur `indice`.
- `controle(indice).ly` : Indique la valeur verticale `[-1, 1]` du stick de gauche du controlleur `indice`. **Attention !** La valeur est positive quand le stick est poussé vers le haut.
- `true`: Booléen vrai.
- `false` : Booléen faux.
- `array nomVariable[longueur]` : Définit un tableau de `longueur` éléments. Les éléments commencent à l'indice `0`.
- `nomVariable = [element1, element2, ...]` : Définit et initialise un tableau.
- `len(tableau)` : Renvoit la longueur d'un tableau.

Comment ajoute-t-on des éléments à un tableau ?

L'origine est dans le coin supérieur gauche de l'écran. L'axe Y augmente vers le bas.

La Switch a une résolution de 1280x720 pixels en mode portable et 1920x1080 pixels en mode dockée.

## Portée

Une variable définie en dehors d'un bloc ou d'une fonction est globale. Sinon elle est locale.

## Structures

```
nomVariable = [.propriete1 = valeur, .propriete2 = valeur, ...]
print(nomVariable.propriete1)
```

```
struct nomStruct
    nomType nomPropriete
    ...
enstruct
```

Les types :

- `string`.
- `int`.
- `float`.
- `array`. Dans ce cas, la propriété doit préciser une longueur.

```
struct nomStruct
    array nomPropriete[longueur]
    ...
endstruct
```

## Conversion

- `int(valeur)` convertit une chaine ou un nombre à virgule en entier.
- `float(valeur)` convertit une chaine ou un nombre entier en nombre à virgule.

## Vecteurs

Un vecteur est un groupe de **nombres**.

```
nomVariable = {valeur1, valeur2, ...}
```

```
print(nomVariable.x)
print(nomVariable.y)
print(nomVariable.z)
print(nomVariable.w)
```

ou

```
print(nomVariable.r)
print(nomVariable.g)
print(nomVariable.b)
print(nomVariable.a)
```

**Remarque :** Si vous ne précisez pas toutes les dimensions, celles restantes sont initialisée à 0. Utilisez des accolades vides pour créer un vecteur nul.

```
vecteurNul = {}
```

Vous pouvez appliquer une opération mathématique sur un vecteur.

```
vecteur2 = vecteur1 * 2
vecteur += 3
```

## Branchement

```
if condition then

endif
```

```
if condition then

else

endif
```

## Boucles

```
loop

repeat
```

```
while condition loop

repeat
```

```
for nomVariable = valeurInitiale to valeurFinale loop

repeat
```

**Remarque :** `valeurFinale` n'est pas incluses dans l'intervalle. `nomVariable` reste dans l'intervalle `[valeurInitiale, valeurFinale[`.

```
for nomVariable = valeurInitiale to valeurFinale step pas loop

repeat
```

**Remarque :** Utilisez `break` pour sortir de la boucle prématurément. 

## Fonctions

Deux types :

- Fonctions prédéfinies.
- Fonctions utilisateur.

```
function nomFonction()

return void
```

```
function nomFonction(parametre1, parametre2, ...)

return valeur
```

## Charger une image

```
nomImage = loadImage(cheminImage, activerFiltre)
```

Le chemin de l'image est défini automatiquement via une sélection visuelle dans l'éditeur.

- `imageW(image)` : Renvoie la largeur en pixels de l'image.
- `imageH(image)` : Renvoie la hauteur en pixels de l'image.

## Dessiner une image

```
drawImage(nomImage, x, y, echelle)
```

```
drawImageEx(image, x, y, angle, echelleX, echelleY, rouge, vert, bleu, opacite, originX, originY)
```

## Boucle de jeu

La boucle de jeu s'exécute 60 fois par seconde.

## Graphismes



## Audio

`playNote(canal, formeOnde, frequence, volume, vitesse, balance)` : Joue une note.

**Remarques :**

- Il y a 16 canaux différents. Cela permet de jouer jusqu'à 16 sons (note, son ou musique) en même temps.
- Il y a 5 formes d'onde.
  - `0` : Square.
  - `1` : Sawtooth.
  - `2` : Triangle.
  - `3` : Sine.
  - `4` : Bruit.
- La vitesse est inversement proportionnelle à la durée.

`note2Freq(note)` : Renvoie la fréquence associée à une note.

`setReverb(??, ??, ??)` : ???.

## Contrôles


