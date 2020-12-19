# Mémo Phaser

*par flashjaysan*

## Introduction

*Phaser* est une bibliothèque open source de création de jeu vidéo pour *JavaScript*. Elle possède de très nombreuses fonctionnalités qui simplifient la création de jeu utilisant le standard *HTML5* pour les navigateurs web. Les jeux développés avec *Phaser* peuvent être joués sur n'importe quel navigateur web.

## Téléchargement de Phaser

Téléchargez le fichier `phaser.js` à la page [https://phaser.io/download/stable](https://phaser.io/download/stable) et placez-le dans le dossier de votre projet. Je le place en général dans un sous-dossier appelé `libs`.

**Remarque :**  Le fichier `phaser.js` est la version de développement de *Phaser*. Vous pouvez l'ouvrir dans un éditeur de code et lire son code source. Le fichier `phaser.min.js` est une version de production de *Phaser*. Les commentaires ainsi que les espaces ont été supprimés pour réduire la taille du fichier. Sa lecture en est en revanche bien moins facile. Utilisez la version de développement, lors du développement de vos jeux, puis utilisez la version de production lors de la publication.

## Outils nécessaires

### Navigateur

*Phaser* étant une bibliothèque *JavaScript*, vous aurez besoin d'un navigateur web pour tester vos jeux. N'importe quel navigateur web récent fera l'affaire. [Google Chrome](https://www.google.com/chrome/), [Mozilla Firefox](https://www.mozilla.org/fr/firefox/new/), [Opera](https://www.opera.com/fr) ou [Microsoft Edge](https://www.microsoft.com/fr-fr/windows/microsoft-edge) par exemple sont tous de bons choix.

### Editeur de code

Bien que vous puissiez programmer votre jeu dans un éditeur de texte basique tel que le bloc-note, un éditeur de code peut vous simplifier les choses. [Microsoft Visual Studio Code](https://code.visualstudio.com/), [Atom](https://atom.io/), [Sublime Text](https://www.sublimetext.com/), [Brackets](http://brackets.io/) sont des éditeurs populaires.

### Serveur web

Pour tester vos jeux localement lors du développement, vous aurez besoin d'un serveur web. En effet, les navigateurs web, pour des raisons de sécurité, ne permettent pas d'accéder à des fichiers locaux. Un serveur web permet cet accès en le restreignant à un dossier particulier.

#### Mongoose web server

Sur *Windows*, je vous recommande le serveur web [*Mongoose*](http://cesanta.com/downloads.html) qui est très léger et qui ne nécessite aucune installation. Placez simplement le fichier dans le dossier de votre choix qui contiendra vos projets *Phaser* et exécutez le fichier. Une fenêtre de navigateur s'ouvre et affiche les fichiers contenus dans ce dossier.

**Remarque :** Si vous fermez le navigateur, cliquez sur l'icône de *Mongoose* dans la zone de notification en bas à droite et choisissez l'option `Go to my address:...` pour ouvrir à nouveau le navigateur sur le serveur web.

Pour fermer le serveur web, cliquez sur l'icône de *Mongoose* dans la zone de notification en bas à droite et choisissez l'option `Exit`.

#### Brackets

Une autre solution très simple est d'utiliser l'éditeur de code [*Brackets*](brackets.io) qui fournit un serveur web. Ouvrez le dossier de votre projet dans *Brackets*, ouvrez le fichier *HTML* contenant votre jeu et cliquez sur l'icône en forme d'éclair en haut à droite pour ouvrir automatiquement un serveur web sur l'emplacement du fichier *HTML* en cours d'édition.

#### Visual Studio Code

Une autre solution simple est d'utiliser l'éditeur de code [Visual Studio Code](https://code.visualstudio.com/) avec l'extension `Live Server` pour programmer votre jeu et de cliquer sur l'icône `Go Live` en bas à droite de l'éditeur pour ouvrir automatiquement le navigateur par défaut avec un serveur web pointant sur l'emplacement d'un fichier *HTML* en cours d'édition.

- Installez l'extension `Live Server` de Ritwick Dey.
- Ouvrez le dossier de votre projet avec *Visual Studio Code* (`File -> Open Folder... (CTRL+K, CTRL+O)`).
- Ouvrez un fichier `.html` dans l'éditeur.
- Cliquez sur l'icône *Go Live* en bas à droite de l'éditeur.

#### Autres solutions

Il existe une multitude de serveurs web différents utilisés pour divers projets. Chacun a sa propre façon de fonctionner, aussi, je ne peux pas détailler chaque outil. Vous pouvez installer un autre serveur web que ceux que je propose, car l'objectif est simplement de pouvoir accéder aux fichiers ressources d'un dossier local depuis votre navigateur.

## Fichiers de base

Pour commencer, vous devez créer un fichier *HTML* qui fera référence au fichier `phaser.js` ainsi qu'à vos fichiers sources de votre jeu.

```html
<!doctype html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Titre</title>
        <script src="libs/phaser.js"></script>
    </head>
    <body>
        <!-- Contenu du document -->
        <script src="scripts/main.js"></script>
    </body>
</html>
```

Dans l'exemple précédent, le fichier *HTML* fait référence au fichier `phaser.js` situé dans un dossier appelé `libs` ainsi qu'au fichier `main.js` situé dans un dossier appelé `scripts`.

*Phaser* ajoute automatiquement un élément `canvas` (avec le contexte approprié) à l'endroit où le script crée un objet `Game`.

**Remarque :** Notez que le fichier `main.js` est référencé **après** la bibliothèque de *Phaser*. Comme il va utiliser les fonctions de cette bibliothèque, il est évident que ces fonctions doivent être connues avant d'y faire référence.

Si vous souhaitez que votre canevas s'adapte à la largeur de la fenêtre du navigateur, ajoutez un style *CSS* à votre fichier *HTML* et définissez la propriété `width` de l'élément `canvas` sur `100%`.

```html
<!doctype html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Test1</title>
        <style>
            canvas {
                width: 100%;
            }
        </style>
        <script src="libs/phaser.js"></script>
    </head>
    <body>
        <!-- Contenu du document -->
        <script src="scripts/main.js"></script>
    </body>
</html>
```

Définir la propriété `width` de l'élément `canvas` sur la valeur `100%` demande au navigateur de redimensionner les canevas du document pour qu'ils prennent toute la largeur de la fenêtre. Cela redimensionne également proportionnellement et automatiquement la hauteur des canevas.

## Programme de base

### Création d'un jeu

Pour le moment, votre projet n'a qu'un fichier *HTML*. Vous devez également créez un fichier *JavaScript* qui contiendra le code source de votre jeu. J'appelle généralement ce fichier `main.js` et je le place dans un dossier appelé `scripts`.

Un jeu *Phaser* est basé sur un objet `Game` mais avant de pouvoir instancier cet objet, vous avez besoin d'une scène et d'un objet de configuration de jeu.

## Scènes

### Créer une scène

Les scènes sont les éléments de plus haut niveau que vous utiliserez dans vos jeux. Elles correspondent aux différents écrans de jeux ou aux différents niveaux. Vous devez définir au moins une scène que vous passerez à l'objet de configuration de jeu.

Pour définir une scène, utilisez le constructeur de la classe [`Scene`](https://photonstorm.github.io/phaser3-docs/Phaser.Scene.html). Il prend en argument une chaîne de caractère unique (qui servira de clé pour faire référence à la scène) ou un [objet de configuration de scène](https://photonstorm.github.io/phaser3-docs/Phaser.Types.Scenes.html#.SettingsConfig).

```js
let scene = new Phaser.Scene('scene_principale');
```

### Définition des méthodes de la scène

Vous devez ensuite définir les méthodes essentielles de la scène.

- La méthode [`init`](https://photonstorm.github.io/phaser3-docs/Phaser.Types.Scenes.html#.SceneInitCallback__anchor) est appelée au démarrage de la scène (à sa création). Elle sert à initialiser les données nécessaires à la scène qui ne concernent pas les ressources à charger.
- La méthode [`preload`](https://photonstorm.github.io/phaser3-docs/Phaser.Types.Scenes.html#.ScenePreloadCallback__anchor) est appelée après la méthode `init`. Elle sert à charger en mémoire les ressources (graphiques, audio, etc...) nécessaires à la scène avant que la scène ne commence à afficher son contenu. Son rôle est de pré-charger les ressources avant leur utilisation pour éviter des erreurs (par exemple, tenter d'afficher une image qui n'est pas encore chargée affichera à la place un simple rectangle de couleur).
- La méthode [`create`](https://photonstorm.github.io/phaser3-docs/Phaser.Types.Scenes.html#.SceneCreateCallback__anchor) est appelée après la méthode `preload` et juste avant que la scène ne commence à afficher son contenu. Elle sert à initialiser les données nécessaires à la scène en utilisant les ressources chargées en mémoire (par exemple, les *sprites*).
- La méthode [`update`](https://photonstorm.github.io/phaser3-docs/Phaser.Scene.html#update__anchor) est appelée avant chaque affichage de la scène. Elle se répète donc en boucle tant que la scène s'exécute. Elle sert à gérer les données du jeu selon diverses conditions.

```js
scene.init = function() {
    
};


scene.preload = function() {
    
};


scene.create = function() {
    
};


scene.update = function() {
    
};
```

### Objet de configuration de jeu

Avant de créer un objet `Game`, vous devez créer un [objet de configuration de jeu](https://photonstorm.github.io/phaser3-docs/Phaser.Types.Core.html#.GameConfig). En général, on l'appelle `config`.

```js
let config = {
    type: Phaser.AUTO,
    width: 640,
    height: 360,
    zoom: 1,
    scene: scene
};
```

Cet objet sert à paramétrer le jeu.

- La propriété `type` définit le type de rendu que le navigateur doit utiliser pour le jeu.
  - La valeur `Phaser.AUTO` indique au navigateur de choisir le rendu *WebGL* en priorité ou *Canvas* si le rendu *WebGL* est inaccessible. **Utilisez de préférence cette valeur.**
  - La valeur `Phaser.WEBGL` indique au navigateur de choisir le rendu *WebGL* (meilleure performance mais n'est pas disponible sur tous les navigateurs).
  - La valeur `Phaser.CANVAS` indique au navigateur de choisir le rendu *Canvas* (moins bonne performance mais fonctionne sur tous les navigateurs).
  - La valeur `Phaser.HEADLESS` indique au navigateur que le programme n'a pas besoin de fenêtre de rendu. Cette valeur est utilisée dans des environnements sans carte graphique pour effectuer des traitements sans avoir besoin d'afficher d'éléments graphiques. Cette valeur est rarement utilisée, mais peut servir pour faire des simulations ou des tests.
- La propriété `scene` définit la scène à lancer au démarrage du jeu. Attribuez-lui l'objet scène que vous souhaitez définir comme scène de démarrage. Consultez la section sur les scènes pour plus d'information.
- La propriété `width` définit la largeur en pixels du rectangle de rendu utilisée par le jeu.
- La propriété `height` définit la hauteur en pixels du rectangle de rendu utilisée par le jeu.
- La propriété `zoom` définit le facteur d'agrandissement des éléments dans la fenêtre de rendu. Pour un jeu en faible résolution, augmentez cette valeur pour agrandir la taille du canevas.

**Remarque :** Vous pouvez également définir une scène anonyme directement dans le fichier de configuration de jeu. Vous devrez alors définir des fonctions pour chaque méthode de la scène.

```js
let config = {
    type: Phaser.AUTO,
    width: 640,
    height: 360,
    zoom: 1,
    scene: {
        init: init,
        preload: preload,
        create: create,
        update: update
    }
};


function init() {
    
}


function preload() {
    
}


function create() {
    
}


function update() {
    
}
```

Si vous voulez utiliser plusieurs scènes, utilisez un tableau :

```js
let scene1 = new Phaser.Scene('scene1');
let scene2 = new Phaser.Scene('scene2');

let config = {
    type: Phaser.AUTO,
    width: 640,
    height: 360,
    zoom: 1,
    scene: [scene1, scene2]
};
```

## Instancier le jeu

Une fois la scène principale et le fichier de configuration de jeu définis, pour créer un jeu avec *Phaser*, il vous suffit d'appeler le constructeur de la classe [`Game`](https://photonstorm.github.io/phaser3-docs/Phaser.Game.html). Ce dernier prend comme argument l'objet de configuration de jeu définit précédemment.

```js
let game = new Phaser.Game(config);
```

## Charger des ressources

Pour chargez des ressources, vous devez le faire dans la méthode de scène `preload`. Celle-ci s'assure que les ressources nécessaires à la scène sont toutes chargées en mémoire avant que la scène ne démarre (lors de l'appel à la méthode `create`).

### Charger une image

Pour charger une image, utilisez la méthode [`Scene.load.image`](https://photonstorm.github.io/phaser3-docs/Phaser.Loader.LoaderPlugin.html#image__anchor) dans la méthode `preload`. Cette méthode prend comme arguments une chaîne de caractère unique (qui servira de clé pour faire référence à l'image) et une chaîne de caractère correspondant au chemin vers le fichier image relativement au fichier *HTML*. *Phaser* prend en charge tous les formats qu'un navigateur peut lire mais je vous conseille de rester sur les format `.png` et `.jpg` ou à défaut `.gif`.

```js
function preload ()
{
    this.load.image('logo', 'images/phaserLogo.png');
}
```

### Charger une spritesheet

Pour charger une spritesheet, utilisez la méthode [`Scene.load.spritesheet`](https://photonstorm.github.io/phaser3-docs/Phaser.Loader.LoaderPlugin.html#spritesheet__anchor) dans la méthode `preload`. Cette méthode prend une chaîne de caractère unique (qui servira de clé pour faire référence à la spritesheet), une chaîne de caractère correspondant au chemin vers le fichier image et un objet contenant les dimensions (`frameWidth` et `frameHeight`) des sprites (voir exemple).

**Attention !** Les sprites du spritesheet doivent tous être de même taille et alignés sur la même grille. *Phaser* prend en charge tous les formats qu'un navigateur peut lire mais je vous conseille de rester sur les format `.png` et `.jpg` ou à défaut `.gif`.

```js
function preload ()
{
    this.load.spritesheet(
        'dude', 
        'assets/dude.png',
        { frameWidth: 32, frameHeight: 48 }
    );
}
```

## Afficher des éléments

Le système de coordonnées de *Phaser* inverse l'axe vertical par rapport au système mathématique habituel. Les valeurs augmentent vers le bas et l'origine du système est positionné dans le coin supérieur gauche du canevas.

### Afficher une image

Une fois vos ressources chargées depuis la fonction `preload`, vous devez ajoutez les images à la scène avec la fonction [`Scene.add.image`](https://photonstorm.github.io/phaser3-docs/Phaser.GameObjects.GameObjectFactory.html#image__anchor). Passez les coordonnées de l'image (par défaut le point d'origine est au centre de l'image) ainsi que la chaîne de caractère unique identifiant la ressource.

```js
function create()
{
    this.add.image(400, 300, 'logo');
}
```

Cette méthode crée un sprite (avec la texture passée en argument), l'ajoute à la scène et renvoie son identifiant. Vous pouvez donc récupérer cet identifiant dans une variable et faire des manipulations sur ce sprite.

```js
let sprite = this.add.image(400, 300, 'logo');
```

**Attention !** Chaque appel à cette méthode ajoute un élément par dessus les précédents. Vous devez donc être vigilant sur l'ordre dans lequel vous souhaitez ajouter vos images à la scène.

### Stocker des variables dans une scène

Pour pouvoir accéder aux sprites créés dans la méthode `create` depuis la méthode `update`, vous devez ajouter des propriétés à la scène en utilisant le mot clé `this`.

```js
function create()
{
    this.sprite = this.add.image(400, 300, 'logo');
}
```

Vous pourrez alors utiliser cette propriété `sprite` dans la méthode `update` pour modifier les propriétés du sprite.

### Déplacer l'origine d'un sprite

Pour déplacer l'origine d'un sprite, utilisez la méthode [`Phaser.GameObjects.Sprite.setOrigin`](https://photonstorm.github.io/phaser3-docs/Phaser.GameObjects.Sprite.html#setOrigin__anchor). Les arguments attendus sont deux nombres compris entre `0` et `1` correspondants aux limites de l'image source. `0, 0` correspond au coin supérieur gauche de l'image. `1, 1` correspond au coin inférieur droit de l'image.

```js
sprite.setOrigin(0.5, 0.5);
```

Vous pouvez également utiliser les propriétés `originX` et `originY` (toujours avec des valeurs comprises entre `0` et `1`).

```js
sprite.originX = 0.5;
sprite.originY = 0.5;
```

**Attention !** Par défaut, l'origine d'un sprite est placée en son centre (`0.5, 0.5`).

### Modifier la position d'un sprite

Pour modifier la position d'un sprite, utilisez la méthode [`Phaser.GameObjects.Sprite.setPosition`](https://photonstorm.github.io/phaser3-docs/Phaser.GameObjects.Sprite.html#setPosition__anchor). Les arguments attendus sont deux nombres correspondants aux coordonnées *x* et *y* du sprite dans le système de coordonnées de l'objet parent (par défaut, la scène). Vous pouvez également accéder directement aux propriétés [`x`](https://photonstorm.github.io/phaser3-docs/Phaser.GameObjects.Sprite.html#x__anchor) et [`y`](https://photonstorm.github.io/phaser3-docs/Phaser.GameObjects.Sprite.html#y__anchor) pour en modifier la valeur.

```js
sprite.setPosition(320, 180);
sprite.x = 320;
sprite.y = 180;
```

#### Modifier la position z d'un sprite

Les sprites ont une propriété [`depth`](https://photonstorm.github.io/phaser3-docs/Phaser.GameObjects.Sprite.html#depth__anchor) (par défaut à `0`) que vous pouvez modifier pour changer l'ordre d'affichage. Plus la valeur est importante, plus le sprite apparait devant les autres.

```js
sprite.depth = 1;
```

### Modifier l'échelle d'un sprite

Pour modifier l'échelle d'un sprite, utilisez la méthode [`Phaser.GameObjects.Sprite.setScale`](https://photonstorm.github.io/phaser3-docs/Phaser.GameObjects.Sprite.html#setScale__anchor).  Les arguments attendus sont deux nombres correspondants aux facteurs d'échelle des axes *x* et *y* du sprite dans le système de coordonnées de l'objet parent (par défaut, la scène). Passez une seule valeur pour que les deux axes prennent le même facteur d'échelle. Vous pouvez également accéder directement aux propriétés [`scaleX`](https://photonstorm.github.io/phaser3-docs/Phaser.GameObjects.Sprite.html#scaleX__anchor) et [`scaleY`](https://photonstorm.github.io/phaser3-docs/Phaser.GameObjects.Sprite.html#scaleY__anchor) pour en modifier la valeur.

```js
sprite.setScale(2, 0.5);
sprite.setScale(2);
sprite.scaleX = 2;
sprite.scaleY = 0.5;
```

**Remarque :** Ces facteurs d'échelle ne modifient pas les propriétés `width` et `height` du sprite mais multiplient ces dernières pour définir les propriétés `displayWidth` et `displayHeight`. Vous pouvez également accéder directement à ces propriétés [`displayWidth`](https://photonstorm.github.io/phaser3-docs/Phaser.GameObjects.Sprite.html#displayWidth__anchor) et [`displayHeight`](https://photonstorm.github.io/phaser3-docs/Phaser.GameObjects.Sprite.html#displayHeight__anchor) pour en modifier la valeur (en pixels).

```js
sprite.displayWidth = 200;
sprite.displayHeight = 100;
```

### Retourner un sprite

Pour retourner un sprite, modifiez les propriétés booléennes `flipX` et `flipY` du sprite.

```js
sprite.flipX = true;
sprite.flipY = true;
```

### Modifier l'angle d'un sprite

Pour modifier l'angle d'un sprite, utilisez la méthode [`Phaser.GameObjects.Sprite.setAngle`](https://photonstorm.github.io/phaser3-docs/Phaser.GameObjects.Sprite.html#setAngle__anchor).  L'argument attendu est un angle en degrés correspondant à l'angle de rotation du sprite dans le système de coordonnées de l'objet parent (par défaut, la scène). Vous pouvez également accéder directement à la propriété [`angle`](https://photonstorm.github.io/phaser3-docs/Phaser.GameObjects.Sprite.html#angle__anchor) pour en modifier la valeur (un entier). Pour modifier l'angle en radians, utilisez la méthode [Phaser.GameObjects.Sprite.setRotation](https://photonstorm.github.io/phaser3-docs/Phaser.GameObjects.Sprite.html#setRotation__anchor) ou la propriété [rotation](https://photonstorm.github.io/phaser3-docs/Phaser.GameObjects.Sprite.html#rotation__anchor)().

```js
sprite.setAngle(90);
sprite.angle = 90;
sprite.setRotation(Math.PI / 2);
sprite.rotation = Math.PI / 2;
```

**Remarque :** Le sens de rotation positif est le sens horaire.

## Obtenir les dimensions de la fenêtre de rendu

Pour obtenir les dimensions de la fenêtre de rendu, utilisez les propriétés de scène `Scene.sys.game.config.width` et `this.sys.game.config.height`.

```js
const largeurEcran = this.sys.game.config.width;
const hauteurEcran = this.sys.game.config.height;
```

## Ajouter de la physique

### Moteur de physique arcade

Vous devez préciser quel moteur de physique vous souhaitez utiliser via l'objet de ocnfiguration.

```js
let config = {
    ...,
    physics: {
        default: 'arcade',
        arcade: {
            gravity: { y: 300 },
            debug: false
        }
    },
    ...
};
```

Le moteur de physique arcade utilise deux types de corps physiques :

- Un corps dynamique est un objet qui peut se déplacer suivant les forces auquel il est soumis.
- Un corps statique est un objet fixe et insensible aux diverses forces.

#### Corps statiques

La méthode `staticGroup` crée un groupe de corps statiques. Grouper divers corps de même nature vous permet de les contrôler comme une seule entité.

```js
let platforms = this.physics.add.staticGroup();
```

Les groupes sont capables de créer leurs propres objets de jeu grâce à la méthode `create`. Un groupe de corps physiques créera automatiquement des enfants avec la physique appropriée.

```js
platforms.create(400, 568, 'ground').setScale(2).refreshBody();
platforms.create(600, 400, 'ground');
platforms.create(50, 250, 'ground');
platforms.create(750, 220, 'ground');
```

**Remarque :** La méthode `setScale` vous permet de modifier l'échelle d'un corps mais vous devez ensuite appeler la méthode `refreshBody` pour ajuster le corps physique **statique** à la nouvelle taille.

#### Corps dynamiques

La méthode `physics.add.sprite` crée un sprite comme la méthode `add.image` mais lui attache un corps dynamique.

```js
let player = this.physics.add.sprite(100, 450, 'dude');
```

La méthode `physics.add.group` crée un groupe de corps dynamiques.

```js
let stars = this.physics.add.group({
    key: 'star',
    repeat: 11,
    setXY: { x: 12, y: 0, stepX: 70 }
});
```

- `key` définit la texture à utiliser.
- `repeat` crée le nombre de corps dynamiques précisé plus un (qui est automatiquement créé par défaut).
- `setXY` définit la position de chaque corps avec les propriété `x` et `y` et le décalage de chaque itération avec les propriétés `stepX` et `stepY`.



Vous pouvez ensuite appeler des méthodes pour spécifier son comportement.

```js
player.setBounce(0.2);
player.setCollideWorldBounds(true);
stars.children.iterate(function (child) {
    child.setBounceY(Phaser.Math.FloatBetween(0.4, 0.8));
});
```

Le sprite possède une propriété `body` qui vous permet d'accéder aux méthodes dédiées au corps dynamique.

```js
player.body.setGravityY(300);
```

Ajouter ensuite un objet de collision entre deux corps physiques (ou des groupes).

```js
this.physics.add.collider(player, platforms);
this.physics.add.collider(stars, platforms);
this.physics.add.overlap(player, stars, collectStar, null, this);


function collectStar(player, star)
{
    star.disableBody(true, true);
}
```

Pour déterminer si un corps en touche un autre, utilisez la propriété `touching.down`.

```js
if (player.body.touching.down)
{
    // contact
}
```

## Contrôles

La méthode `createCursorKeys` de l'objet `input.keyboard` crée un objet qui surveille automatiquement les touches fléchées du clavier.

```js
let cursors = this.input.keyboard.createCursorKeys();
```

La propriété `isDown` des objets `cursors.left`, `cursors.right`, `cursors.up` et `cursors.down` (qui sont des instances d'un objet `Key`) est `true` si la touche associée est enfoncée. Utilisez cette propriété dans la méthode `update`.

```js
if (cursors.left.isDown)
{
    player.setVelocityX(-160);
    player.anims.play('left', true);
}
else if (cursors.right.isDown)
{
    player.setVelocityX(160);
    player.anims.play('right', true);
}
else
{
    player.setVelocityX(0);
    player.anims.play('turn');
}

if (cursors.up.isDown && player.body.touching.down)
{
    player.setVelocityY(-330);
}
```

## Spritesheets et animations

```js
this.anims.create({
    key: 'left',
    frames: this.anims.generateFrameNumbers('dude', { start: 0, end: 3 }),
    frameRate: 10,
    repeat: -1
});

this.anims.create({
    key: 'turn',
    frames: [ { key: 'dude', frame: 4 } ],
    frameRate: 20
});

this.anims.create({
    key: 'right',
    frames: this.anims.generateFrameNumbers('dude', { start: 5, end: 8 }),
    frameRate: 10,
    repeat: -1
});
```

## Exemple très simple

Fichier `index.html` :

```html
<!DOCTYPE html>
<html>
    <head>
        <script src="libs/phaser.js"></script>
    </head>
    <body>
        <!-- Contenu du document -->
        <script src="scripts/main.js"></script>
    </body>
</html>
```

Fichier `main.js` :

```js
var config = {
    type: Phaser.AUTO,
    width: 800,
    height: 600,
    physics: {
        default: 'arcade',
        arcade: {
            gravity: { y: 200 }
        }
    },
    scene: {
        preload: preload,
        create: create
    }
};

var game = new Phaser.Game(config);

function preload ()
{
    this.load.setBaseURL('http://labs.phaser.io');

    this.load.image('sky', 'assets/skies/space3.png');
    this.load.image('logo', 'assets/sprites/phaser3-logo.png');
    this.load.image('red', 'assets/particles/red.png');
}

function create ()
{
    this.add.image(400, 300, 'sky');

    var particles = this.add.particles('red');

    var emitter = particles.createEmitter({
        speed: 100,
        scale: { start: 1, end: 0 },
        blendMode: 'ADD'
    });

    var logo = this.physics.add.image(400, 100, 'logo');

    logo.setVelocity(100, 200);
    logo.setBounce(1, 1);
    logo.setCollideWorldBounds(true);

    emitter.startFollow(logo);
}
```


## Exemples en ligne

Consultez le site [http://labs.phaser.io/](http://labs.phaser.io/) pour une longue liste d'exemples créés avec Phaser.
