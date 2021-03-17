# Memo CTJS

*par flashjaysan*

Les *textures* sont utilisées par des *types* qui sont eux-même utilisés pour créer des *copies* dans les *rooms* du jeu.
Par rapport à GameMaker, les textures sont équivalents aux *sprites*, les types aux *objets* et les copies aux *instances*.

## Textures

### Importer des textures

Cliquez sur la section `Textures` et faites glisser les images dans la fenêtre ou cliquez sur le bouton `Import` pour naviguer dans vos dossier et importer manuellement les fichiers. L'éditeur copie automatiquement les textures dans le projet et les fichiers d'origine ne sont pas altérés.

### Editeur de texture

Dans la section `Textures`, cliquez sur la texture que vous souhaitez éditer pour ouvrir l'éditeur de textures.

#### Vue centrale

- La glissière de zoom en bas à droite vous permet d'agrandir ou de réduire l'affichage de la texture. Vous pouvez également utiliser la molette de la souris.
- Le bouton `Replace...` vous permet d'ouvrir un explorateur de fichiers pour remplacer la texture par une autre.
- Le bouton `Update from clipboard` vous permet de remplacer la texture par une image copiée dans le presse papier.
- Le bouton `Reimport` vous permet d'importer à nouveau la texture depuis le fichier d'origine. Cette option ne fonctionne que si le fichier d'origine existe toujours. Cela vous permet de modifier la texture depuis un éditeur d'image et d'importer la version la plus récente d'une image modifiée. 

#### Edition générale

Les informations générales de la texture se trouvent à gauche de la vue centrale.

- Le champ `Name` vous permet de définir le nom de la texture.
- La case `Use as a background?` vous permet de définir la texture comme un arrière plan.
- Les champs `Axis` vous permettent de préciser la position du point d'origine dans la texture. Cela définit également le point d'origine du masque de collision.
- Le bouton `Image's center` positionne le point d'origine au centre de la texture.
- Le bouton `Isometrify` positionne le point d'origine au centre bas de la texture et définit le masque de collision sur la totalité de la texture.
- La section `Collision Shape` vous permet de choisir la forme du masque de collision.
  - L'option `Circle` définit la forme du masque de collision sur un cercle. Le champ `Radius` vous permet alors de définir le rayon du cercle.
  - L'option `Rectangle` définit la forme du masque de collision sur un rectangle. Le champ de saisie vous permettent alors de définir la distance haute, gauche, droite et basse des bords du rectangle par rapport au point d'origine. Le bouton `Fill` vous permet de régler automatiquement le masque sur la totalité de la texture.
  - L'option `Line Strip / Polygon` vous permet de définir la forme du masque de collision sur un polygone. Les champs de chaque ligne vous permettent de définir la position d'un point du polygone relativement au point d'origine. Le bouton `-` à droite de ces champs vous permet de supprimer le point. Le bouton `Add a point` vous permet d'ajouter un point au polygone. La case `Close the shape` vous permet d'indiquer que le polygone doit être fermé. Si la case est décoché, le masque de collision est constitué d'une simple suite de segments. La case `Symetry tool` définit le polygone comme un ensemble de deux polygones symmétriques autour de l'axe défini par le premier et le dernier point de la liste.
- La case `Show mask` vous permet d'afficher le masque de collision par dessus la texture.
- Dans la vue centrale, directement sur la texture, vous pouvez déplacer les points de contrôle manuellement.
- Le bouton `Save` vous permet de sauvegarder vos modifications et ferme automatiquement l'éditeur de textures.

**Attention !** N'oubliez pas de cliquer sur le bouton `Save` pour sauvegarder vos modifications !

#### Editeur d'animation

Les informations relatives à l'animation de la texture se trouvent à droite de la vue centrale.

- Le champ `Columns` vous permet de définir le nombre de colonnes contenues dans la texture et constituant l'animation.
- Le champ `Rows` vous permet de définir le nombre de lignes contenues dans la texture et constituant l'animation.
- Le champ `Width` vous permet de définir la largeur d'une frame d'animation.
- Le champ `Height` vous permet de définir la hauteur d'une frame d'animation.
- Le champ `Margin X` vous permet de définir l'espace horizontal entre chaque frame d'animation de chaque ligne.
- Le champ `Margin Y` vous permet de définir l'espace vertical entre chaque frame d'animation de chaque colonne.
- Le champ `Frame count` vous permet de définir le nombre d'images constituant l'animation.
- Le champ `Padding` vous permet de définir le nombre de pixels à ajouter aux bords de la texture pour éviter les effets de *bleeding* sur les textures qui se répètent.
- Le bouton `Play / Pause` vous permet de lancer ou stopper la lecture de l'animation dans la fenêtre juste au dessus.
- Les boutons `Previous frame` et `Next frame` vous permettent d'afficher les différentes images de l'animation dans la fenêtre juste au dessus.
Le champ `Framerate` vous permet de définir la vitesse de l'animation.

## Types

Cliquez sur l'onglet `Types` pour afficher l'éditeur de types.

### Créer un type

Cliquez sur le bouton `Create` pour créer un nouveau type et ouvrir l'éditeur de types.

- Cliquez sur le bouton `Change texture` pour attribuer une texture au type (parmi les textures importées dans l'éditeur).
- Le champ `Name` vous permet de définir le nom du type.
- Le champ `Depth` vous permet de définir la position de profondeur du type.
- La case `Visible` vous permet de définir si le type doit être visible ou non.
- Le champ `Collision group` vous permet de définir le groupe de collision auquel appartient le type.
- Le bouton `Done` vous permet de sauvegarder vos modifications et ferme automatiquement l'éditeur de types.

**Attention !** N'oubliez pas de cliquer sur le bouton `Done` pour sauvegarder vos modifications !

### Propriétés

La liste des propriétés se trouve (ici)[https://docs.ctjs.rocks/copy.html].

Pour voir la liste des propriétés d'un type, saisissez `this` suivi d'un point dans l'éditeur d'évènements.

```js
this.x
this.y
this.xstart
this.ystart
this.xprev
this.yprev
this.speed
this.direction
this.gravity
this.gravityDir
this.hspeed
this.vspeed
```

- La propriété `rotation` définit l'angle de la texture associé au type.
- La propriété `alpha` définit l'opacité de la texture associé au type.
- La propriété `scale.x` définit l'échelle horizontale de la texture associé au type.
- La propriété `scale.y` définit l'échelle verticale de la texture associé au type.
- La propriété `ctype` (chaine de caractère) définit le groupe de collision auquel appartient le type.

### Evènements

`On Create` is called when you launch the game or move to this room programmatically;
`On Step` is called each frame, after Copies' On Step;
`Draw` is called after drawing all the level. It is useful for updating UI;
`On Destroy` is called before moving to another room.

## Copies

### Créer une copie

Pour créer une copie dans la room actuelle, utilisez `ct.types.copy`.

```js
let new_copy = ct.types.copy("nom_type", x, y);
```

Si vous omettez les paramètres `x` et `y`, la copie est placée à l'origine du repère de la room.

### Détruire une copie

Attribuez la valeur `true` à la propriété `kill`. La copie sera détruite à la fin de la frame en cours.

```js
this.kill = true;
```

## Rooms

Cliquez sur l'onglet `Rooms` pour afficher l'éditeur de rooms. Les rooms n'ont pas de dimension limitée.

### Créer une room

Cliquez sur le bouton `Add new` pour créer une nouvelle room et ouvrir l'éditeur de rooms.

### Editeur de rooms

Créez une nouvelle room ou cliquez sur une des rooms existantes pour ouvrir l'éditeur de rooms.

- Le champ `Name` vous permet de définir le nom de la room.
- Le bouton `Room events` affiche l'éditeur d'évènements de la room.
  - 
  - 
  - 
  - 
  - 
  - 
  - Le bouton `Done` vous permet de sauvegarder vos modifications et revient automatiquement à l'éditeur de rooms.
- L'onglet `Copies` vous permet de sélectionner une copie et de cliquer dans la room pour la placer à cet emplacement. Sélectionnez `Select and Move` pour sélectionner et déplacer des copies déjà placées dans la room.
- L'onglet `Backgrounds` vous permet d'ajouter des fonds dans la room.
  - Cliquez sur le bouton `Add a Background` pour ajouter un fond à la room parmi les textures importées. La texture utilisée en tant que fond doit avoir l'option `Use as a background?` de cochée. si ce n'est pas le cas, l'éditeur vous propose de cocher cette option automatiquement en cliquant sur le texte `Fix it`.
  - Cliquez sur la roue dentée d'un fond ajouté pour éditer ses propriétés.
    - Le champ `Depth` vous permet de définir la position de profondeur du fond.
    - Les champs `Shift (X, Y)` vous permettent de définir le décalage horizontal et vertical de la texture utilisée pour le fond.
    - Les champs `Scaling (X, Y)` vous permettent de définir l'échelle horizontale et verticale de la texture utilisée pour le fond.
    - Les champs `Movement speed (X, Y)` vous permettent de définir la vitesse de mouvement horizontal et vertical à appliquer à la texture utilisée pour le fond.
    - Les champs `Parallax (X, Y)` vous permettent ??????????.
    - Le menu déroulant `Repeat` vous permet de choisir comment la texture doit se répéter dans la room.
      - Sélectionnez l'option `repeat` si la texture doit se répéter horizontalement et verticalement.
      - Sélectionnez l'option `repeat-x` si la texture doit se répéter uniquement horizontalement.
      - Sélectionnez l'option `repeat-y` si la texture doit se répéter uniquement verticalement.
      - Sélectionnez l'option `no-repeat` si la texture ne pas se répéter du tout.

- L'onglet `Tiles` .
  - Le bouton 
  - Le champ `Collision group` vous permet de définir le groupe de collision auquel appartient le type.
- L'onglet `Properties` vous permet de configurer les propriétés générales de la room.
  - Le champ `View width` vous permet de définir la largeur de la vue dans la room.
  - Le champ `View height` vous permet de définir la hauteur de la vue dans la room.
  - Le bouton `Background color` vous permet de définir la lcouleur de fond de la room.
  - La case `Is a UI layer?` vous permet d'indiquer si la room est un calque d'interface utilisateur.
- Le bouton `Done` vous permet de sauvegarder vos modifications et ferme automatiquement l'éditeur de rooms.

**Attention !** N'oubliez pas de cliquer sur le bouton `Done` pour sauvegarder vos modifications !

La variable `ct.room` définit la room actuelle.

`ct.rooms.switch` unloads the current room and loads a new one. By pointing to the same room as we were playing, we restart it.

### Evènements de room

`On Create` is called when you launch the game or move to this room programmatically;
`On Step` is called each frame, after Copies' On Step;
`Draw` is called after drawing all the level. It is useful for updating UI;
`On Leave` is called before moving to another room.

## Contrôles

Cliquez sur l'onglet `Project` puis la section `Catmods`.

- Activez le module `Keyboard` pour la gestion du clavier.
- Activez le module `Gamepad` pour la gestion de manettes.
- Activez le module `Mouse Input` pour la gestion de la souris.

Cliquez sur la section `Actions and input methods` puis cliquez sur le bouton `Add` pour ajouter une action.

Le nom des actions que vous créez se retrouve dans l'objet `ct.actions`.

## Mouvement

Dans l'onglet `Types`, sélectionnez l'objet à éditer.

Cliquez sur l'évènement `On Create` pour ajouter une propriété.

```js
this.movementMagnitude = 8;
```

Cliquez sur l'événement `On Step`.

```js
this.x += this.movementMagnitude * ct.delta * ct.actions.MoveX.value;
this.y += this.movementMagnitude * ct.delta * ct.actions.MoveY.value;
this.move();
```

Si aucun contrôle n'est activé, la valeur renvoyée vaut `0`.

### Limiter le déplacement dans la vue

Les propriétés `ct.camera.width` et `ct.camera.height` vous permettent d'accéder aux dimensions de la vue.

```js
if (this.x < 0)
{
    this.x = 0;
}
if (this.x > ct.camera.width)
{
    this.x = ct.camera.width;
}

if (this.y < 0)
{
    this.y = 0;
}
if (this.y > ct.camera.height)
{
    this.y = ct.camera.height;
}
```

### Mouvement automatique

Utilisez les propriétés prédéfinies `speed` et `direction` des types dans l'évènement `On Create`.

```js
this.speed = 5;
this.direction = 270;
```

- `speed` désigne la vitesse de déplacement du type vers la droite. Cette propriété modifie les propriétés `hspeed` et `vspeed`.
- `direction` désigne l'angle (en degrès) de déplacement du type. `0` est vers la droite. `90` vers le haut, `180` vers la gauche et `270` vers le bas.

Pour que la copie se déplace, vérifiez bien que la méthode `move` est appelée dans l'évènement `On Step`.

```js
this.move();
```

**Attention !** Si vous utilisez cette méthode, veillez bien à toujours paramétrer la propriété `speed` avant la propriété `direction`. Si vous faites l'inverse, modifier la propriété `speed` remettra la propriété `direction` à la valeur `0`.

## Fonctions aléatoires

Cliquez sur l'onglet `Project` puis la section `Catmods`.

Activez le module `ct.random` pour ajouter au projet les fonctions aléatoires.

```js
ct.random.range(1, 3);
```

`ct.random.deg` returns a random value between 0 and 360
`ct.random.dice` returns one of the provided values. You can put any value here, including Numbers, Strings, complex objects. Here, there is a 50% chance that 'Asteroid_Big' will be returned and a 50% chance that it will be 'Asteroid_Medium'.

`ct.random.range(a, b)` returns a random numerical value between a and b.

`ct.random(b)` is the same as ct.random.range(0, b)


## Collisions

Cliquez sur l'onglet `Project` puis la section `Catmods`.

Activez le module `ct.place` pour ajouter au projet la gestion des collisions.

```js
const collided = ct.place.meet(this, this.x, this.y, 'nom_type');
if (collided)
{
    collided.kill = true;
    this.kill = true;
}
```
`ct.place.meet` fonctionne sur les types.
`ct.place.occupied` fonctionne sur les groupes de collision.

## GUI

Cliquez sur l'onglet `UI` pour ouvrir l'éditeur d'interface utilisateur.

Placez le code dans l'évènement `On Create` de la room.

```js
this.score = 0;

this.scoreLabel = new PIXI.Text('Score: ' + this.score);
this.addChild(this.scoreLabel);
this.scoreLabel.x = 30;
this.scoreLabel.y = 30;
this.scoreLabel.depth = 1000;
```

Puis, dans l'évènement `Draw`.

```js
this.scoreLabel.text = 'Score: ' + this.score;
```







