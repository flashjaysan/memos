# Mémo CSS

*par flashjaysan*

## Intégration à un document HTML

- Directement dans un élément :

```html
<element style="propriete=valeur">
```

- Directement dans le document :

```html
<style>
selecteur {propriete: valeur;}
</style>
```

- Depuis un fichier externe :

```html
<link rel="stylesheet" type="text/css" href="css/style.css">
```

## Syntaxe de base

```css
selecteur {propriete: valeur;}
```

ou

```css
selecteur:pseudoclasse {propriete: valeur;}
```

- Le sélecteur correspond à l'élément à modifier dans le document HTML.
- La pseudoclasse d'un élément correspond à son état. (par exemple, si la souris survol ou clic sur l'élément)
- La propriété correspond à la propriété à modifier.
- La valeur correspond à la nouvelle valeur à attribuer à la propriété.

```css
/* ceci est un commentaire */
```

Pour cibler des éléments possédant une classe spécifique, utilisez un point `.` suivi du nom de la classe.

```css
.nom_de_classe {}
```

Pour cibler des éléments possédant un id spécifique, utilisez un caractère dièse `#` suivi du nom de la classe.

```css
#nom_d_id {}
```

Pour cibler plusieurs éléments, séparez-les par une virgule.

```css
h1, h2 {}
```

**Remarque :** Pour définir des propriétés générales à tout le document, ciblez l'élément `body`.

```css
body {
    font-family: "Helvetica Neue", Arial;
    font-size: 18px;
}
```

### Définir la couleur d'un élément

Définissez la valeur de la propriété `color` avec un [nom de couleur prédéfini](https://html-color-codes.info/color-names/), un nombre hexadécimal précédé du caractère dièse `#`, utilisez la fonction `rgb`, la fonction `hsl` ou le mot clé `currentcolor`.

```css
h1 {
    color: red;
}

h2 {
    color: #FF0000;
}

h3 {
    color: rgb(255, 0, 0);
}

h4 {
    color: hsl(0, 100%, 50%);
}

h5 {
    color: currentcolor;
}
```

**Remarque :** Pour contrôler l'opacité d'un objet, utilisez la fonction `rgba` ou `hsla`.

```css
h1 {
    color: rgba(255, 0, 0, 0.5);
}

h2 {
    color: hsla(0, 100%, 50%, 0.25);
}
```

### Définir la taille de police

Utilisez la propriété `font-size`.

```css
h1 {
    font-size: 40px;
}
```

### Définir la police

Utilisez la propriété `font-family`.

```css
h1 {
    font-family: "Helvetica Neue", Arial;
}
```

### Définir l'alignement de police

Utilisez la propriété `text-align` avec l'une des valeurs `left`, `right`, `center` ou `justify`.

```css
h1 {
    text-align: left;
}
```

### Le modèle en boite

![modele en boite](box_model.png)

Chaque élément peut être considéré comme une boite constituée :

- d'un contenu avec une dimension précise.
- d'une marge interne (*padding*) définissant l'espace entre le contenu et la bordure.
- d'une bordure.
- d'une marge externe (*margin*) définissant l'espace entre la bordure et les autres éléments.

Il existe deux types d'éléments.

- Les éléments en bloc (de type `block`) utilisent le modèle en boite. Ils prennent la totalité de la largeur du document et forcent un retour à la ligne après leur affichage.
- Les éléments en ligne (de type `inline`) n'ont pas ces particularités.

Un élément peut définir ses dimensions par rapport à son contenu (auquel cas les marges et la bordure débordent des dimensions) ou sur sa boite (auquel cas les marges et la bordure ne déborderont jamais et c'est le contenu qui sera ajusté). Utilisez la propriété `box-sizing` avec la valeur `content-box` (par défaut) ou la valeur `border-box`.

```css
h1 {
    box-sizing: border-box;
}
```

#### Définir la marge interne

Utilisez les propriétés `padding-top`, `padding-right`, `padding-bottom` et `padding-left` ou directement la propriété `padding`.

```css
body {
    padding: 0;
}

h1 {
    padding-top: 5px;
    padding-right: 10px;
    padding-bottom: 15px;
    padding-left: 20px;
}

h2 {
    padding: 5px 10px 15px 20px; /* top right bottom left */
}

h3 {
    padding: 10px 20px; /* top et bottom 10px left et right 20px */
}
```

#### Définir la bordure


```css

```

#### Définir la marge externe

Utilisez les propriétés `margin-top`, `margin-right`, `margin-bottom` et `margin-left` ou directement la propriété `margin`.

```css
body {
    margin: 0;
}

h1 {
    margin-top: 5px;
    margin-right: 10px;
    margin-bottom: 15px;
    margin-left: 20px;
}

h2 {
    margin: 5px 10px 15px 20px; /* top right bottom left */
}

h3 {
    margin: 10px 20px; /* top et bottom 10px left et right 20px */
}
```

#### Supprimer les marges par défaut

Utilisez le sélecteur étoile `*` pour cibler tous les éléments.

```css
* {
    margin: 0;
    padding: 0;
}
```

```css

```

```css

```

```css

```

```css

```

```css

```