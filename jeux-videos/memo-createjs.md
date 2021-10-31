# Mémo CreateJS

*par flashjaysan*

## Introduction

[VIDE]

## Préparatifs

Créez un fichier HTML de base.

```html
<html>
  <head>
  </head>
  <body>
  </body>
</html>
```

Dans la balise `head`, ajoutez une référence à la bibliothèque createJS.

```html
<html>
  <head>
    <script src="https://code.createjs.com/1.0.0/createjs.min.js"></script>
  </head>
  <body>
  </body>
</html>
```

**Remarque :** Vous pouvez également télécharger le fichier minifié de la bibliothèque et l'inclure localement avec votre fichier HTML.

```html
<html>
  <head>
    <script type="text/javascript" src="libs/createjs.min.js"></script>
  </head>
  <body>
  </body>
</html>
```

Ajoutez une balise `canvas` dans la balise `body`. Attribuez des dimensions à votre canevas et un attribut `id` qui sera utilisé par CreateJS pour faire référence à ce canevas.

```html
<html>
  <head>
    <script src="https://code.createjs.com/1.0.0/createjs.min.js"></script>
  </head>
  <body>
    <canvas id="canvas" width="640" height="360"></canvas>
  </body>
</html>
```

Dans la balise `head`, ajoutez une référence à un fichier source JavaScript local. Ce sera votre programme.

```html
<html>
  <head>
    <script src="https://code.createjs.com/1.0.0/createjs.min.js"></script>
    <script type="text/javascript" src="game.js"></script>
  </head>
  <body>
    <canvas id="canvas" width="640" height="360"></canvas>
  </body>
</html>
```

Créez un fichier JavaScript et insérez la définition de fonction `init`.

```js
function init() {

}
```

Dans le fichier HTML, associez l'appel à la fonction `init` à la propriété `onload` de la balise `head`.

```html
<html>
  <head>
    <script src="https://code.createjs.com/1.0.0/createjs.min.js"></script>
    <script type="text/javascript" src="game.js"></script>
  </head>
  <body onload="init();">
    <canvas id="canvas" width="640" height="360"></canvas>
  </body>
</html>
```

Dans le fichier JavaScript, dans la fonction `init`, créez une instance de la classe [`Stage`](https://www.createjs.com/docs/easeljs/classes/Stage.html). A la fin de la fonction, appelez la méthode `update`.

```js
function init() {
    const stage = new createjs.Stage("canvas");

    stage.update();
}
```

Vous pouvez maintenant coder votre jeu dans le fichier JavaScript.

## Principe de base

Une fois une instance de la classe `Stage` créée, vous pouvez créer des instances de diverses entités et vous devez ensuite les ajouter à la scène via la méthode `addChild`.

```js
function init() {
    const stage = new createjs.Stage("canvas");
    const circle = new createjs.Shape();
    circle.graphics.beginFill("DeepSkyBlue").drawCircle(0, 0, 50);
    circle.x = 100;
    circle.y = 100;
    stage.addChild(circle);
    stage.update();
}
```

## Formes vectorielles

CreateJS fournit des formes vectorielles via la classe [`Shape`](https://www.createjs.com/docs/easeljs/classes/Shape.html). Commencez par créer une instance de cette classe.

```js
const shape = new createjs.Shape();
```

Ajoutez cette nouvelle instance à la scène.

```js
stage.addChild(shape);
```

Les propriétés `x` et `y` définissent la position de l'instance dans la scène.

```js
shape.x = 160;
shape.y = 180;
```

La propriété `rotation` définit l'angle (en degrés) de l'instance dans la scène.

```js
shape.rotation = 45;
```



## Images

CreateJS prend en charge les images via la classe [`Bitmap`](https://www.createjs.com/docs/easeljs/classes/Bitmap.html). Commencez par créer une instance de cette classe.

```js
 const image = new createjs.Bitmap("image.png");
 ```

Ajoutez cette nouvelle instance à la scène.

```js
stage.addChild(image);
```

Les propriétés `x` et `y` définissent la position de l'instance dans la scène.

```js
image.x = 160;
image.y = 180;
```

La propriété `rotation` définit l'angle (en degrés) de l'instance dans la scène.

```js
image.rotation = 45;
```


