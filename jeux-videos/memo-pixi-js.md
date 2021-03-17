# Mémo PixiJS

*par flashjaysan*

**The golden rule of rendering with WebGL: The less the CPU talks to GPU, the faster things are.**

## Introduction

*PixiJS* est une bibliothèque *JavaScript* de rendu graphique 2D performante et légère que l'on peut utiliser pour la création de jeux vidéos. Elle possède de très nombreuses fonctionnalités qui simplifient la création de jeux utilisant le standard *HTML5* pour les navigateurs web.

## Installation

### Serveur web

Pour tester vos jeux localement, vous aurez besoin d'un serveur web.

#### Mongoose web server

Sur Windows, je vous recommande le serveur web [Mongoose](http://cesanta.com/downloads.html) qui est très léger et qui ne nécessite aucune installation. Placez simplement le fichier `Mongoose-free-X.X.exe` dans un dossier contenant vos projets *PixiJS* et exécutez-le. Une fenêtre de navigateur s'ouvre et affiche les fichiers contenus dans ce dossier.

**Remarque :** Si vous fermez le navigateur, cliquez sur l'icône de *Mongoose* dans la zone de notification en bas à droite et choisissez l'option `Go to my address:...` pour ouvrir à nouveau le navigateur sur le serveur web.

Pour fermer le serveur web, cliquez sur l'icône de *Mongoose* dans la zone de notification en bas à droite et choisissez l'option `Exit`.

#### Brackets

Une autre solution simple est d'utiliser l'éditeur de code [Brackets](brackets.io) pour programmer votre jeu et de cliquer sur l'icône en forme d'éclair en haut à droite de l'éditeur pour ouvrir automatiquement le navigateur par défaut avec un serveur web pointant sur l'emplacement d'un fichier *HTML* en cours d'édition.

- Ouvrez simplement le dossier de votre projet avec *Brackets* (`Fichier -> Ouvrir un dossier... (CTRL+ALT+O)`).
- Ouvrez un fichier `.html` dans l'éditeur.
- Cliquez sur l'icône *éclair* en haut à droite de l'éditeur.

#### Visual Studio Code

Une autre solution simple est d'utiliser l'éditeur de code [Visual Studio Code](https://code.visualstudio.com/) avec l'extension `Live Server` pour programmer votre jeu et de cliquer sur l'icône `Go Live` en bas à droite de l'éditeur pour ouvrir automatiquement le navigateur par défaut avec un serveur web pointant sur l'emplacement d'un fichier *HTML* en cours d'édition.

- Installez l'extension `Live Server` de Ritwick Dey.
- Ouvrez le dossier de votre projet avec *Visual Studio Code* (`File -> Open Folder... (CTRL+K, CTRL+O)`).
- Ouvrez un fichier `.html` dans l'éditeur.
- Cliquez sur l'icône *Go Live* en bas à droite de l'éditeur.

### Télécharger PixiJS

Téléchargez le fichier [pixi.min.js](https://pixijs.download/release/pixi.min.js).

**Remarque :** Si vous souhaitez obtenir des messages d'erreurs plus clairs lors du développement, téléchargez plutôt la version non optimisée [pixi.js](https://pixijs.download/dev/pixi.js). Si vous le souhaitez, vous pouvez également télécharger le [code source](https://github.com/pixijs/pixi.js).

Les versions antérieures de *PixiJS* sont disponibles [ici](https://github.com/pixijs/pixi.js/releases).

**Remarque :** Par défaut, *PixiJS* V5 ne prend plus en charge que `WebGL`. Pour utiliser le moteur de rendu [`CanvasRenderingContext2D`](https://developer.mozilla.org/fr/docs/Web/API/CanvasRenderingContext2D), vous devez télécharger le fichier `pixi-legacy.js` à la place du fichier `pixi.js`. [Plus d'information](https://medium.com/goodboy-digital/pixijs-v5-lands-5e112d84e510).

### Editeur de code

Vous pouvez à présent commencer à créer vos projets avec *PixiJS*. Si ce n'est déjà fait, vous pouvez également installer un éditeur de code ou un *IDE*. [Brackets](brackets.io), [Visual Studio Code](https://code.visualstudio.com/), [Atom](https://atom.io/) ou [Sublime Text](https://www.sublimetext.com/), sont tous de bons choix très populaires.

## Préparatifs

Pour chaque projet *PixiJS*, je vous conseille de créer un dossier séparé où vous placerez une copie du fichier `pixi.min.js` et où vous créerez un fichier *JavaScript* et un fichier *HTML*.

- Créez un dossier qui servira de dossier de travail à votre projet *PixiJS*.
- Placez le fichier `pixi.min.js` (ou le fichier `pixi.js` lors du développement) dans le dossier précédent (ou dans un sous-dossiers).

Pour bien organiser mon projet, je place généralement le fichier `pixi.min.js` dans un dossier appelé `libs`.

### Fichier *JavaScript* de base

En plus du fichier `pixi.min.js`, vous devez créer un fichier de script *JavaScript* qui contiendra votre programme.

- Pour créer un fichier de script *JavaScript*, créez un nouveau fichier texte et modifiez son extension en `.js`.
- Ouvrez-le avec un éditeur de code ou un éditeur de texte.
- Vous n'avez plus qu'à coder votre application dans ce fichier.

Dans ce mémo, nous appelerons le fichier *JavaScript* `main.js` et nous le placerons dans un dossier `scripts`. Ce fichier contiendra le code source principal de votre jeu.

**Remarque :** Vous avez la possibilité de vous passer de ce fichier de script *JavaScript* ; il vous suffit de saisir votre programme dans une balise `<script>` directement dans un fichier *HTML*. Toutefois, afin d'améliorer la lisibilité de votre projet, je vous déconseille cette approche. Le rôle de chaque fichier sera ainsi bien séparé. Pour bien organiser mon projet, je place généralement mes fichiers de script *JavaScript* dans un dossier appelé `scripts`.

### Fichier *HTML* de base

En plus du fichier `pixi.min.js` et de votre fichier de script *JavaScript*, vous devez créer un fichier *HTML* pour contenir votre application. Ce fichier d'extension `.html` doit faire référence au fichier `pixi.min.js` ainsi qu'au fichier de script *JavaScript* où se trouve le code source de votre application *PixiJS*.

- Pour créer un fichier *HTML*, dans votre dossier de travail, créez un nouveau fichier texte et modifiez son extension en `.html`.
- Ouvrez-le avec un éditeur de code ou avec un editeur de texte et saisissez le code suivant :

```html
<!doctype html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Titre du projet</title>
        <script src="libs/pixi.min.js"></script>
        <script src="scripts/main.js"></script>
    </head>
    <body>
    </body>
</html>
```

Le but de ce fichier est simplement de contenir un code *HTML* valide avec des balises `<script>` faisant référence au fichier `pixi.min.js` et à votre fichier de script principal (ici, `main.js`).

**Remarque :** Notez que je préconise l'utilisation d'un fichier de script *JavaScript* externe au document *HTML* mais vous pouvez créer une balise `<script>` et saisir votre code *JavaScript* à l'intérieur. Si le fichier `pixi.min.js` se trouve dans un sous-dossier (appelé par exemple `libs`), passez à la balise `script`, le chemin relatif au fichier *HTML* (par exemple `scr="libs/pixi.min.js"`). De même, si le fichier `main.js` se trouve dans un sous-dossier (appelé par exemple `scripts`), passez à la balise `script`, le chemin relatif au fichier *HTML* (par exemple `scr="scripts/main.js"`).

### Tester si PixiJS fonctionne

Pour tester si *PixiJS* fonctionne, saisissez le code suivant dans le fichier `main.js` :

```javascript
let type = "WebGL";
if (!PIXI.utils.isWebGLSupported()) {
  type = "canvas";
}

PIXI.utils.sayHello(type);
```

- Lancez votre serveur web et ouvrez le fichier *HTML* dans un navigateur.
- Ouvrez la console de votre navigateur. Si tout est bien configuré, vous devriez voir un message décrivant la version de *PixiJS* ainsi que le moteur de rendu pris en charge par votre navigateur (`WebGL` ou `canvas`).

```
    PixiJS 5.1.5 - ✰ WebGL ✰      http://www.pixijs.com/    ♥♥♥ 
```

Si le message précédent s'est bien affiché dans la console du navigateur, vous êtes prêt à utiliser *PixiJS*. Effacez le contenu du fichier *JavaScript* avant de continuer.

### Retirer l'affichage de version de *PixiJS* dans la console

Par défaut, *PixiJS* appelle automatiquement la méthode `sayHello` de l'objet `utils` qui affiche dans la console du navigateur la version de *PixiJS* utilisée. Si vous souhaitez masquer cette information, appelez la méthode `skipHello` de l'objet `utils` avant tout appel à une autre fonction de *PixiJS*.

```javascript
// Supprime l'affichage de la version de PixiJS dans la console du navigateur
PIXI.utils.skipHello();
```

## Exemples à consulter

Rendez-vous sur [https://pixijs.io/examples/](https://pixijs.io/examples/) pour consulter des programmes exemples et voir leur exécution démontrant le potentiel de *PixiJS*. C'est également un très bonne source d'information pour commencer à apprendre à utiliser *PixiJS*.

## Concepts généraux de *PixiJS*

- *PixiJS* a besoin d'un canevas (`canvas`) dans un document *HTML* pour y attacher son moteur de rendu (`renderer`). Ce dernier s'occupe de l'affichage des objets graphiques dans le canevas.
- Pour maintenir une fréquence d'affichage constante, *PixiJS* utilise un *gestionnaire de temps* (`ticker`).
- Pour charger en mémoire les ressources nécessaires à votre projet, *PixiJS* utilise un *chargeur de ressources* (`loader`). Ce dernier charge les ressources de type image dans un cache de texture `TextureCache` (pour éviter de charger plusieurs fois la même image) ou directement en mémoire vidéo (où elles deviennent des objets `Texture`s).
- Enfin, *PixiJS* tourne autour du concept de conteneurs (`Container`). Un conteneur peut contenir des éléments graphiques ou d'autres conteneurs. Cela constitue une arborescence d'éléments graphiques et de conteneurs. Un conteneur racine doit être créé et passé au moteur de rendu. Ce dernier s'occupera d'afficher tout ce que le conteneur racine contient.

**Remarque :** L'ordre dans lequel vous ajoutez les éléments graphiques à un conteneur détermine l'ordre dans lequel ils s'afficheront. Un élément ajouté après d'autres s'affichera devant ces derniers.

## Configurer l'application manuellement

### Créer un moteur de rendu

Commencez par créer un moteur de rendu. La meilleure façon de faire est d'utiliser la méthode [autoDetectRenderer](http://pixijs.download/release/docs/PIXI.html#.autoDetectRenderer) qui prend en paramètre un objet `options` contenant les propriétés définissant les options de configuration (la documentation liste les valeurs par défaut) et renvoie un objet `Renderer` si le navigateur prend en charge *WebGL* ou un objet `CanvasRenderer` dans le cas contraire. Elle crée également automatiquement un élément `canvas` stockée dans sa propriété `view`. Il vous suffit donc ensuite d'ajouter cet élément à votre document *HTML*.

```js
// Crée un objet Renderer (WebGL) ou un objet CanvasRenderer
let renderer = PIXI.autoDetectRenderer({width: 640, height: 360});
// Ajoute l'élément canvas associé au document HTML
document.body.appendChild(renderer.view);
```

**Remarque :** Au lieu d'utiliser la méthode `autoDetectRenderer`, vous pouvez manuellement forcer la création d'un moteur de rendu *WebGL* en appelant le constructeur de la classe [`Renderer`](http://pixijs.download/release/docs/PIXI.Renderer.html). De même, vous pouvez manuellement forcer la création d'un moteur de rendu *CanvasRenderer* en appelant le constructeur de la classe [`CanvasRenderer`](http://pixijs.download/release/docs/PIXI.CanvasRenderer.html). 

Si vous le souhaitez, vous pouvez également créer un canevas dans votre document *HTML* et le passer à la propriété `view` lors de l'appel à la méthode `autoDetectRenderer`.

Fichier *HTML* :

```html
<!doctype html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Titre du projet</title>
    </head>
        <!--crée une balise <canvas> portant l'id 'pixiCanvas'-->
        <canvas id=pixiCanvas></canvas>
        <script src="libs/pixi.min.js"></script>
        <script src="scripts/main.js"></script>
    <body>
    </body>
</html>
```

Fichier *JavaScript* :

```js
// Récupère le canevas ayant l'id 'pixiCanvas'
const pixiCanvas = document.getElementById('pixiCanvas');
// Associe au moteur de rendu le canevas 'pixiCanvas'
let renderer = new PIXI.autoDetectRenderer({width: 640, height: 360, view: pixiCanvas});
```

Le moteur de rendu est responsable de l'affichage d'un conteneur racine (qui contiendra tous les autres conteneurs à afficher).

### Créer un conteneur racine

Avec la méthode manuelle, aucun conteneur racine n'est créé. Créer un conteneur racine avec le constructeur de la classe [`Container`](http://pixijs.download/release/docs/PIXI.Container.html). Utilisez la méthode `render` du moteur de rendu à chaque fois que vous souhaitez afficher le conteneur racine.

```js
// Crée un objet conteneur appelé 'stage'
const stage = new PIXI.Container();
// affiche le conteneur 'stage'
renderer.render(stage);
```

### Créer un gestionnaire de temps

Avec la méthode manuelle, aucun gestionnaire de temps n'est créé. Créez un gestionnaire de temps avec le constructeur de la classe [`Ticker`](http://pixijs.download/release/docs/PIXI.Ticker_.html). Attachez un fonction au gestionnaire de temps avec la méthode `add` puis lancez le gestionnaire avec la méthode `start`.

```js
// Crée un objet gestionnaire de temps
const ticker = new PIXI.Ticker();
// Attache une fonction au gestionnaire de temps
ticker.add(animate);
// Démarre le gestionnaire de temps
ticker.start();
```

**Remarque :** La fonction `animate` sera alors appelée à intervalle régulier créant ainsi la boucle de jeu. Vous pouvez nommer cette fonction comme bon vous semble mais vous devez bien évidemment penser à la définir. En dernière instruction de cette fonction, demandez au moteur de rendu d'afficher le conteneur racine avec la méthode `render`.


```js
function animate() {
    // Instructions d'animation
    // Demander au moteur de rendu d'afficher le conteneur racine
    renderer.render(stage);
}
```

## Configurer l'application automatiquement

La classe `Application` vous permet de créer de de configurer automatiquement un moteur de rendu, un conteneur racine, un gestionnaire de temps ainsi qu'un canevas *HTML* associé.

### La classe `Application`

La classe `Application` est faite pour simplifier la création d'une nouvelle application *PixiJS*. Cette classe crée automatiquement le moteur de rendu,  le conteneur racine de l'application, le gestionnaire de temps, et l'élément canevas *HTML* associé.

- Créez un nouvel objet [`Application`](http://pixijs.download/release/docs/PIXI.Application.html). Le constructeur prend en paramètre un objet `options` contenant les propriétés définissant les options de configuration (la documentation liste les valeurs par défaut) et renvoie un objet `Application`.
- Ajoutez ensuite le canevas au document *HTML* avec la méthode `document.body.appendChild` en lui passant la propriété `view` qui correspond à un élément `canvas` *HTML* où s'affichera l'application. Avec cette méthode, il vous est donc inutile de créer manuellement un élément `canvas` dans le fichier *HTML*.

```javascript
// Crée un objet Application
const app = new PIXI.Application({width: 640, height: 360});
// Ajoute automatiquement le canevas de l'application au document HTML
document.body.appendChild(app.view);
```

**Remarque :** Vous pouvez toutefois créer un canevas manuellement dans votre document *HTML* et le passer au constructeur de la classe `Application` en tant que propriété `view`.

Fichier *HTML* :

```html
<!doctype html>
<html>
    <head>
        <meta charset="utf-8">
        <title>Titre du projet</title>
    </head>
        <!--crée une balise <canvas> portant l'id 'pixiCanvas'-->
        <canvas id=pixiCanvas></canvas>
        <script src="libs/pixi.min.js"></script>
        <script src="scripts/main.js"></script>
    <body>
    </body>
</html>
```

Fichier *JavaScript* :

```js
// Récupère le canevas ayant l'id 'pixiCanvas'
const pixiCanvas = document.getElementById('pixiCanvas');
// Associe au moteur de rendu le canevas 'pixiCanvas'
const app = new PIXI.Application({width: 640, height: 360, view: pixiCanvas});
```

L'objet `Application` détermine automatique (par défaut) si le navigateur prend en charge `WebGL` et configure le canevas dans ce mode s'il est disponible.

**Remarque :** Il semble que la version 5 de *PixiJS* utilise uniquement le moteur de rendu `WebGL`. Pour utiliser le moteur de rendu `canvas` *HTML5*, il faut utiliser le fichier `pixi-legacy.js`.

#### La propriété `view`

La propriété [`view`](http://pixijs.download/release/docs/PIXI.Application.html#view) de l'objet `Application` correspond à l'élément `canvas` *HTML* dans lequel est rendu l'application. Vous pouvez ajouter la propriété `view` au document *HTML* pour faire apparaître le canevas dans la fenêtre.

```js
// Ajoute un nouvel élément `canvas` au document *HTML*
document.body.appendChild(app.view);
```

#### La propriété `stage`

La propriété [`stage`](http://pixijs.download/release/docs/PIXI.Application.html#stage) (de type [Container](http://pixijs.download/release/docs/PIXI.Container.html)) de l'objet `Application` correspond au conteneur racine du moteur de rendu. Tout ce que vous voulez faire apparaître à l'écran doit être attaché à ce conteneur racine ou à un de ses enfants en utilisant la méthode `addChild`.

```js
// Ajoute le sprite 'image' au conteneur racine
app.stage.addChild(image);
```

#### La propriété `renderer`

La propriété [`renderer`](http://pixijs.download/release/docs/PIXI.Application.html#renderer) (de type [Renderer](http://pixijs.download/release/docs/PIXI.Renderer.html) ou [CanvasRenderer](http://pixijs.download/release/docs/PIXI.CanvasRenderer.html)) de l'objet `Application` correspond au moteur de rendu associé au canevas *HTML*. Selon que le navigateur prend en charge *WebGL* ou non, cet objet est de type `Renderer` ou `CanvasRenderer`. Pour afficher le conteneur racine, utilisez la méthode `render`.

```javascript
app.renderer.render(app.stage);
```

#### La propriété `ticker`

La propriété [`ticker`](http://pixijs.download/release/docs/PIXI.Application.html#ticker) (de type [PIXI.Ticker](http://pixijs.download/release/docs/PIXI.Ticker_.html)) de l'objet `Application` correspond au gestionnaire de temps de l'application. Vous devez passer à ce gestionnaire une fonction qui sera appelée à intervalle régulier.

```js
// Associe au gestionnaire de temps la fonction 'animate'
app.ticker.add(animate);

function animate() {
    // Instructions d'animation
}
```

**Remarque :** La fonction `animate` sera appelée à intervalle régulier créant ainsi la boucle de jeu. Vous pouvez nommer cette fonction comme bon vous semble mais vous devez bien évidemment penser à la définir. En dernière instruction de cette fonction, demandez au moteur de rendu d'afficher le conteneur racine avec la méthode `render`.


```js
function animate() {
    // Instructions d'animation
    // Demander au moteur de rendu d'afficher le conteneur racine
    app.renderer.render(app.stage);
}
```

## Eléments graphiques

### La classe `Loader`

*PixiJS* fournit automatiquement un chargeur de ressources par défaut. Depuis la version 5, vous pouvez utiliser l'objet `shared` de la classe `Loader`. Vous pouvez toutefois instancier votre propre chargeur de ressources.

```js
const loader = PIXI.Loader.shared;
```

ou

```js
const loader = new PIXI.Loader();
```

La classe `Loader` de *PixiJS* est une extension de la classe [`Loader`](https://github.com/englercj/resource-loader/blob/master/src/Loader.ts) d'`englercj`. Les méthodes listées ci-dessous ne sont pas documentées par *PixiJS*.

Utilisez la méthode `add` pour charger une ressource.

```js
loader.add('chemin/image.png');
loader.add('id_image','chemin/image.png');
```

Vous pouvez enchainer les appels pour charger plusieurs ressources.

```js
loader
    .add('image1.png')
    .add('image2.png')
    .add('image3.png');
```

Vous pouvez également passer un tableau.

```js
loader.add(['image1.png', 'image2.png', 'image3.png']);
```

Utilisez la méthode `load` pour appeler une fonction de votre choix une fois le chargement des ressources terminé.

```js
loader.load(init);

function init() {
    // instructions à exécuter uniquement lorsque les ressources sont totalement chargées
}
```

Une ressource (de type [`Resource`](https://github.com/englercj/resource-loader/blob/master/src/Resource.ts)) chargée est stockée dans l'objet `resources` (de type `Loader.ResourceMap` ou plus exactement `Partial<Record<string, Resource>>`) de l'objet `Loader`. Vous pouvez accéder à une ressource spécifique en utilisant la nom ou le chemin d'accès de la ressource en tant que clé sur l'objet `resources`.

```js
const image1_resource = loader.resources['image1.png'];
```

**Remarque :** *PixiJS* utilise par défaut le moteur de rendu *WebGL* pour gérer l'affichage. Cela signifie que *PixiJS* utilise l'accélération matériel (la carte graphique). C'est pourquoi vous devez convertir vos images (stockées en tant que fichiers) en *textures*. Ces dernières sont simplement des images converties dans un format compréhensible par la carte graphique et stockées dans sa mémoire.

Vous pouvez accéder à la texture d'une ressource image grâce à sa propriété `texture`.

```js
const image1_texture = image1_resource.texture;
```

### La classe `Texture`

La classe [`Texture`](http://pixijs.download/release/docs/PIXI.Texture.html) correspond à une image (ou une partie d'image) convertie dans une format pris en charge par le GPU. Utilisez sa méthode `from` pour charger un fichier image au format `.png`, `.gif` ou `.jpg` sans passer par le chargeur de ressources.

```js
// Crée une texture à partir d'un fichier image
const texture = PIXI.Texture.from('assets/images/image.png');
```

Plusieurs objets `Texture`s peuvent faire référence à la même texture de base [`BaseTexture`](http://pixijs.download/release/docs/PIXI.BaseTexture.html) mais sélectionner seulement une petite section grâce à la propriété `frame` de type `Rectangle`. Si vous modifiez cette propriété, appelez la méthode `updateUvs` ensuite.

```js
texture.frame = new PIXI.rectangle(x, y, largeur, hauteur);
texture.updateUvs();
```

### La classe `Sprite`

La classe `Sprite` correspond à un conteneur associé à une texture. En plus de la référence à un objet `Texture`, cet objet contient des informations de transformation spaciale (position, rotation, etc...). Vous pouvez créer un objet `Sprite` en passant au constructeur un objet `Texture`. 

```js
// Crée un sprite à partir d'une texture
const sprite = new PIXI.Sprite(texture);
```

Vous pouvez toutefois créer un nouveau sprite directement en passant le chemin d'un fichier image à la méthode `from`.

```js
// Crée un sprite à partir d'un fichier image
const sprite = PIXI.Sprite.from('assets/images/image.png');
```

Une fois un sprite créé, vous pouvez l'attacher au conteneur racine (ou à n'importe quel sous conteneur) du moteur de rendu ou à un de ses enfants.

```js
// Ajoute le sprite au conteneur racine
app.stage.addChild(sprite);
```

Pour supprimer un sprite d'un conteneur................









**Remarque :** Pour faire apparaître le sprite, pensez à appeler la méthode `render` du moteur de rendu.

```js
renderer.render(stage);
```

ou (avec un objet `Application`)

```js
app.renderer.render(app.stage);
```

#### Positionner un sprite

Les propriétés `x` et `y` (alias des propriétés `position.x` et `position.y`) vous permettent de positionner le sprite dans le conteneur parent (par défaut le conteneur racine).

```js
// Attribue la valeur 10 aux proprités x et y de la propriété position
sprite.position.set(10); // Identique à sprite.position.set(10, 10);
```

ou :

```js
// Attribue la valeur 10 à la propriété x de la propriété position
sprite.x = 10; // identique à sprite.position.x = 10;
// Attribue la valeur 10 à la propriété y de la propriété position
sprite.y = 10; // identique à sprite.position.y = 10;
```

Pour centrer le sprite sur le canevas, vous pouvez faire comme ceci :

```js
// Centre horizontalement le sprite sur le canevas
sprite.x = app.renderer.width / 2;
// Centre verticalement le sprite sur le canevas
sprite.y = app.renderer.height / 2;
```

#### Positionner le point d'ancrage de la texture d'un sprite

La propriété `anchor` vous permet de positionner le point d'ancrage de la texture du sprite relativement a ses dimensions. Les valeurs possibles sont donc comprises entre `0` (gauche et haut) et `1` (bas et droite). Par défaut le point d'ancrage est situé dans le coin supérieur gauche de la texture `(0, 0)`.

```js
// Attribue la valeur 0.5 aux proprités x et y de la propriété anchor
sprite.anchor.set(0.5); // Identique à sprite.anchor.set(0.5, 0.5);
```

ou :

```js
// Attribue la valeur 0.5 à la propriété x de la propriété anchor
sprite.anchor.x = 0.5;
// Attribue la valeur 0.5 à la propriété y de la propriété anchor
sprite.anchor.y = 0.5;
```

#### Faire pivoter un sprite

Les propriétés `rotation` et `angle` indiquent l'angle de rotation du sprite. `rotation` s'exprime en radians et `angle` s'exprime en degrés.

```js
// Définit l'angle de rotation
sprite.angle = 90; // Identique à sprite.rotation = Math.PI / 2;
```

#### Positionner le point de pivot d'un sprite

La propriété `pivot` vous permet de positionner le point de pivot du sprite en pixels depuis le coin supérieur gauche.

```javascript
// Attribue la valeur 5 aux proprités x et y de la propriété pivot
sprite.pivot.set(5); // Identique à sprite.pivot.set(5, 5);
```

ou :

```js
// Attribue la valeur 5 à la propriété x de la propriété pivot
sprite.pivot.x = 5;
// Attribue la valeur 5 à la propriété y de la propriété pivot
sprite.pivot.y = 5;
```

#### Modifier l'échelle du sprite

La propriété `scale` vous permet de modifier l'échelle du sprite.

```javascript
// Attribue la valeur 2 aux proprités x et y de la propriété scale
sprite.scale.set(2); // Identique à sprite.scale.set(2, 2);
```

ou :

```js
// Attribue la valeur 5 à la propriété x de la propriété scale
sprite.scale.x = 2;
// Attribue la valeur 5 à la propriété y de la propriété scale
sprite.scale.y = 2;
```

## Astuces diverses

### Définir la couleur de fond du canevas

Pour modifier la couleur de fond du canevas (noire par défaut), attribuez une couleur (une valeur hexadécimale à six chiffres) à la propriété `backgroundColor` du moteur de rendu (`PIXI.Application.renderer` pour un moteur de rendu créé automatiquement par l'objet `PIXI.Application`).

```javascript
// Définit la couleur de fond
app.renderer.backgroundColor = 0xFF0000;
```

### Obtenir les dimensions du canevas

Si vous avez besoin des dimensions du canevas, utilisez les propriétés `width` et `height` du moteur de rendu `renderer` de l'`Application`. Ces propriétés sont identiques aux propriétés `width` et `height` de la propriété `view` du moteur de rendu.

```js
// largeur du canevas
let canvasWidth = app.renderer.width; // ou app.renderer.view.width
// hauteur du canevas
let canvasHeight = app.renderer.height; // ou app.renderer.view.height
```

### Redimensionner le canevas

Pour redimensionner le canevas, attribuez la valeur `true` à la propriété `autoResize` du moteur de rendu `renderer` de l'`Application` puis appelez la méthode `resize` avec les nouvelles dimensions.

```javascript
// Autorise le redimensionnement du canevas
app.renderer.autoResize = true;
// Redimensionne le canevas
app.renderer.resize(1280, 720);
```

### Afficher l'application dans toute la fenêtre

Si vous souhaitez afficher votre application dans toute la fenêtre du navigateur, utilisez les propriétés `window.innerWidth` et `window.innerHeight` dans la configuration du moteur de rendu.

```js
// Crée un canevas de la taille de la fenêtre du navigateur
let app = new PIXI.Application({width: window.innerWidth, height: window.innerHeight});
``` 

### Définir des alias

Si vous utilisez souvent certaines méthodes, vous pouvez définir des alias et utilisez ceux-ci à la place de leur nom complètement qualifié.

```javascript
// Crée un alias Sprite
const Sprite = PIXI.Sprite;
```

## Ressources externes

- [Site officiel de *PixiJS*](https://www.pixijs.com/)
- [Documentation de l'API](http://pixijs.download/release/docs/index.html)
- [Getting started Wiki](https://github.com/pixijs/pixi.js/wiki/Getting-Started)
- [Forum officiel](https://www.html5gamedevs.com/forum/15-pixijs/)
- [Environnement de test en ligne](https://www.pixiplayground.com/)
- [Tutoriel de Kittykatattack](https://github.com/kittykatattack/learningPixi)
- [Vidéo de présentation de *PixiJS*](https://www.youtube.com/watch?v=GLbjF-ajG_I)
- [Série de vidéo youtube d'introduction à *PixiJS*](https://www.youtube.com/watch?v=eKsTVZKMeuI&list=PL08jItIqOb2oGcyrgREbrm_b9OW7TE1ji)
- [Video de GameFromScratch sur la sortie de *PixiJS* v5](https://www.youtube.com/watch?v=GKCFvcSyhP8)

## Lib supplémentaires pour *PixiJS*

- bump
- smoothie
- pixi-keyboard
- pixi-sound
- pixi-tiled
- pixi-particles



