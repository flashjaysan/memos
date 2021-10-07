# Mémo cocos2d-Python

Par *flashjaysan*

## Introduction

cocos2d est un framework dédié à la création de jeux vidéos 2D, de démos et autres applications graphiques et interactives. Il est basé sur le module pyglet qui nécessite le module AVbin pour lire des formats vidéos et audios. Il est truffé de fonctionnalités et sa conception est si bonne qu’il a gagné une énorme popularité au point qu’il a été porté pour de nombreux langages et environnements :

- C++ : cocos2d-x
- JavaScript : cocos2d-JS
- Lua : cocos2d-lua
- MonoGame : cocos2d-XNA
- Objective-C : cocos2d-ObjC

Ainsi, si vous apprenez cocos2d pour Python (l’original), vous pourrez par la suite adapter vos jeux à d’autres plateformes plus performantes. Vous gagnez donc en polyvalence sans avoir à réapprendre un nouveau framework.

cocos2d simplifie le développement de jeux car :

- Il gère le déroulement du jeu entre les différentes scènes d'une façon simple.
- Il permet une gestion des sprites rapide et facile.
- Il fournit des actions pour contrôler les sprites de manière automatique.
- Il gère les effets visuels tels que des vagues, des tourbillons, des effets de lentilles et plus encore...
- Il gère des systèmes de particules tels que des explosions, des feux d'artifice, des météores, de la fumée et plus encore…
- Il gère les tilemaps rectangulaires et hexagonales.
- Il fournit une gestion des collisions.
- Il permet de faire des transitions entre les scènes.
- Il fournit des classes pour créer des menus.
- Il permet l'affichage de texte.
- Il fournit un interpréteur Python pour le débogage.
- Il est sous licence libre (BSD).
- Il est basé sur OpenGL et supporte donc l'accélération matérielle.

## Préparations

### Installer cocos2d

cocos2d n'est pas installé avec les distributions de Python mais le framework est vraiment facile à installer une fois Python déjà en place. Utilisez simplement la commande `pip` suivante :

```
pip install cocos2d
```

Grâce à cette commande, toutes les dépendances sont installées automatiquement. Si cela ne fonctionne pas, installez les bibliothèques `six` et `pyglet` puis téléchargez cocos2d manuellement. Dézippez le fichier puis placez-vous dans le dossier et installez cocos2d avec la commande suivante :

```
setup.py install
```

En cas de difficulté, consultez la page suivante :

http://python.cocos2d.org/doc/programming_guide/installation.html

### Utiliser cocos2d

La première chose à faire avant d'utiliser cocos2d est d'importer le package du framework. Placez la ligne suivante au début de vos fichiers sources :

```python
import cocos
```

Vous pouvez dès à présent commencer à programmer vos premiers jeux avec cocos2d. Amusez-vous bien !

### Le singleton director

cocos2d fournit un objet spécial nommé `director` qui gère l'ensemble des scènes du jeu. C'est une instance unique (un singleton) de la classe `Director` qui sait quelle scène est active à un instant donné et qui gère une pile de scènes pour les enchaîner ou les mettre en pause. Le singleton `director` est également responsable de la création et de la gestion de la fenêtre principale.

Le singleton `director` est situé dans le module `cocos.director`. Pour y accéder, utilisez la hiérarchie suivante :

```python
cocos.director.director
```

### Créer une fenêtre de jeu

Pour créer une fenêtre de jeu vide, initialisez le singleton `director`. Pour cela, utilisez la méthode `init` :

```python
cocos.director.director.init()
```

Cette méthode prend les paramètres suivants :

- autoscale : booléen. Si vous donnez la valeur `True`, cocos2d redimensionne automatiquement la vue si la fenêtre change de taille. Dans le cas contraire, c'est à vous de le gérer manuellement. Par défaut, la valeur est `False`.
- audio_backend : chaîne de caractères. Définit le moteur audio à utiliser. Par défaut, vaut `Pyglet` mais vous pouvez également utiliser la valeur `sdl`.
- audio : dictionnaire ou None. Fournit des paramètres au moteur audio SDL. `None` est un système audio désactivé. Le dictionnaire correspond à des arguments pour régler la sortie audio. Vous pouvez passer l'argument `{}` pour un réglage par défaut. Dans le cas contraire, consultez le lien suivant :
http://www.pygame.org/docs/ref/mixer.html#pygame.mixer.init
- fullscreen : booléen. Définit si le jeu doit s'afficher en mode plein écran. Par défaut, vaut `False`.
- resizable : booléen. Définit si la fenêtre est redimensionnable. Par défaut, vaut `False`.
- vsync : booléen. Définit si l'affichage doit se synchroniser avec la fréquence d'affichage de l'écran. Par défaut, vaut `True`.
- width : entier. Définit la largeur en pixels de la fenêtre. Par défaut, vaut 640.
- height : entier. Définit la hauteur en pixels de la fenêtre. Par défaut, vaut 480.
- caption : chaîne de caractères. Définit le texte de la barre de titre de la fenêtre.
- visible : booléen. Définit si la fenêtre est visible. Par défaut, vaut `True`.

La méthode renvoie une instance de type `pyglet.window.Window` correspondant à la fenêtre principale du jeu.

Une fois le singleton `director` initialisé, démarrez la première scène avec la méthode `run` et passez en argument la scène de votre choix (une instance de type `cocos.scene.Scene`) :

```python
cocos.director.director.run(première_scène)
```

Le code suivant passe une scène vide en argument à la méthode `run` :

```python
cocos.director.run(cocos.scene.Scene())
```

Exécutez le code, une fenêtre vide avec des paramètres par défaut est créée.

**Remarque :** En pratique, ne passez pas une scène vide en argument de la méthode `run` mais bien une scène que vous aurez confectionnée selon vos besoins.

### Remplacer une scène active

Pour remplacer la scène active par une autre, utilisez la méthode `replace` du singleton `director` en lui passant en argument la nouvelle scène :

```python
cocos.director.director.replace(nouvelle_scène)
```

**Remarque :** Pour changer de scène avec une transition, consultez la section sur le sujet.

Avec cette méthode, la scène courante est terminée. Si vous souhaitez sauvegarder son état pour l'utiliser de nouveau, utilisez plutôt la méthode `push` du singleton `director` en lui passant en argument la nouvelle scène :

```python
cocos.director.director.push(nouvelle_scène)
```

### Restaurer une scène sauvegardée

Pour restaurer la dernière scène sauvegardée avec la `méthode push`, utilisez la méthode `pop` du singleton `director` :

```python
cocos.director.director.pop()
```

Avec cette méthode, la scène courante est terminée. Si vous souhaitez le faire manuellement, utilisez plutôt la méthode `scene.end` du singleton `director` en lui passant en argument une valeur de fin. La scène située au sommet de la pile de scènes est ensuite démarrée :

```python
cocos.director.director.scene.end(valeur_de_fin)
```

### La classe CocosNode

La classe `cocos.cocosnode.CocosNode` est la super classe de base de la plupart de celles représentant des éléments graphiques. Tout ce qui est affiché ou contient des choses qui le sont est un objet CocosNode. Les sous-classes les plus utilisées sont `cocos.scene.Scene`, `cocos.layer.base_layers.Layers` et `cocos.sprite.Sprite`. La classe `CocosNode` dérive de la classe `object`. L'avantage d'avoir une classe générale pour la plupart des classes existantes et que celles-ci partagent un ensemble de fonctionnalités communes.

Un objet CocosNode peut :

- contenir d'autres objets CocosNode (`add`, `get`, `remove`, etc).
- programmer des fonctions d'appel périodiques (`schedule`, `schedule_interval`, etc).
- exécuter des actions (`do`, `pause`, `stop`, etc).

Dériver de la classe CocosNode signifie généralement :

- surcharger la méthode` __init__` pour initialiser les ressources et programmer les fonctions d'appel.
- créer des fonctions d'appel pour gérer le temps.
- surcharger la méthode `draw` pour afficher le node.

### Attacher un objet CocosNode à un autre

Pour attacher un objet CocosNode à un autre, utilisez la méthode `add` de la classe CocosNode :

```python
objet_conteneur.add(objet_enfant, z=nombre, name=None)
```

Cette méthode prend les paramètres suivants :

- objet_enfant : CocosNode. Correspond à l'objet à attacher à l'objet conteneur.
- z : nombre à virgule flottante (optionnel). Correspond à l'index de l'objet enfant. Par défaut, prend la valeur 0.
- name : chaîne de caractères ou None (optionnel). Correspond au nom à attribuer à l'objet enfant. Par défaut, prend la valeur `None`.

Cette méthode renvoie l'objet conteneur.

Le nombre `z` correspond à l'ordre dans lequel l'objet conteneur et ses enfants sont affichés. Les objets enfants sont affichés dans l'ordre croissant de leur valeur `z`. Cependant, l'objet conteneur est affiché après les objets enfants ayant une valeur `z` négative et avant les objets enfants ayant une valeur `z` positive. Vous pouvez ainsi contrôler l'ordre d'affichage des différents éléments.

### Les scènes

Une scène peut avoir plusieurs calques. 


### Les calques



### Les sprites




### Les événements




### Les actions





### Les transformations




### Les effets







### Les transitions de scènes





### Les tilemaps






### Les collisions






