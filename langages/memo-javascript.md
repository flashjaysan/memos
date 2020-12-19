# Mémo JavaScript dans un navigateur

*par flashjaysan*

## Conseils de pro

### Toujours utiliser le mode strict

Placez toujours l'instruction suivante en tête de vos scripts :

```js
'use strict';
```

Cette instruction demande à l'interpréteur JavaScript de contrôler certaines ?????????????????. Par exemple, l'interpréteur lance une erreur si une variable n'est pas déclarée. Elle protège de certaines erreurs difficiles à détecter.

### Utilisez `let` et `const` à la place de `var`

```js
let data = 'value';
const add = function(number1, number2) {
    return number1 + number2;
}
```

### Utilisez un linter

ESLint, JSLint, JSHint sont des outils de vérification de code selon certaines règles qui peuvent être configurées.

### Utilisez `===` plutôt que `==`



## Ressources supplémentaires

Le site suivant fournit un rapide résumé de la syntaxe JavaScript :

[https://developer.mozilla.org/fr/docs/Web/JavaScript/Une_r%C3%A9introduction_%C3%A0_JavaScript](https://developer.mozilla.org/fr/docs/Web/JavaScript/Une_r%C3%A9introduction_%C3%A0_JavaScript)

Pour une description détaillée du langage, consultez le site suivant :

[https://developer.mozilla.org/fr/docs/Web/JavaScript](https://developer.mozilla.org/fr/docs/Web/JavaScript)

## Types de base

### Nombres

Tous les nombres (y compris les entiers) sont représentés sour la forme de valeurs au format IEEE 754 en double précision 64 bits. 

On peut convertir une chaîne de caractères en un nombre entier à l'aide de la fonction intégrée `parseInt()`. Elle reçoit la base de conversion comme second paramètre, qui devrait toujours être fourni afin de lever une éventuelle ambiguïté :

```js
let number = parseInt("123", 10);
```

De la même manière, vous pouvez traiter les nombres à virgule flottante à l'aide de la fonction intégrée parseFloat(), qui, à la différence de parseInt(), utilise toujours la base 10.

On peut également utiliser l'opérateur unaire `+` pour convertir des valeurs en nombres :

```js
+ "42";   // 42
+ "010";  // 10
+ "0x10"; // 16
```

Une valeur spéciale appelée `NaN` (qui signifie « Not a Number », soit « pas un nombre ») est renvoyée si la chaîne est non numérique :

```js
parseInt("coucou", 10); // NaN
```

`NaN` est « toxique » : si cette valeur est fournie en entrée pour n'importe quelle opération mathématique, le résultat sera également `NaN` :

```js
NaN + 5; // NaN
```

Cette valeur peut être détectée grâce à la fonction native `isNaN()` :

```js
isNaN(NaN); // true
```

JavaScript dispose également de valeur spéciales pour l'infini `Infinity` et l'infini négatif (`-Infinity`) :

```js
1 / 0; // Infinity
-1 / 0; // -Infinity
```

Il est possible de tester les valeurs `Infinity`, `-Infinity` et `NaN` à l'aide de la fonction native `isFinite()` :

```js
isFinite(1/0); // false
isFinite(-Infinity); // false
isFinite(NaN); // false
```

La fonction `Number` convertit une chaine de caractères en nombre.

### Chaînes de caractères

Si vous voulez représenter un seul caractère, il suffit d'utiliser une chaîne qui contient un seul caractère.

Pour connaître la longueur d'une chaîne, utilisez sa propriété `length` :

```js
"bonjour".length; // 7
```

C'est notre première rencontre avec les objets JavaScript ! Les chaînes peuvent également être utilisées comme des objets. Elles possèdent aussi des méthodes permettant de manipuler la chaîne et d'accéder à certaines informations sur cette chaîne de caractères :

```js
"bonjour".charAt(0); // "b"
"coucou monde".replace("coucou", "bonjour"); // "bonjour monde"
"bonjour".toUpperCase(); // "BONJOUR"
```

### null et undefined

JavaScript fait la distinction entre `null`, qui est un objet de type object indiquant une absence délibérée de valeur, et `undefined` qui est un objet de type `undefined` indiquant une variable non initialisée — c'est-à-dire qui n'a pas encore été assignée. En JavaScript il est possible de déclarer une variable sans lui assigner de valeur. Si vous faites cela, le type de la variable sera `undefined` qui est une constante.

### Booléens

JavaScript dispose d'un type booléen, dont les valeurs possibles sont `true` (vrai) et `false` (faux). L'un et l'autre sont des mots clés. Toute valeur peut être convertie en une valeur booléenne selon les règles suivantes :

- `false`, `0`, la chaîne vide (`""`), `NaN`, `null` et `undefined` deviennent toutes `false`.
- Toutes les autres valeurs deviennent `true`.

Cette conversion peut être faite de manière explicite à l'aide de la fonction `Boolean()` :

```js
Boolean(""); // false
Boolean(234); // true
```

Cependant, c'est rarement nécessaire, puisque JavaScript effectuera cette conversion silencieusement chaque fois qu'il attend une valeur booléenne, comme par exemple dans une instruction `if`. Pour cette raison, on parle souvent simplement de valeurs « vraies » et « fausses » pour indiquer des valeurs devenant respectivement `true` et `false` lorsqu'elles sont converties en valeurs booléennes.

Les opérations booléennes comme `&&` (et logique), `||` (ou logique) et `!` (non logique) sont également gérées.

## Objets

Il existe deux façons très simples pour créer un objet vide :

```js
var obj = new Object();
```

Et :

```js
var obj = {};
```

Ces deux lignes sont sémantiquement équivalentes ; la seconde est appelée la syntaxe littérale d'objet, et est beaucoup plus pratique. Cette syntaxe n'existait pas dans les toutes premières versions du langage, c'est pourquoi on voit parfois du code utilisant l'ancienne méthode. Cette seconde syntaxe se rapproche également du format JSON.

## objets

On peut se servir du mot clé `this` pour améliorer un constructeur :

```js
function Personne(prenom, nom) {
  this.prenom = prenom;
  this.nom = nom;
}

Personne.prototype.nomComplet = function() {
  return this.prenom + ' ' + this.nom;
}

Personne.prototype.nomCompletInverse = function nomCompletInverse() {
  return this.nom + ' ' + this.prenom;
}

var s = new Personne("Simon", "Willison");
```

`new` est très lié à `this`. Il crée un nouvel objet vide et appelle ensuite la fonction spécifiée, avec `this` pointant vers ce nouvel objet. Les fonctions prévues pour être appelées par `new` sont appelées des constructeurs. L'usage courant est de mettre la première lettre de ces fonctions en majuscule pour se souvenir de les appeler avec `new`.




## JavaScript pour HTML

### Insérer du code JavaScript dans un document HTML

La balise `script` vous permet de placer du code JavaScript directement dans le document HTML.

```html
<!doctype html>
<html>
  <head>
    <title>Titre de la page</title>
    <script>
    // code JavaScript
    </script>
  </head>
  <body>
  </body>
</html>
```

Vous pouvez également faire référence à un fichier externe en utilisant l'attribut `src`.

```html
<!doctype html>
<html>
  <head>
    <title>Titre de la page</title>
    <script src="emplacement_fichier_javascript"></script>
  </head>
  <body>
  </body>
</html>
```

**Remarque :** Utilisez l'attribut `defer` pour indiquer que le script doit s'exécuter uniquement lorsqu'il est totalement chargé.

Un évènement peut être :

- "click" : l'utilisateur a cliqué sur l'élément.
- "dblclick" : l'utilisateur a double cliqué sur l'élément.
- "keydown" : l'utilisateur a appuyé sur une touche du clavier.
- "keyup" : l'utilisateur a relâché une touche du clavier.
- "keypress" : l'utilisateur appuie sur une touche du clavier.
- "mousedown" : l'utilisateur a cliqué avec le pointeur au dessus de l'élément.
- "mouseup" : l'utilisateur a relâché son clic avec le pointeur au dessus de l'élément.
- "mouseenter" : le pointeur de la souris entre dans la zone de l'élément.
- "mouseleave" : le pointeur de la souris sort de la zone de l'élément.
- "mousedown" : l'utilisateur a cliqué sur l'élément.


```javascript
let htmlElement = document.querySelector("idOfElement")
htmlElement.addEventListener(event, eventHandler, false)

window.addEventListener(event, eventHandler, false)

function eventHandler(event)
{
    if (event.keyCode == )
}
```
