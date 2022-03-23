# Mémo CSS

*par flashjaysan*

## Intégration à un document HTML

Directement dans un élément en utilisant l'attribut `style` :

```html
<element style="propriete: valeur">
```

Directement dans le document dans une balise `<style>` :

```html
<style>
selecteur {propriete: valeur;}
</style>
```

Depuis un fichier externe :

```html
<link rel="stylesheet" type="text/css" href="css/style.css">
```

On utilise généralement la troisième approche.

## Syntaxe de base

```css
selecteur {
    propriete: valeur;
}
```

ou

```css
selecteur:pseudoclasse {
    propriete: valeur;
}
```

- Le sélecteur correspond à l'élément à modifier dans le document HTML.
- La pseudoclasse d'un élément correspond à son état. (par exemple, si la souris survol ou clic sur l'élément)
- La propriété correspond à la propriété à modifier.
- La valeur correspond à la nouvelle valeur à attribuer à la propriété.

Placez vos commentaires entre `/*` et `*/`.

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

Pour définir des propriétés générales à tout le document, ciblez l'élément `body`.

```css
body {
    font-family: "Helvetica Neue", Arial;
    font-size: 18px;
}
```

Pour cibler tous les éléments, utilisez le sélecteur étoile `*`.

```css
* {}
```

**Attention !** Utiliser le sélecteur étoile affecte tous les éléments du document alors que cibler l'élément `body` transmet par héritage les propriétés qui sont héritées. Autrement dit, le sélecteur étoile attribue une propriété à tous les éléments même si ils ne la possèdent pas au départ. En général, on se sert du sélecteur étoile pour modifier le modèle en boite et on utilise l'élément `body` pour les propriétés générales telles que la couleur ou la police.

```css
* {
    box-sizing: border-box;
}

body {
    font-family: Roboto, Arial, Helvetica, sans-serif;
}
```

### Combinaisons de sélecteurs

Vous pouvez combiner un id, une classe et des éléments pour sélectionner des éléments particuliers.

```css
/* cible les éléments h1 contenus dans l'id nom_d_id */
#nom_d_id h1 {}
```

Le combinateur de frère adjacent attribue le style à l'élément définit par `selecteur2` quand ce dernier suit immdiatement un élément définit par `selecteur1`. Les éléments doivent avoir le même parent.

```css
selecteur1 + selecteur2 {}
```

Le combinateur de frère général attribue le style à l'élément définit par `selecteur2` quand ce dernier suit un élément définit par `selecteur1`. Les éléments doivent avoir le même parent mais peuvent avoir d'autre éléments situés entre eux.

```css
selecteur1 ~ selecteur2 {}
```

Le combinateur d'enfant attribue le style à l'élément définit par `selecteur2` quand ce dernier est un enfant direct de l'élément définit par `selecteur1`.

```css
selecteur1 > selecteur2 {}
```

Le combinateur de descendant attribue le style à l'élément définit par `selecteur2` quand ce dernier est un descendant (direct ou indirect) de l'élément définit par `selecteur1`.

```css
selecteur1 selecteur2 {}
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

## Image de fond

### Définir une image de fond

```css
selecteur {
    background-image: url(chemin);
}
```

### Assombrir une image de fond

```css
selecteur {
    background-image: 
        rgba(0, 0, 0, 0.7),
        url(chemin);
}
```

### Prendre l'intégralité de la fenêtre

```css
selecteur {
    background-image: url(chemin);
    background-size: cover; /* force l'image à se redimensionner pour prendre toute la place disponible */
    background-position: center;
    height: 100vh; /* force l'élément à prendre toute la haute de la fenêtre */
}
```

### Définir des réglages globaux

```css
html {
    font_size: 20px;
}
```

### définir des réglages relatifs

```css
h1 {
    font_size: 200%;
}
```

## modifier un texte en majuscules

```css
selecteur {
    text-transform: uppercase;
}
```

```css

```

```css

```