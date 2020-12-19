# Mémo HTML canvas

*par flashjaysan*

## Etapes de base

- Créez un fichier HTML.
- Insérer le squelette suivant :

```html
<!doctype html>
<html>
    <head>
        <meta charset="utf-8">
        <meta name="description" content="description pour les moteurs de recherche">
        <meta name="author" content="votre nom">
        <title>Titre</title>
    </head>
    <body>
        <canvas id="game" width="largeur" height="hauteur">Votre navigateur ne prend pas en charge la balise canvas.</canvas>
        <script>main.js</script>
    </body>
</html>
```

**Remarque :** Si vous ne spécifiez pas les dimensions du canvas, elles sont par défaut de 300x150.

- Créez un fichier JavaScript (ici `main.js`).
- Insérer le squelette suivant :

```js
'use strict';
```

## L'élément canvas

### Propriétés

- `width` : définit la largeur en pixels du canvas. La valeur doit être un entier positif.
- `height` : définit la hauteur en pixels du canvas. La valeur doit être un entier positif.

Par défaut, le navigateur définit les dimensions de la surface de dessin du canevas sur les dimensions du canevas. Si un CSS modifie les dimensions du canevas, la surface de dessin n'est pas modifiée et est étirée sur les nouvelles dimensions du canevas.

### Méthodes

- `getContext` : Appelée avec l'argument `'2d'`, renvoie l'objet `CanvasRenderingContext2D` associé au canevas. Dans un environnement prenant en charge WebGL, appelée avec l'argument `'webgl'`, renvoie l'objet `WebGLRenderingContext` associé au canevas.
- `` : .
- `` : .

## Exécuter un script lorsque la page est entièrement chargée

```js
window.onload = function() {
    // Instructions
}
```

ou

```js
window.onload = init();


function init() {
    // Instructions
}
```

## Récupérer l'élément canevas dans le script

```js
let canvas = document.getElementById('game');
```

## Modifier la taille du canevas

```js
canvas.width = largeur;
canvas.height = hauteur;
```

## Donner au canevas la taille de la fenêtre

```js
canvas.width = window.innerWidth;
canvas.height = window.innerHeight;
```

## Supprimer la marge auomatique de la fenêtre

- Ajoutez le code suivant au fichier HTML dans la balise `head` :

```html
<link rel="stylesheet" href="styles.css">
```

- Créez un fichier CSS (ici, `styles.css`).
- Ajoutez la règle suivante :

```css
body {
    margin: 0;
}
```

**Attention !** Bien que vous puissiez modifier la taille du canevas dans un CSS, cela modifie la taille du canevas mais pas celui de la surface de dessin associée. Cette dernière est étirée automatiquement sur la taille du canevas lorsque les dimensions ne sont pas identiques. Il est donc préférable d'utiliser les propriétés `width` et `height` du canevas directement dans le document HTML plutôt que dans un CSS.

## Récupérer le contexte du canevas dans le script

A partir de l'élément `canvas`, vous devez obtenir un objet particulier appelé `context` (de type [`CanvasRenderingContext2D`](https://developer.mozilla.org/fr/docs/Web/API/CanvasRenderingContext2D)) qui vous permettra de dessiner dans le canevas.

```js
let context = canvas.getContext('2d');
```

Exemple :

```js
'use strict';
let canvas;
let context;

window.onload = init;

function init(){
    // Get a reference to the canvas
    canvas = document.getElementById('canvas');
    context = canvas.getContext('2d');
}
```

## Sauvegarder l'état du contexte et le restaurer

```js
context.save();
// modifications et utilisation du contexte
context.restore();
```

**Remarque :** La sauvegarde s'effectue sur une pile. Vous pouvez donc sauvegarder ou restaurer plusieurs états successivement.

## Définir la couleur de contour

```js
context.strokeStyle = couleur;
```

La `couleur` peut être une chaîne correspondant à une [couleur prédéfinie](https://htmlcolorcodes.com/fr/noms-de-couleur/) ou un nombre hexadécimal correspondant à une couleur RGB et précédé du signe `#`. Une fois définie, la couleur de contour reste la même jusqu'à la définition d'une nouvelle couleur.

## Définir la couleur de remplissage

```js
context.fillStyle = couleur;
```

La `couleur` peut être une chaîne correspondant à une [couleur prédéfinie](https://htmlcolorcodes.com/fr/noms-de-couleur/) ou un nombre hexadécimal correspondant à une couleur RGB et précédé du signe `#`. Une fois définie, la couleur de remplissage reste la même jusqu'à la définition d'une nouvelle couleur.

## Définir l'épaisseur de ligne des contours

```js
context.lineWidth = epaisseur;
```

## dessiner un rectangle de couleur pleine

```js
context.fillRect(coin_supérieur_gauche_x, coin_supérieur_gauche_y, largeur, hauteur);
```

## dessiner un contour de rectangle de couleur

```js
context.strokeRect(coin_supérieur_gauche_x, coin_supérieur_gauche_y, largeur, hauteur);
```

## Remplir le canevas avec un rectangle de couleur

```js
context.fillRect(0, 0, canvas.width, canvas.height);
```

## Effacer le canevas

```js
context.clearRect(0, 0, canvas.width, canvas.height);
```

## Dessiner un cercle de couleur pleine

```js
context.beginPath();
context.arc(centre_x, centre_y, rayon, 0, 2 * Math.PI);
context.fill();
```

## Dessiner un contour de cercle de couleur

```js
context.beginPath();
context.arc(centre_x, centre_y, rayon, 0, 2 * Math.PI);
context.stroke();
```

## Dessiner une ligne droite entre deux points

```js
context.beginPath();
context.moveTo(point_depart_x, point_depart_y);
context.lineTo(point_arrivee_x, point_arrivee_y);
context.stroke();
```

## Dessiner un triangle de couleur pleine

```js
context.beginPath();
context.moveTo(premier_point_x, premier_point_y);
context.lineTo(deuxieme_point_x, deuxieme_point_y);
context.lineTo(troisieme_point_x, troisieme_point_y);
context.fill();
```

## Dessiner un contour de triangle

```js
context.beginPath();
context.moveTo(premier_point_x, premier_point_y);
context.lineTo(deuxieme_point_x, deuxieme_point_y);
context.lineTo(troisieme_point_x, troisieme_point_y);
context.closePath();
context.stroke();
```

**Remarque :** La méthode `fill` ferme le chemin défini automatiquement mais pas la méthode `stroke` c'est pourquoi vous devez explicitement appeler la méthode `closePath` avant de tracer le contour d'une forme fermée.

## Dessiner à la fois le contour et remplir la forme

Après avoir terminé la définition du chemin, appelez les méthodes `fill` et `stroke` à la suite.

```js
context.beginPath();
context.moveTo(premier_point_x, premier_point_y);
context.lineTo(deuxieme_point_x, deuxieme_point_y);
context.lineTo(troisieme_point_x, troisieme_point_y);
context.fill();
context.stroke();
```

## Dessiner du texte

```js
context.font = '25px Arial';
context.textAlign = 'right';
context.textBaseline = 'bottom';
context.fillText('Texte à afficher.', position_x, position_y);
```

## Dessiner une image

```js
let image = new Image();
image.src = 'assets/image.png';
context.drawImage(image, coin_supérieur_gauche_x, coin_supérieur_gauche_y);
```

**Attention !** Une image ne s'affichera pas si elle n'est pas entièrement chargée. Utilisez l'événement `onload` pour vérifier si l'image est chargée.

```js
image.onload = function() {
   context.drawImage(image, coin_supérieur_gauche_x, coin_supérieur_gauche_y);
};
```

Si vous n'utilisez qu'un seul atlas contenant toutes les images, vous pouvez utiliser `onload` pour lancer l'exécution de la boucle de jeu.

```js
atlas.onload = gameLoop;
```

## Dessiner une image qui se répète

La technique est un peu particulière car vous devez créer un motif avec la méthode `createPattern` à partir d'une image.

```js
const type = 'repeat';
const motif = context.createPattern(image, type);
```

Vous pouvez utiliser les options suivantes pour le type :

- `'repeat'` répète l'image horizontalement et verticalement.
- `'repeat-x'` répète l'image uniquement horizontalement.
- `'repeat-y'` répète l'image uniquement verticalement.
- `'no-repeat'` ne répète pas l'image.

Affectez ensuite ce motif au style de remplissage.

```js
context.fillStyle = motif;
```

Il ne vous reste plus qu'à dessiner des formes.

```js
context.fillRect(x, y, largeur, hauteur);
```

## Modifier l'échelle d'une image

```js
context.drawImage(image, coin_supérieur_gauche_x, coin_supérieur_gauche_y, largeur, hauteur);
```

**Remarque :** Vous pouvez utiliser les propriétés `width` et `height` de l'image et les diviser par un facteur d'échelle.

```js
context.drawImage(image, coin_supérieur_gauche_x, coin_supérieur_gauche_y, image.width / ratio_horizontal, image.width / ratio_vertical);
```

## Dessiner une partie d'image

```js
context.drawImage(
    image, 
    position_x_sous_image, 
    position_y_sous_image, 
    largeur_sous_image, 
    hauteur_sous_image, 
    position_x, 
    position_y, 
    largeur, 
    hauteur);
```

## Appliquer une rotation

```js
context.translate(position_x + decalage_origine_x, position_y + decalage_origine_y);
context.rotate(angle);
context.translate(-(position_x + decalage_origine_x), -(position_y + decalage_origine_y));

context.drawImage(image, x, y);

context.setTransform(1, 0, 0, 1, 0, 0); // réinitialise la matrice de transformation
```

**Remarque :** Vous pouvez également utiliser les méthodes `save` et `restore` pour sauvegarder l'état précédent de la matrice de transformation puis la rétablir une fois vos manipulations terminées mais réinitialiser la matrice est plus efficace car il n'y a pas de sauvegarde d'état.

```js
context.save();

context.translate(position_x + decalage_origine_x, position_y + decalage_origine_y);
context.rotate(angle);
context.translate(-(position_x + decalage_origine_x), -(position_y + decalage_origine_y));

context.drawImage(image, x, y);

context.restore();
```

## Lisser les images

```js
context.imageSmoothingEnabled = true; // par défaut, déjà true
context.imageSmoothingQuality = 'high';
```

Pour un jeu pixel art, désactivez le lissage en passant la propriété `imageSmoothingEnabled` à `false`.

## Répéter l'appel à une fonction selon un intervalle de temps

```js
const FPS = 60;
let timer = setInterval(gameLoop, 1000 / FPS);
```

Appelez la fonction `clearInterval` pour stopper la répétition.

```js
clearInterval(timer);
```

## Répéter l'appel à une fonction selon la vitesse de rafraichissement du navigateur

```js
window.requestAnimationFrame(gameLoop); // ou plus simplement gameLoop()

function gameLoop() {
    update();
    draw();
    window.requestAnimationFrame(gameLoop);
}
```

## Exemple complet

```js
let canvas;
let context;


window.onload = function() {
    canvas = document.getElementById('game');
    context = canvas.getContext('2d');
    const FPS = 60;
    setup();
    setInterval(gameLoop, 1000 / FPS);
}


function setup() {
    // Initialisation des éléments du jeu
}


function gameLoop() {
    update();
    draw();
}


function update() {
    // Mise à jour des éléments du jeu
}


function draw() {
    // Affichage des éléments du jeu
}
```

ou

```js
let canvas;
let context;
let deltaTime;
let previousTimeStamp;
let fps;


window.onload = function() {
    canvas = document.getElementById('game');
    context = canvas.getContext('2d');
    setup();
    window.requestAnimationFrame(gameLoop);
}


function setup() {
    deltaTime = 0;
    previousTimeStamp = performance.now();
    fps = 1;
    // Initialisation des éléments du jeu
}


function gameLoop(timeStamp) {
    privateUpdate(timeStamp);
    update();
    clearCanvas();
    draw();
    window.requestAnimationFrame(gameLoop);
}


function privateUpdate(timeStamp) {
    deltaTime = (timeStamp - previousTimeStamp) / 1000;
    deltaTime = Math.min(secondsPassed, 0.1); // limite le délai entre deux frames à 1/10e de secondes max
    fps = Math.round(1 / deltaTime);
    previousTimeStamp = timeStamp;
}


function clearCanvas() {
    context.clearRect(0, 0, canvas.width, canvas.height);
}


function update() {
    // Mise à jour des éléments du jeu
}


function draw() {
    // Affichage des éléments du jeu
}
```








## Liens utiles

- Le [tutoriel de Spicy Yoghurt](https://spicyyoghurt.com/tutorials/html5-javascript-game-development/develop-a-html5-javascript-game) m'a bien aidé à écrire ce document.








