# Mémo Godot

par *flashjaysan*

## Introduction

Gratuit, libre et open source. 2D et 3D.

## 

out est un noeud (*node*). Un `Node` a un nom, des propriétés, des fonctions. Un `Node` est extensible.

Les `Node` sont arrangés dans une arborescence appelée une `Scène`. Un `Node` a un seul parent et peut avoir autant d'enfants que vous le souhaitez.

## Projet

### Créer un projet

Vous devez définir un emplacement vide sur votre ordinateur.

### Paramètres du projet

Cliquez sur le menu `Projet -> Paramètres du projet...`.

### Résolution du projet

Dans l'onglet `Général`, la section `Display -> Window` vous permet d'éditer les champs `Width` (largeur) et `Height` (hauteur) pour définir la résolution du projet. 

## Créer une scène

Dans le panneau `Scène`, cliquez sur le bouton `+`.

## Script

### Attacher un script à un Node

Sélectionnez un noeud pour afficher ses propriétés dans le panneau `Inspecteur`. Dans la section `Node -> Script`, sélectionnez l'option `Nouveau script`. Vous pouvez également faire un clic droit sur le noeud dans le panneau `Scène` et choisir l'option `Attacher un script`.

Définissez les propriétés du script puis validez.

Un script hérite du `Node` auquel il est attaché. Vous pouvez donc utiliser toutes les propriétés et méthodes de ce `Node`.

### Squelette de base d'un script

- La méthode `_ready` est appelée quand le noeud entre dans la scène en cours. Toutes les variables définies avant cette méthode et étant précédées du mot clé `onready` sont chargées avant l'exécution de cette fonction.
- La méthode `_init` est le constructeur du noeud. Le plus souvent, vous ne l'utiliserez pas.
- La méthode `_process` est appelée avant chaque affichage d'une image de jeu. Elle s'exécute si elle est définie par le programmeur. Elle reçoit un paramètre nommé `delta` correspondant au temps passé depuis le dernier appel de cette fonction. Ce temps peut varier.
- La méthode `_physics_process`, contrairement à la méthode `_process`, est appelée à intervalle fixe (par défaut avant chaque affichage d'une image de jeu mais cela peut être configuré différemment). Elle s'exécute si elle est définie par le programmeur. Elle reçoit un paramètre nommé `delta` correspondant au temps passé depuis le dernier appel de cette fonction. Cette fonction est préférable à la précédente dès que vous voulez utiliser le moteur physique et les collisions dans votre jeu.

## Node



## CanvasItem

La méthode [`get_viewport_rect`](https://docs.godotengine.org/en/stable/classes/class_canvasitem.html#class-canvasitem-method-get-viewport-rect) vous permet d'obtenir le rectangle (de type `Rect2`) correspondant au viewport.

## Node2D

La propriété `position` (de type `Vector2`) vous permet d'accéder à la position du `Node2D`.

**Déprécié :** La méthode `get_position` renvoie la position du Node2D relative à l'origine de son parent.

La méthode `get_global_position` renvoie la position globale du `Node2D`.

## Sprite

La propriété `texture` (de type `Texture`) vous permet d'accéder à la texture associée au sprite.

## Obtenir la résolution du jeu

`get_viewport_rect().size` donne un `Vector2` contenant la résolution du viewport.

## Génération de nombres aléatoires

- `randomize` modifie la graine.
- `randf` génère un nombre aléatoire à virgule compris entre 0 et le nombre passé en paramètre.
- `randi` génère un nombre aléatoire entier compris entre 0 et le nombre passé en paramètre.
- `rand_range` génère un nombre aléatoire compris entre un nombre et un autre.

```python
randomize()
nombre = rand_range(2.5, 5.75)
```

## Charger une scène

```python
onready var sprite = preload("res://sprite.tscn")

func _ready():
    var s = sprite.instance()
    add_child(s)
```

## Définir la façon d'importer les images

Sélectionnez une ou plusieurs images dans le panneau `Système de fichiers`. Dans le panneau `Importer`, le nom de l'image ou le nombre de fichiers sélectionnées est affiché. Dans la sous-section `Flags`, cochez / décochez la ligne `Filter` pour activer / désactiver le lissage de l'image. Pour des jeux en pixel art, décochez la case. Ensuite, cliquez sur le bouton `Ré-importer` en bas du panneau. Cela applique le réglage sur la ou les images sélectionnées.

Si vous voulez appliquer ce réglage à toutes les images que vous ajouterez par la suite cliquez sur le texte `Pré-réglage...` et choisissez l'option `Définir comme défaut pour « Texture »`. Cela ne s'applique pas à celles déjà importées dans le projet. Pour ces dernières, vous devrez les ré-importer manuellement.

Si vous voulez appliquer un réglage à une image associée à un Sprite, sélectionnez-le, puis, en haut à gauche du panneau `Inspecteur`, cliquez sur la flèche droite. Dans la sous-section `Texture`, cochez / décochez l'option `Filter` de la ligne `Flags`. Si vous double cliquez sur une image du panneau `Système de fichiers`, vous pouvez également utiliser le panneau `Inspecteur`. 

## Contrôles

`Input.is_action_pressed` renvoie si une action est enfoncée ou non.

```python
if Input.is_action_pressed("ui_up"):
    pass
```

## GDScript

```
var variable : type = valeur
```

Les types de base :

- `bool`
- `int`
- `float`
- `String`

```
var nombre1 : int = 10
var nombre2 : int = 5
var somme : int = nombre1 + nombre2
var difference : int = nombre1 - nombre2
var produit : int = nombre1 * nombre2
var quotient : int = nombre1 / nombre2
var reste : int = nombre1 % nombre2
var comparaison : bool = nombre1 == nombre2
comparaison = nombre1 != nombre2
comparaison = nombre1 < nombre2
comparaison = nombre1 <= nombre2
comparaison = nombre1 > nombre2
comparaison = nombre1 >= nombre2
comparaison = not comparaison
comparaison = comparaison and comparaison
comparaison = comparaison or comparaison
```

Un nombre négatif ou nul, une chaine ou un tableau vide, sont évalués à `false`.

```
var tableau_vide : Array = []
var tableau : Array = [1, 2, 3]
print(tableau[0])
```

```
if condition1:
    instruction1
elif condition2:
    instruction2
else:
    instruction3
```

```
for element in array:
    instruction
```

`continue` passe à l'itération suivante.

`break` sort de la boucle.

```
var objet : Object = Object.new()
```

```
func nom_de_fonction(nom_de_parametre : type_du_parametre) -> type_de_retour:
    instructions
```

```
extends NomDeClasse
```

```
if Input.is_action_pressed("action"):
    instructions
```

```
velocity = move_and_slide(velocity, Vector2.UP)
```

```
if velocity.x != 0:
    sprite.flip_h = velocity.x > 0
```

### Nombre aléatoires

Par défaut, Godot utilise le même seed pour générer des nombres aléatoires. Appelez la fonction `randomize` pour modifier ce comportement.

```
randomize()
```

La fonction `rand_range` renvoie un nombre à virgule compris dans un intervalle passé en argument.

```
nombre_aleatoire = rand_range(min, max)
```

### Obtenir les dimensions du viewport

Appelez la méthode `get_viewport_rect`.

```
viewport_rect = get_viewport_rect()
```

### Signaux

#### Définir un nouveau signal

Définissez un nouveau signal en le faisant précéder du mot clé `signal`.

```
signal nom_signal
```

**Remarque :** Utilisez un verbe d'action au passé comme nom de signal.

Vous pouvez également définir un signal avec des paramètres.

```
signal nom_signal(nom_paramètre)
```

#### Emettre un signal

Utilisez la méthode `emit_signal` et passez le signal sous forme de chaine.

```
emit_signal("nom_signal")
```

**Remarque :** Cette technique est très utile lorsque vous avez un noeud dans votre scène qui n'est pas la racine. Si vous instanciez cette scène dans une autre, vous ne pouvez pas connecter de signal d'un noeud enfant. Pour cela, connectez le noeud racine de la scène à instancier à un signal d'un de ses noeuds enfants et émettez un nouveau signal. Ce dernier peut ainsi être connecté à un noeud de l'autre scène.

Si vous avez défini un signal avec des paramètres, passez-les lors de l'appel à la fonction `emit_signal`.

```
emit_signal("nom_signal", paramètre)
```

#### Connectez un noeud à un signal

Utilisez la méthode `connect` en passant le signal sous forme de chaine, l'objet à connecter et la méthode à appeler sous forme de chaine. En général, on définit le nom de la méthode en faisant précéder le nom du signal par le préfixe `on`.

```
noeud.connect("nom_signal", self, "on_nom_signal")
```

**Attention !** Certains signaux utilisent des paramètres. La méthode connectée recevra ces paramètres en arguments lors de l'appel. Pensez à le prévoir dans la méthode.

## Créer un nouveau type de ressource

Dans le panneau FileSystem, faites un clic droit et créez un nouveau script.

```
class_name NomDeRessource
extends resource

# vous pouvez définir des variables, les exporter ou définir des fonctions
```

Pour instancier une nouvelle ressource de ce type, dans le panneau FileSystem, faites un clic droit, sélectionnez `New Resource...` et choisissez la nouvelle ressource `NomDeRessource`.



