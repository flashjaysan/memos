# Mémo HTML

*par flashjaysan*

## Balises

Un document HTML est essentiellement un fichier texte composé d'une arborescence de **balises** HTML. La plupart des balises contiennent un contenu. Pour délimiter ce contenu, on place une balise d'ouverture (`<nom_de_balise>`) avant le contenu et une balise de fermeture (`</nom_de_balise>`) après le contenu.

```html
<balise>contenu</balise>
```

Une balise et son contenu constitue **un élément**.

Certaines balises ne contiennent pas de contenu. La balise de fermeture est donc inutile dans ce cas.

```html
<balise_sans_contenu>
```

### Propriétés

Une balise peut également spécifier des valeurs pour ses **propriétés**.

```html
<balise propriété="valeur">contenu</balise>
```

**Remarque :** La valeur d'une propriété est toujours écrite entre guillemets.

Chaque type de balise définit une liste de propriétés prédéfinies.

### Créer une nouvelle propriété

Vous aurez parfois besoin de créer de nouvelles propriétés sur une balise. Vous devez faire précéder vos nouvelles propriétés par le préfixe `data-`.

```html
<balise data-nouvelle-propriete="valeur">contenu</balise>
```

**Remarque :** Pour accéder à ces propriétés en JavaScript, utilisez la propriété `dataset` de l'élément suivi d'un point `.` et du nom de la nouvelle propriété sans la partie `data-`. Supprimez les tirets et remplacez le nom de la propriété par sa version camelCase.

```js
const elements = document.getElementsByName('balise');
Console.log(elements[0].dataset.nouvellePropriete);
```

## Commentaires

```html
<!-- commentaire -->
```

## Doctype

La balise `doctype` doit être placée au tout début du document. Elle ne possède pas de balise de fermeture.

```html
<!doctype html>
```

ou

```html
<!DOCTYPE html>
```

## HTML

La balise `html` se place à la racine du document après la balise `doctype`.

```html
<!doctype html>
<html>
</html>
```

## Tête du document

La balise `head` se place dans la balise `html`. L'élément `head` contient des informations sur la page elle-même et ces informations ne sont pas affichées dans le navigateur.

```html
<!doctype html>
<html>
  <head>
  </head>
</html>
```

## Titre

La balise `title` se place dans la balise `head`. L'élément `title` définit le titre de la page qui apparaît dans l'onglet ou dans l'en-tête de fenêtre du navigateur. Il est également utilisé comme texte de marque page de la page.

```html
<!doctype html>
<html>
  <head>
    <title>Titre du document</title>
  </head>
</html>
```

## Corps du document

La balise `body` se place dans la balise `html`. L'élément `body` contient tout le contenu que doit afficher la page.

```html
<!doctype html>
<html>
  <head>
    <title>Titre du document</title>
  </head>

  <body>
  </body>
</html>
```

## Divisions

La balise `div` vous permet de découper le contenu du document. Utilisez cette balise lorsque vous souhaitez grouper un ensemble de balises dans un même bloc.

```html
<!doctype html>
<html>
  <head>
    <title>Titre du document</title>
  </head>

  <body>
    <div></div>
    <div></div>
  </body>
</html>
```

## Sous sections

La balise `body` peut être subdivisée en quatre sous sections `header`, `nav`, `main` et `footer`.

```html
<!doctype html>
<html>
  <head>
    <title>Titre du document</title>
  </head>

  <body>
    <header></header>
    <nav></nav>
    <main></main>
    <footer></footer>
  </body>
</html>
```

Ces balises ont les mêmes fonctionnalités que la balise `div` mais définissent sémantiquement des zones fréquemment utilisées dans les documents.

- La balise `header` définit le bandeau d'en-tête d'un document.
- La balise `nav` définit la zone de navigation d'un document.
- La balise `main` définit le contenu principal d'un document.
- La balise `footer` définit le bandeau de bas de page d'un document.

## span

```html
<!doctype html>
<html>
  <head>
    <title>Titre du document</title>
  </head>

  <body>
    <p>Paragraphe.</p>
    <p><span>Paragraphe.</span></p>
  </body>
</html>
```

## Paragraphes

L'élément `p` définit un paragraphe de texte.

```html
<!doctype html>
<html>
  <head>
    <title>Titre du document</title>
  </head>

  <body>
    <p>Paragraphe.</p>
  </body>
</html>
```

## Emphase de texte

Les balises `em` et `strong` définissent un bloc de texte plus important que d'ordinaire.

```html
<!doctype html>
<html>
  <head>
    <title>Titre du document</title>
  </head>

  <body>
    <p>Cette phrase est ordinaire.
    <em>Cette phrase est importante.</em>
    <strong>Cette phrase est encore plus importante.</strong></p>
  </body>
</html>
```

## Retour à la ligne

La balise `br` se place dans la balise `p`. Elle n'a pas de balise fermante.

```html
<!doctype html>
<html>
  <head>
    <title>Titre du document</title>
  </head>

  <body>
    <p>Ligne 1.<br>Ligne 2.</p>
  </body>
</html>
```

## Ligne horizontale

Utilisez la balise `hr` pour insérer une ligne horizontale et séparer deux blocs de contenu.

```html
<!doctype html>
<html>
  <head>
    <title>Titre du document</title>
  </head>

  <body>
    <p>Paragraphe.</p>
    <hr>
    <p>Paragraphe.</p>
  </body>
</html>
```

## Titres

Les balises `h1`, `h2`, `h3`, `h4`, `h5` et `h6` définissent des titres par ordre d'importance. `h1` est le titre le plus important et `h6` le titre le moins important. Utilisez ces balises autant que possible dans l'ordre.

```html
<!doctype html>
<html>
  <head>
    <title>Titre du document</title>
  </head>

  <body>
    <h1>Titre importance 1</h1>
    <h2>Titre importance 2</h2>
    <h3>Titre importance 3</h3>
    <h3>Titre importance 4</h4>
    <h4>Titre importance 5</h5>
    <h5>Titre importance 6</h6>
  </body>
</html>
```

## Listes

- La balise `ol` définit une liste ordonnée (numérotée).
- La balise `ul` définit une liste non ordonnée.
- La balise `li` définit un élément de liste.

```html
<!doctype html>
<html>
  <head>
    <title>Titre du document</title>
  </head>

  <body>
    <ol>
      <li>Element 1.</li>
      <li>Element 2.</li>
      <li>Element 3.</li>
    </ol>

    <ul>
      <li>Element.</li>
      <li>Element.</li>
      <li>Element.</li>
    </ul>
  </body>
</html>
```

## Liens

La balise `a` définit un lien. Utilisez la propriété `href` pour définir l'adresse du lien. L'adresse peut être absolue ou relative au document en cours.

```html
<!doctype html>
<html>
  <head>
    <title>Titre du document</title>
  </head>

  <body>
    <p>Ceci est un <a href="https://site.fr/">lien</a>.</p>
  </body>
</html>
```

Utilisez un lien vers un id du document en cours précédé du signe dièse `#` pour créer un lien interne à la page.

```html
<!doctype html>
<html>
  <head>
    <title>Titre du document</title>
  </head>

  <body>
    <p>Ceci est un <a href="#fin">lien interne</a>.</p>
    <p id="fin">Fin du document.</p>
  </body>
</html>
```

La propriété `target` vous permet de définir si le lien doit s'ouvrir à la place du document actuel (par défaut) ou dans une nouvelle fenêtre (`"_blank"`).

```html
<!doctype html>
<html>
  <head>
    <title>Titre du document</title>
  </head>

  <body>
    <p>Ceci est un <a href="https://site.fr/" target="_blank">lien</a>.</p>
  </body>
</html>
```

### Lien vers une adresse email

Faites simplement précéder l'adresse email par `mailto:`.

```html
<!doctype html>
<html>
  <head>
    <title>Titre du document</title>
  </head>

  <body>
    <p>Ceci est un <a href="mailto:nom@domaine.com">lien vers une adresse email</a>.</p>
  </body>
</html>
```

## Id

Utilisez la propriété `id`. Un id ne peut être attribué qu'une seule fois dans un document HTML.

```html
<balise id="id_unique"></balise>
```

## Classes

Utilisez la propriété `class`. Une classe peut être attribuée à plusieurs éléments dans un document HTML.

```html
<balise_1 class="nom_de_classe"></balise_1>
<balise_2 class="nom_de_classe"></balise_2>
```

Un élément peut avoir plusieurs classes séparées par un espace.

```html
<balise class="nom_de_classe1 nom_de_classe2"></balise>
```

## Images

La balise `img` définit une image et elle n'a pas de balise fermante. Utilisez la propriété `src` pour définir l'adresse (absolue ou relative) de l'image, la propriété `width` pour définir la largeur de l'image, la propriété `height` pour définir la hauteur de l'image et la propriété `alt` pour définir un texte alternatif si l'image ne peut être affichée (pour l'accessibilité).

```html
<!doctype html>
<html>
  <head>
    <title>Titre du document</title>
  </head>

  <body>
    <img src="image.png" width="120" height="90" alt="Texte alternatif">
  </body>
</html>
```

**Remarque :** La plupart des navigateurs prennent en charge les formats d'image `PNG`, `JPEG` et `GIF`.

## Tableaux

La balise `table` définit un tableau. La balise `tr` définit une ligne et se place dans l'élément `table`. La balise `td` définit une cellule d'une ligne du tableau et se place dans l'élément `tr`.

```html
<!doctype html>
<html>
  <head>
    <title>Titre du document</title>
  </head>

  <body>
    <table>
      <tr>
        <td>Ligne 1, Colonne 1</td>
        <td>Ligne 1, Colonne 2</td>
        <td>Ligne 1, Colonne 3</td>
      </tr>

      <tr>
        <td>Ligne 2, Colonne 1</td>
        <td>Ligne 2, Colonne 2</td>
        <td>Ligne 2, Colonne 3</td>
      </tr>
    </table>
  </body>
</html>
```

## Citations

```html
<blockquote cite="url">Texte à afficher.</blockquote>
```

## Formulaires



## Balises de type inline et de type block-level

En HTML, il y a deux types de balises :

- Les balises de type *inline* affichent leur contenu dans un minimum d'espace et le contenu des balises suivantes est affiché à la suite sur la même ligne.
- Les balises de type *block-level* affichent leur contenu sur toute la largeur de la page. Le contenu des balises suivantes est affiché au dessous du contenu précédent.

Vous pouvez modifier le type de chaque élément grâce aux CSS.

## Clavier

La balise `kbd` permet de définir un texte correspondant à une saisie clavier. Le navigateur présente alors le texte comme un raccourci clavier dans une police monospace.

```html
<kbd>CTRL+N</kbd>
```

### Evènements

Utilisez le type d'évènement `keydown` pour exécuter une fonction lorsque l'utilisateur appuie sur une touche du clavier.

```js
window.addEventListener('keydown', keyDownListener);

function keyDownListener(eventInfo) {
  // gestion de l'évènement
}
```

Lorsque l'utilisateur appuie sur une touche du clavier, la fonction `keyDownListener` est appelée avec un objet `eventInfo` contenant les informations relatives à l'évènement.

Utilisez la propriété `keyCode` de l'objet `eventInfo` pour connaître le code numérique associé à la touche.

**Remarque :** Le site `http://keycode.info/` vous permet de connaître le code numérique associé à une touche de votre clavier.



