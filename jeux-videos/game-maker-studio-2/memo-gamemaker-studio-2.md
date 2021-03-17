# Mémo GameMaker Studio 2

*par flashjaysan*

## Table des matières

- [Mémo GameMaker Studio 2](#m-mo-gamemaker-studio-2)
  * [Introduction](#introduction)
  * [Versions de GameMaker Studio 2](#versions-de-gamemaker-studio-2)
  * [Concepts de base](#concepts-de-base)
    + [Système de coordonnées et angles](#syst-me-de-coordonn-es-et-angles)
  * [Gérer le projet](#g-rer-le-projet)
    + [Créer un nouveau projet](#cr-er-un-nouveau-projet)
    + [Régler le nombre d'images par seconde](#r-gler-le-nombre-d-images-par-seconde)
    + [Compiler et exécuter le jeu](#compiler-et-ex-cuter-le-jeu)
    + [Définir la résolution du jeu](#d-finir-la-r-solution-du-jeu)
  * [L'éditeur](#l--diteur)
    + [Les ressources](#les-ressources)
      - [Créer une ressource](#cr-er-une-ressource)
      - [Ouvrir une ressource dans l'éditeur](#ouvrir-une-ressource-dans-l--diteur)
    + [Les sprites](#les-sprites)
      - [Créer un sprite vide](#cr-er-un-sprite-vide)
      - [Importer une image dans un sprite](#importer-une-image-dans-un-sprite)
      - [Créer automatiquement un sprite à partir d'un fichier image](#cr-er-automatiquement-un-sprite---partir-d-un-fichier-image)
      - [Origine d'un sprite](#origine-d-un-sprite)
      - [Zone de collision d'un sprite](#zone-de-collision-d-un-sprite)
    + [Les rooms](#les-rooms)
      - [Créer une room](#cr-er-une-room)
      - [Définir la couleur de fond](#d-finir-la-couleur-de-fond)
    + [Les objects](#les-objects)
      - [Créer un object](#cr-er-un-object)
      - [Editer un object](#editer-un-object)
      - [Attribuez un sprite à un object](#attribuez-un-sprite---un-object)
    + [Les sounds](#les-sounds)
      - [Créer un sound](#cr-er-un-sound)
  * [Evènements](#ev-nements)
    + [Clavier](#clavier)
    + [Timers](#timers)
  * [GML](#gml)
    + [Commentaires](#commentaires)
    + [Variables](#variables)
      - [Variables prédéfinies](#variables-pr-d-finies)
      - [Variables d'instance](#variables-d-instance)
      - [Variables locales](#variables-locales)
      - [Variables globales](#variables-globales)
      - [Variables globales prédéfinies](#variables-globales-pr-d-finies)
    + [Macros](#macros)
    + [Types de base et conversion](#types-de-base-et-conversion)
    + [Afficher un message](#afficher-un-message)
    + [Afficher du texte](#afficher-du-texte)
    + [Saisie de l'utilisateur](#saisie-de-l-utilisateur)
    + [Tableaux](#tableaux)
    + [Énumérations](#-num-rations)
    + [Opérateurs](#op-rateurs)
    + [Affectation simple et composée](#affectation-simple-et-compos-e)
    + [Incrémentation et décrémentation](#incr-mentation-et-d-cr-mentation)
    + [Instruction conditionnelle](#instruction-conditionnelle)
    + [Boucles](#boucles)
    + [Ressources scripts et fonctions](#ressources-scripts-et-fonctions)
    + [Scripter les instances](#scripter-les-instances)
      - [Propriétés prédéfinies d'une instance](#propri-t-s-pr-d-finies-d-une-instance)
      - [Créer une instance](#cr-er-une-instance)
      - [Détruire une instance](#d-truire-une-instance)
      - [Vérifier si une instance existe](#v-rifier-si-une-instance-existe)
      - [Consulter les propriétés d'une instance dans une room](#consulter-les-propri-t-s-d-une-instance-dans-une-room)
      - [Tester si une instance entre en collision avec une autre instance](#tester-si-une-instance-entre-en-collision-avec-une-autre-instance)
      - [Déterminer le nombre d'instances d'un object contenues dans une Room](#d-terminer-le-nombre-d-instances-d-un-object-contenues-dans-une-room)
      - [Déterminer si une instance est située en dehors de la room](#d-terminer-si-une-instance-est-situ-e-en-dehors-de-la-room)
      - [Déplacer automatiquement une instance vers un point](#d-placer-automatiquement-une-instance-vers-un-point)
    + [Sprites](#sprites)
      - [Retourner ou redimensionner un sprite](#retourner-ou-redimensionner-un-sprite)
      - [Propriétés prédéfines des sprites](#propri-t-s-pr-d-fines-des-sprites)
    + [Shaders](#shaders)
    + [Effets de particules](#effets-de-particules)
      - [Effets prédéfinis](#effets-pr-d-finis)
      - [Système de particules personnalisé](#syst-me-de-particules-personnalis-)
        * [Système de particule](#syst-me-de-particule)
        * [Création et configuration d'une particule](#cr-ation-et-configuration-d-une-particule)
          + [Type de particule](#type-de-particule)
          + [Forme prédéfinie](#forme-pr-d-finie)
          + [Sprite personnalisé](#sprite-personnalis-)
          + [Durée de vie](#dur-e-de-vie)
          + [Taille](#taille)
          + [Orientation](#orientation)
          + [Couleur](#couleur)
          + [Mélange](#m-lange)
          + [Direction](#direction)
          + [Vitesse](#vitesse)
          + [Force de gravité](#force-de-gravit-)
          + [Opacité](#opacit-)
        * [Génération de particules](#g-n-ration-de-particules)
          + [Génération sur un point](#g-n-ration-sur-un-point)
          + [Génération dans une région](#g-n-ration-dans-une-r-gion)
        * [Cleanup](#cleanup)
    + [Exemple de code pour retourner un personnage avec les flèches du clavier](#exemple-de-code-pour-retourner-un-personnage-avec-les-fl-ches-du-clavier)
    + [Trouver la doc des variables prédéfinies](#trouver-la-doc-des-variables-pr-d-finies)
    + [Surfaces](#surfaces)
    + [Contrôles](#contr-les)
      - [Souris](#souris)
        * [Position du pointeur](#position-du-pointeur)
        * [Appui d'un bouton de souris](#appui-d-un-bouton-de-souris)
        * [Constantes prédéfinies liées à la souris](#constantes-pr-d-finies-li-es---la-souris)
      - [Clavier](#clavier-1)
      - [Appui d'une touche du clavier](#appui-d-une-touche-du-clavier)
        * [Constantes prédéfinies liées au clavier](#constantes-pr-d-finies-li-es-au-clavier)
        * [Touches alphanumériques du clavier](#touches-alphanum-riques-du-clavier)
        * [Associer une touche du clavier à une autre](#associer-une-touche-du-clavier---une-autre)
      - [Gamepads](#gamepads)
    + [Génération aléatoire](#g-n-ration-al-atoire)
    + [Scripting associé aux rooms](#scripting-associ--aux-rooms)
      - [Dimensions d'une room](#dimensions-d-une-room)
      - [Ajouter du code à une room](#ajouter-du-code---une-room)
      - [Organisation des rooms](#organisation-des-rooms)
    + [Sons et musiques](#sons-et-musiques)
      - [Lecture](#lecture)
      - [Vérifier qu'un son est en lecture](#v-rifier-qu-un-son-est-en-lecture)
      - [Modifier le gain](#modifier-le-gain)
    + [Dessin](#dessin)
      - [Définir la couleur de dessin](#d-finir-la-couleur-de-dessin)
      - [Couleurs](#couleurs)
        * [Couleurs prédéfinies](#couleurs-pr-d-finies)
      - [Dessiner un sprite](#dessiner-un-sprite)
      - [Dessiner une barre de vie](#dessiner-une-barre-de-vie)
    + [Techniques d'animation automatique](#techniques-d-animation-automatique)
      - [Interpolation linéaire](#interpolation-lin-aire)
      - [Easing](#easing)
    + [Utiliser des fichiers](#utiliser-des-fichiers)
      - [Fichiers INI](#fichiers-ini)
        * [Ouvrir un fichier *INI*](#ouvrir-un-fichier--ini-)
        * [Lecture d'un fichier *INI*](#lecture-d-un-fichier--ini-)
        * [Ecriture dans un fichier *INI*](#ecriture-dans-un-fichier--ini-)
        * [Fermeture d'un fichier *INI*](#fermeture-d-un-fichier--ini-)
  * [Divers](#divers)
    + [Redémarrer le jeu](#red-marrer-le-jeu)
    + [Quitter le jeu](#quitter-le-jeu)
    + [Propriétés de viewports](#propri-t-s-de-viewports)
    + [L'affichage du jeu](#l-affichage-du-jeu)
    + [Résolution](#r-solution)
    + [La surface d'application](#la-surface-d-application)
    + [Le calque GUI](#le-calque-gui)
    + [Ecran splitté](#ecran-splitt-)
    + [Bitmap fonts](#bitmap-fonts)
    + [Convertir une direction en un nombre](#convertir-une-direction-en-un-nombre)

## Introduction

GameMaker Studio 2 est un moteur de jeux vidéos multi-plateformes. Principalement destiné à la création de jeux vidéos 2D, il embarque une multitude d'outils pour faciliter le développement. Il propose de scripter les comportements des éléments de jeu avec deux approches différentes.

- La première approche appelée *Drag and drop* (*DND*) vous permet de manipuler et d'organiser visuellement des briques d'actions. Elle est destinée aux débutants.
- La seconde approche utilise le langage de programmation *GameMaker Language* (*GML*) spécifique à GameMaker Studio 2. Cette approche est la plus utilisée car elle permet un contrôle plus précis des choses.

## Versions de GameMaker Studio 2

GameMaker Studio 2 est proposé en différentes versions.

- La version **Trial** correspond à la version d'essai de GameMaker Studio 2. Vous devez vous inscrire sur le site de Yoyo Games et télécharger cette version.
  - Vous bénéficiez de 30 jours d'utilisation à compter du jour de votre inscription.
  - Vous ne pouvez pas exporter vos jeux.
  - Vous ne pouvez pas désactiver la notification de la version d'essai.
  - Vous ne pouvez pas créer de compte Marketplace Publisher mais vous pouvez utiliser votre compte Yoyo Games pour accéder au contenu du Marketplace.
- La version **Creator** à 39 € par an vous permet d'exporter votre jeu soit pour Windows soit pour Mac OS selon la version que vous avez choisie.
  - Vous ne pouvez pas supprimer l'écran splash par défaut.
  - Vous ne pouvez exporter votre jeu qu'avec la machine virtuelle.
  - Cette licence moins cher ne dure toutefois qu'un an.
- La version **Desktop** à 99 € vous permet d'exporter votre jeu pour Windows, Mac OS, et Ubuntu.
  - Vous pouvez exporter votre jeu sur les trois plateformes en utilisant la machine virtuelle ou le compilateur natif YYC.
  - Cette licence est permanente.
- La version **Web** à 149 € vous permet d'exporter votre jeu pour HTML5.
  - Vous pouvez exporter votre jeu pour le web (en JavaScript).
  - Cette licence est permanente.
- La version **UWP** à 199 € vous permet d'exporter votre jeu pour la plateforme Microsoft Universal Windows Platform ainsi que le programme Xbox One Creators.
  - Vous pouvez exporter votre jeu en utilisant la machine virtuelle ou le compilateur natif YYC.
  - Cette licence est permanente.
- La version **Mobile** à 199 € vous permet d'exporter votre jeu pour Android, Fire et iOS.
  - Vous pouvez exporter votre jeu sur les trois plateformes en utilisant la machine virtuelle ou le compilateur natif YYC.
  - Cette licence est permanente.
- La version **PS4** à 799 € par an vous permet d'exporter votre jeu pour la console PS4 de Sony.
  - Vous devez posséder un compte de développeur Sony.
  - Cette licence ne dure qu'un an.
- La version **Xbox One** à 799 € par an vous permet d'exporter votre jeu pour la console Xbox One de Microsoft.
  - Vous devez posséder un compte de développeur Microsoft.
  - Cette licence ne dure qu'un an.
- La version **Switch** à 799 € par an vous permet d'exporter votre jeu pour la console Switch de Nintendo.
  - Vous devez posséder un compte de développeur Nintendo.
  - Cette licence ne dure qu'un an.
- La version **Ultimate** à 1500 € par an vous permet d'exporter votre jeu pour toutes les plateformes précédentes.
  - Vous pouvez exporter sur toutes les plateformes possibles.
  - Pour exporter sur PS4 vous devez posséder un compte de développeur Sony.
  - Pour exporter sur Xbox One vous devez posséder un compte de développeur Microsoft.
  - Pour exporter sur Switch vous devez posséder un compte de développeur Nintendo.
  - Cette licence ne dure qu'un an.

**Remarque :** Les prix listés correspondent au prix hors promotion. Comme ils sont relativement couteux, surveillez le site officiel, Humble Bundle et Steam pour vous procurer ces licenses un peu moins cher.

## Concepts de base

Dans GameMaker Studio 2, un jeu est essentiellement constitué de ressources appelées *rooms*. Ce sont les écrans ou niveaux de votre jeu. Chaque room comporte à son tour des *instances* de ressources appelées *objects*. Les objets définissent les interactions possibles dans votre jeu et les instances en sont des exemplaires indépendants interagissant dans une room.

**Remarque :** GameMaker Studio 2 fournit une room vide appelée `room0` pour tout nouveau projet.

Les instances d'objets interagissent entre elles par le biais de programmes GML (ou d'actions DND mais cela revient au même) attachés à des *évènements*. Les évènements déclenchent l'exécution des programmes GML.

Pour afficher quelque chose à l'écran, un objet utilise généralement une ou plusieurs ressources appelées *sprites*. Les sprites correspondent aux éléments graphiques de votre jeu. Un sprite peut être une simple image fixe ou une série d'images animées.

Les *sounds* correspondent aux éléments audio de votre jeu. Un sound peut représenter un son ou une musique.

Les ressources objets, sprites et sons sont les plus importantes mais GameMaker Studio 2 fournit de nombreux autres types de ressources pour vous aider à concevoir votre jeu.

### Système de coordonnées et angles

L'axe vertical (Y) augmente vers le bas. L'origine d'une room (à la coordonnée `(0, 0)`) se trouve dans son coin supérieur gauche. Un angle de `0` degré pointe vers la droite. Les angles augmentent dans le sens anti-horaire (le sens inverse des aiguilles d'une montre).

## Gérer le projet

### Créer un nouveau projet

- Sur l'écran de démarrage, cliquez sur le bouton `New`. Si cet écran n'est pas visible, vous pouvez également utiliser le menu `File -> New Project` ou les touches `CTRL+N`.
- Vous devez ensuite choisir entre *GML* et *DND* en cliquant sur les boutons correspondants. Si vous n'êtes pas totalement débutant, je vous conseille d'utiliser *GML*.
- Enfin, sélectionnez un emplacement sur votre ordinateur et donnez un nom à votre projet.

**Remarque :** Les actions *DND* sont converties automatiquement en *GML* lorsque vous exportez votre jeu. Vous pouvez à tout moment demander à voir la conversion en *GML* (sans convertir définitivement le script *DND*) en faisant un clic droit sur les actions *DND* et en choisissant l'option `Live Preview`. Vous pouvez également demander la conversion définitive d'un script *DND* en faisant un clic droit sur l'évènement et en choisissant l'option `Convert to GML`.

### Régler le nombre d'images par seconde

Pour ouvrir le menu de configuration du projet, cliquez sur le bouton `Game Options` ou, dans le panneau `Resources`, dans le dossier `Options`, double cliquez sur l'élément `Main`.

Paramétrez la fréquence de rafraichissement de l'écran de votre jeu (`60` par défaut) à la ligne `Game frames per second`.

**Conseil :** Dans le panneau `Resources`, faites un clic droit sur le dossier `Scripts` et choisissez `Create Script` pour créer un nouveau script. Appelez-le `MACROS.`Dans ce script, saisissez l'instruction' `#macro FRAME_RATE 60`. Cela définit une constante symbolique `FRAME_RATE` dont la valeur est `60` que vous pourrez utiliser partout dans votre projet à la place de la valeur en dur `60`. Si vous modifiez la fréquence de rafraichissement de l'écran de votre jeu, vous n'aurez à modifier cette valeur que dans ce script.

###  Compiler et exécuter le jeu

Cliquez sur le bouton`Run`, sur le menu `Build -> Run` ou appuyez sur la touche `F5`.

**Conseil :** Testez votre jeu régulièrement.

### Définir la résolution du jeu

Par défaut, GameMaker Studio 2 définit la résolution générale du jeu en se basant sur la taille de la première room existante dans le dossier `Rooms` du panneau `Resources`.

- Dans le dossier `Rooms` du panneau `Ressources`, double cliquez sur `room0` (la room créée par défaut) pour l'ouvrir dans l'éditeur. Si vous avez plusieurs rooms dans ce dossier, double cliquez sur la première de la liste.
- Dans la section `Properties` du panneau `Room Editor`, à la sous-section `Room Settings`, définissez les dimensions de la room grâce aux champs `Width` (largeur) et `Height` (hauteur).

**Attention !** Si vous avez activé les *viewports* (en cochant la case `Enable Viewports` dans la sous-section `Viewport and Cameras`) et que des viewports ont leur case `Visible` de cochée, la résolution du jeu sera celle du viewport visible. La résolution du jeu peut donc être différente de la taille de la room (par exemple avec une room très grande où la caméra n'affiche qu'une partie de la room). De plus, vous pouvez définir une résolution d'affichage du jeu différente de celle de la caméra (par exemple si votre jeu en pixel art a une résolution très faible et que vous souhaitez afficher le jeu avec une résolution supérieure). Pour faire simple, chaque caméra a une résolution de capture de la room et une résolution de rendu dans la fenêtre de jeu. Les deux résolutions sont indépendantes mais veillez bien à ce que la résolution de rendu dans la fenètre soit bien aux même proportions (le rapport largeur/hauteur) que la résolution de capture de la caméra associée sinon votre jeu sera déformé dans la fenêtre.

- Pour définir la résolution de capture de la caméra dans la room, utilisez les champs `Width` (largeur) et `Height` (hauteur) de la sous-section `Camera Properties` de chaque viewport visible.
- Pour définir la résolution de rendu de la caméra dans la fenêtre de jeu, utilisez les champs `Width` (largeur) et `Height` (hauteur) de la sous-section `Viewport Properties` de chaque viewport visible.

## L'éditeur

### Les ressources

#### Créer une ressource

Dans le panneau `Resources`, faites un clic droit sur un dossier correspondant à un type de ressource et choisissez l'option `Create X` (où `X` correspond au type de ressource à créer).

Donnez à la nouvelle ressource un nom unique (de préférence avec un préfixe indiquant le type de ressource car GameMaker Studio 2 ne fait pas la distinction entre les différentes ressources).

**Remarque :** Vous pouvez renommer une ressource par la suite en faisant un clic droit dessus et en sélectionnant l'option `Rename` ou en appuyant sur la touche `F2`.

Chacun a sa propre façon de nommer ses variables mais efforcez-vous d'appliquer la même dans tous vos projets. J'ai choisi d'utiliser la convention `snake_case` pour nommer mes ressources avec le premier mot correspondant au type de la ressource :

```js
sprite_player
object_player
tileset_village
sound_village
sound_jump
room_level_1
```

#### Ouvrir une ressource dans l'éditeur

Dans le panneau `Resources`, double cliquez sur la ressource à éditer.

### Les sprites

Bien que vous puissiez utiliser les fonctions de dessin fournies par GameMaker Studio 2 pour afficher des formes géométriques à l'écran, la plupart du temps vous aurez besoin d'importer ou de créer des images pour afficher des choses à l'écran.

GameMaker Studio 2 embarque un éditeur complet de sprites pour vous permettre de créer vos propre sprites directement dans l'éditeur. Il vous permet également d'importer facilement des fichiers images.

#### Créer un sprite vide

Faites un clic droit sur le dossier `Sprites` du panneau `Resources` et choisissez l'option `Create Sprite` ou appuyez sur les touches `ALT+S`.

#### Importer une image dans un sprite

Une fois un sprite vide créé, cliquez sur le bouton `Import` pour sélectionner un fichier image.

#### Créer automatiquement un sprite à partir d'un fichier image

Pour créer des sprites automatiquement à partir de fichiers images, faites simplement glisser les fichiers sur le dossier `Sprites` du panneau `Resources`.

Une animation au format `.gif` est automatiquement importée sous la forme d'une suite d'images composant l'animation mais la couleur associée aux pixels transparents est importée telle quelle. Vous devrez donc supprimer manuellement ces pixels de couleur pour rétablir la transparence.

Un fichier image au format `.png` dont le nom se termine par `_stripX` est automatiquement importé sous la forme d'une suite de `X` images. Les sous-images du fichier image d'origine doivent être disposées à la suite sur une seule ligne. Le format `.png` prend en charge la valeur alpha (l'opacité) des pixels. Les images sont donc importées sans retouches nécessaires dans GameMaker Studio 2.

#### Origine d'un sprite

Lorsque vous affichez un sprite dans une room, vous indiquez sa position par rapport à un point spécifique dans votre image. L'éditeur vous permet de définir ce point d'origine. Par défaut, il est défini dans le coin supérieur gauche de l'image.

#### Zone de collision d'un sprite

GameMaker Studio 2 fournit un ensemble de fonctions pour gérer les collisions entre différents sprites. Pour ces calculs, il vous faut définir une zone de collision pour chaque sprite. Vous avez le choix entre plusieurs options et vous pouvez même définir manuellement les limites de cette zone de collision.

### Les rooms

#### Créer une room

Dans le panneau `Resources`, faites un clic droit sur le dossier `Rooms` puis sélectionnez `Create Room` ou appuyez sur les touches `ALT+R` pour créez une room.

#### Définir la couleur de fond

Dans la section `Layers` du panneau `Room Editor`, définissez la couleur de fond du calque `Background`.

### Les objects

#### Créer un object

Dans le panneau `Resources`, faites un clic droit sur le dossier `Objects` puis sélectionnez `Create Object` ou appuyez sur les touches `ALT+O` pour créez un object.

#### Editer un object

Dans le panneau `ressources`, double cliquez sur l'object à éditer.

#### Attribuez un sprite à un object

Cliquez sur le bouton `No Sprite` pour sélectionner un sprite existant à attribuer à l'object. Vous pouvez également faire glisser un sprite depuis le panneau `Resources` vers ce bouton.

### Les sounds

#### Créer un sound

Dans le panneau `Resources`, faites un clic droit sur le dossier `Sounds` puis sélectionnez `Create Sound` ou appuyez sur les touches `ALT+U` pour créez un sound.

## Les Evènements

### Create

L'évènement `Create` se déclenche lorsqu'une instance de l'objet est créée. Le programme qu'il contient ne s'exécute donc qu'une seule fois. Un objet est créé lorsqu'une instance est placée dans une room et que celle-ci est initialisée ou lorsqu'un programme crée une instance manuellement dans son code. Le programme de cet évènement s'exécute après l'initialisation des variables d'objet et d'instance créées dans l'éditeur.

### Destroy

L'évènement `Destroy` se déclenche lorsqu'une instance de l'objet est détruite. Le programme qu'il contient ne s'exécute donc qu'une seule fois juste avant que l'instance ne soit définitivement détruite.

### Clean Up

L'évènement `Clean Up` se déclenche lorsqu'une instance de l'objet est détruite après l'évènement `Destroy`. Le programme qu'il contient ne s'exécute donc qu'une seule fois. Cet évènement est destiné à libérer la mémoire que l'objet aurait réservé durant son existence. Notez que l'objet termine d'exécuter le programme ayant appelé la fonction `instance_destroy` après l'exécution de cet évènement avant de détruire l'objet.

### Step

- L'évènement `Begin Step` se déclenche chaque step avant l'évènement `Step`. Il se répète tant que l'objet existe.
- L'évènement `Step` se déclenche chaque step après l'évènement `Begin Step` et avant l'évènement `End Step`. Il se répète tant que l'objet existe.
- L'évènement `End Step` se déclenche chaque step après l'évènement `Step`. Il se répète tant que l'objet existe.

### Clavier

- Les évènements de la catégorie `Key Down` se déclenchent à chaque step si une touche est enfoncée.
- Les évènements de la catégorie `Key Pressed` se déclenchent une seule fois dans le step où une touche est enfoncée.
- Les évènements de la catégorie `Key Up` se déclenchent une seule fois dans le step où une touche est relâchée.

### Alarms

Chaque instance d'object a 12 *timers*. La variable d'instance prédéfinie `alarm` est un tableau de 12 éléments. Chaque *frame*, la valeur entière contenue dans chaque élément de ce tableau diminue de `1`. Lorsque la valeur d'un élément du tableau `alarm` atteint `0`, l'évènement `alarm[X]` se déclenche et exécute le script associé à cet évènement.

**Attention !** Si vous ne définissez pas de script pour un timer (même vide), il ne se déclenchera jamais.

Par exemple, vous pouvez définir un *timer* de `60` frames dans l'évènement `Create` dans la première case du tableau `alarm` associé à un object.

```js
alarm[0] = 60;
```

Lorsque 60 *frames* sont passées, l'évènement `alarm[0]` se déclenche. Définissez des instructions à exécuter dans cet évènement. Par exemple, faites apparaître un ennemi.

```js
instance_create_layer(irandom_range(0, Room_width), irandom_range(0, Room_height), "Instances", ennemi);
```

**Remarque :** Après l'exécution du script associé à l'évènement, le *timer* prend la valeur `-1`.

Si vous souhaitez relancer le *timer*, affectez-lui une nouvelle valeur.

```js
alarm[0] = 120;
```

Si vous souhaitez déclencher l'évènement `alarm[0]` immédiatement, donnez-lui la valeur `1` pour que le *timer* se déclenche à nouveau à la *frame* suivante.

```js
alarm[0] = 1;
```

## GML

### Documentation

Vous aurez constamment besoin de consulter la documentation pour apprendre de nouvelles fonctionnalités ou pour obtenir plus de détails. Lorsque vous souhaitez consulter la documentation de GameMaker Studio 2 depuis l'éditeur, cliquez sur le menu `Help -> Open Manual` ou appuyez sur la touche `F1`.

**Remarque :** Vous pouvez consulter la documentation d'une fonction spécifique dans l'éditeur de code en cliquant sur la fonction avec le bouton du milieu de la souris.

### Commentaires

Les commentaires sont des morceaux de code qui sont ignorés par le compilateur. Ils servent essentiellement de moyen de communiquer pour les programmeurs. Vous pouvez vous en servir pour détailler certaines parties complexes de vos programmes (bien qu'il soit en général conseillé de faire un programme clair et lisible avant tout), séparer différentes parties ayant des rôles différents ou indiquer qu'une section n'est pas encore écrite. Vous pouvez également vous en servir pour désactiver temporairement un morceau de programme pour effectuer des tests.

```js
// Commentaire de fin de ligne
```

```js
/*
Commentaire
multi-lignes
*/
```

```js
/// Commentaire de documentation
```

### Variables

#### Variables prédéfinies

GameMaker Studio 2 définit automatiquement certaines variables. Chaque room, chaque instance d'object et de nombreuses autres choses possèdent des variables prédéfinies. Elles s'affichent en vert dans l'éditeur de GameMaker Studio 2.

**Attention !** Soyez attentif à la couleur des variables. Par exemple, la variable `speed` d'un object est une variable prédéfinie dans GameMaker Studio 2.  Si vous donnez à cette variable une valeur différente de `0`, chaque instance de cet object se déplacera automatiquement dans la direction définie par la variable `direction` (qui vaut par défaut `0` degrés, soit une direction vers la droite).

```js
x += 1;
y += 1;
```

#### Variables d'instance

Une variable d'instance est une variable associée à une instance d'un object. Elle peut être accédée ou être modifiée depuis n'importe quelle évènement de l'instance. Elle s'affiche en violet dans l'éditeur de GameMaker Studio 2. Pour éviter les erreurs, on la définit et on l'initialise généralement dans l'évènement `Create` d'un object.

- Créez une variable d'instance dans l'évènement `Create` en lui affectant une valeur. Vous pouvez ensuite y accéder ou la modifier depuis n'importe quel autre évènement de l'instance. 

```js
debut_x = 10;
fin_x = 20;
```

#### Variables locales

Une variable locale est une variable utilisable uniquement dans un seul script. Chaque évènement définit un script différent. A la fin de l'exécution du programme, la variable est détruite. Elle s'affiche en jaune dans l'éditeur de GameMaker Studio 2.

- Créez une variable locale en la faisant précéder du mot clé `var`.

```js
var longueur = debut_x - fin_x;
```

#### Variables globales

Une variable globale est une variable accessible depuis l'ensemble des scripts de votre jeu. Elle s'affiche en rose dans l'éditeur de GameMaker Studio 2.

- Créez une variable globale en ajoutant une sous-variable à la variable prédéfinie `global`.

```js
global.meilleur_score = 100;
```

#### Variables globales prédéfinies

GameMaker Studio 2 fournit trois variables globales prédéfinies accessibles depuis l'ensemble des scripts de votre jeu.

- `score` correspond au score général du joueur.
- `health` correspond aux points de vie du joueur.
- `lives` correspond au nombre de vies du joueur.

**Attention !** La documentation déconseille d'utiliser ces variables.

### Macros

La directive `#macro` vous permet de définir une constante symbolique associée à une valeur. Cette constante peut alors être utilisée à la place de la valeur.

```js
#macro FRAME_RATE 60
```

**Conseil :** Créez une ressource script appelée `MACROS` et définissez vos constantes symboliques dans ce script. En faisant ainsi, toutes les constantes seront accessibles dans tous vos scripts.

### Types de base et conversion

GameMaker Studio 2 utilise trois types de base. Les booléens, les nombres (entiers ou à virgule) et les chaînes de caractères.

Un booléen peut valoir `false` (faux) ou `true` (vrai).  Ces valeurs sont équivalentes aux valeurs entières `0` et `1`.

GameMaker Studio 2  ne fait pas de distinction entre les nombres entiers et les nombres à virgules.

```js
var dix = 10;
var demi = 0.5;
var dix_et_demi = dix + demi;
```

Les littéraux chaînes sont écrits entre guillemets doubles.

```js
var salut = "Bonjour";
```

Vous pouvez concaténer plusieurs chaînes avec l'opérateur `+`.

```js
var salut = "Bonjour";
var nom = "Steve";
var message = salut + ", " + nom + ".";
```

Vous pouvez convertir un nombre en chaîne grâce à la fonction `string`.

```js
var nombre = 10.5;
var chaine_nombre = string(nombre);
```

Vous pouvez convertir une chaîne en nombre grâce à la fonction `real`.

```js
var chaine_dix = "10";
var dix = real(chaine_dix);
```

### Afficher un message

La fonction `show_message` prend une chaîne de caractères en paramètre et l'affiche dans une boîte de dialogue lorsque l'évènement associé se déclenche.

**Conseil :** Evitez d'utilisez cette fonction au profit de la fonction `draw_text` qui affiche du texte directement dans l'écran de jeu.

### Afficher du texte

La fonction `draw_text` vous permet d'afficher du texte dans l'écran de jeu. Le texte est affiché avec la font et dans la couleur actuellement sélectionnées. Par défaut, c'est une font de type `Arial` de taille `10` et de couleur blanche qui est active. Utilisez cette fonction dans un évènement `Draw` ou `Draw GUI`.

- Le premier paramètre correspond à la position horizontale du texte à afficher.
- Le deuxième paramètre correspond à la position verticale du texte à afficher.
- Le troisième paramètre correspond au texte à afficher.

**Remarque :** La fonction `draw_text_transformed` propose d'afficher du texte avec plus de contrôle.

- Le premier paramètre correspond à la position horizontale du texte à afficher.
- Le deuxième paramètre correspond à la position verticale du texte à afficher.
- Le troisième paramètre correspond au texte à afficher.
- Le quatrième paramètre correspond à l'échelle horizontale à appliquer au texte à afficher.
- Le cinquième paramètre correspond à l'échelle verticale à appliquer au texte à afficher.
- Le sixième paramètre correspond à l'angle d'inclinaison à appliquer au texte à afficher.

### Saisie de l'utilisateur

La fonction `get_string` affiche une boîte de dialogue proposant à l'utilisateur de saisir une chaîne de caractères que vous pouvez ensuite utiliser dans votre jeu.

- Le premier paramètre est une chaîne correspondant au titre de la boîte de dialogue.
- Le second paramètre correspond à la chaîne de caractères utilisée par défaut et affichée dans le champ de saisie.

```js
var name = get_string("Saisissez votre nom :", "Steve");
```

La fonction `get_integer` affiche une boîte de dialogue proposant à l'utilisateur de saisir un nombre entier que vous pouvez ensuite utiliser dans votre jeu.

- Le premier paramètre est une chaîne correspondant au titre de la boîte de dialogue.
- Le second paramètre correspond à un nombre utilisé par défaut et affiché dans le champ de saisie.

```js
var age = get_integer("Saisissez votre age :", 18);
```

**Remarque :** L'utilisateur peut également saisir un nombre à virgule.

Les fonctions `get_integer_async` et `get_string_async` fonctionnent de la même manière mais de manière asynchrone. Le jeu continue à s'exécuter même si la saisie n'est pas terminée. Pour cela ces fonctions renvoient un identifiant associé à un objet de type `ds_map`. Consultez la documentation sur ces fonctions pour plus d'information.

### Tableaux

Utilisez un indice entre des crochets pour accéder aux éléments d'un tableau. Le premier élément est à l'indice `0`.

```js
tableau[indice] = valeur;
```

Utilisez une liste d'indices séparés par une virgule pour manipuler un tableau à plusieurs dimensions.

```js
tableau_deux_dimensions[indice_1, indice_2] = valeur;
```

### Énumérations

Les énumérations sont globales. Utilisez le mot clé `enum` suivi du nom de l'énumération et listez vos constantes séparées par une virgule dans des accolades.

```js
enum nom_enum {
    CONSTANTE_1,
    CONSTANTE_2,
    CONSTANTE_3,
    CONSTANTE_4
}
```

Chaque constante est associée à un entier. Par défaut, la première constante prend la valeur zéro. Une constante prend la valeur entière de la constante précédente plus un. Vous pouvez affecter une valeur spécifique à une constante.

```js
enum nom_enum {
    CONSTANTE_1, // 0
    CONSTANTE_2, // 1
    CONSTANTE_3 = 10, // 10
    CONSTANTE_4 // 11
}
```

Utilisez une constante en la faisant précéder du nom de l'énumération et d'un point. Comme ce sont des constantes, vous ne pouvez pas modifier leur valeur.

```js
variable_name = nom_enum.CONSTANTE_2;
```

**Remarque :** Comme ces constantes sont des valeurs entières, vous pouvez vous en servir comme des indices de tableaux.

### Opérateurs

- `+` : s'applique sur deux nombres et donne un nombre. Calcule la somme de ses opérandes.
- `-` : s'applique sur deux nombres et donne un nombre. Calcule la différence de ses opérandes.
- `-` : appliqué sur un seul nombre et donne un nombre. Calcule l'opposé de son opérande.
- `*` : s'applique sur deux nombres et donne un nombre. Calcule le produit de ses opérandes.
- `/` : s'applique sur deux nombres et donne un nombre. Calcule la division de ses opérandes.
- `%` : s'applique sur deux nombres et donne un nombre. Calcule le reste de la division de ses opérandes.
- `mod` : s'applique sur deux nombres et donne un nombre. Calcule le reste de la division entière de ses opérandes.
- `div` : s'applique sur deux nombres et donne un nombre. Calcule le quotient de la division entière de ses opérandes.
- `<` : s'applique sur deux nombres et donne un booléen. Vrai si le premier opérande est inférieur au second opérande.
- `<=` : s'applique sur deux nombres et donne un booléen. Vrai si le premier opérande est inférieur ou égale au second opérande.
- `>` : s'applique sur deux nombres et donne un booléen. Vrai si le premier opérande est supérieur au second opérande.
- `>=` : s'applique sur deux nombres et donne un booléen. Vrai si le premier opérande est supérieur ou égal au second opérande.
- `==` : s'applique sur deux nombres et donne un booléen. Vrai si le premier opérande est égal au second opérande.
- `!=` : s'applique sur deux nombres et donne un booléen. Vrai si le premier opérande est différent du second opérande.
- `!` ou `not` : donne un booléen correspondant à la négation de son opérande booléen (inverse la valeur de l'opérande).
- `&&` ou `and` : s'applique sur deux booléens et donne un booléen. Vrai si les deux opérandes sont vrais.
- `||` ou `or` : s'applique sur deux booléens et donne un booléen. Vrai si au moins un des deux opérandes est vrai.
- `^^` : s'applique sur deux booléens et donne un booléen. Vrai un seul des deux opérandes est vrai.

### Affectation simple et composée

```js
nom_de_variable = valeur;
nom_de_variable += valeur; // équivalent à nom_de_variable = nom_de_variable + valeur
nom_de_variable -= valeur; // équivalent à nom_de_variable = nom_de_variable - valeur
nom_de_variable *= valeur; // équivalent à nom_de_variable = nom_de_variable * valeur
nom_de_variable /= valeur; // équivalent à nom_de_variable = nom_de_variable / valeur
nom_de_variable %= valeur; // équivalent à nom_de_variable = nom_de_variable % valeur
```

### Incrémentation et décrémentation

```js
nom_de_variable++;
++nom_de_variable;
nom_de_variable--;
--nom_de_variable;
```

### Instruction conditionnelle

```js
if (condition)
    // instruction
```

```js
if (condition)
{
    // instructions
}
```

```js
if (condition)
    // instruction
else
    // instruction
```

```js
if (condition)
{
    // instructions
}
else
{
    // instructions
}
```

```js
switch (valeur)
{
    case CONSTANTE_1:
        // instructions
        break;
    case CONSTANTE_2:
        // instructions
        break;
    ...
    default:
        //instructions
}
```

### Boucles

```js
while (condition)
    // instruction
```

```js
while (condition)
{
    // instructions
}
```

```js
for (var i = 0; i < valeur; i++)
    // instruction
```

```js
for (var i = 0; i < valeur; i++)
{
    // instructions
}
```

```js
repeat (nombre_de_fois)
    // instruction
```

```js
repeat (nombre_de_fois)
{
    // instructions
}
```

```js
do
{
    // instructions
} until (condition);
```

### Ressources scripts et fonctions

Créez une ressource script dans le dossier `Scripts` du panneau `Resources`.

```js
// script some_function
show_message('Hello');
```

Vous pouvez ensuite appeler le script par son nom comme s'il s'agissait d'une fonction depuis n'importe quel autre script.

```js
some_function();
```

Si vous avez besoin de passer des arguments, utilisez le mot clé `argument` suivi d'un nombre correspondant au numéro de l'argument (à partir de zéro).

```js
var local_variable = argument0;
```

Vous pouvez également définir un commentaire de documentation pour indiquer un nom plus parlant au paramètre attendu. Il s'affichera dans l'aide de GameMaker Studio 2.

```js
///@param parameter_name

var parameter_name = argument0;
```

### Scripter les instances

#### Propriétés prédéfinies d'une instance

- `x` : correspond à la position horizontale de l'object. Lecture et écriture.
- `y` : correspond à la position verticale de l'object. Lecture et écriture.
- `id` : correspond au numéro d'identification unique de l'instance de l'object. Lecture seule.
- `v_speed` : correspond à la vitesse horizontale de l'object. Lecture et écriture.
- `h_speed` : correspond à la vitesse verticale de l'object. Lecture et écriture.
- `speed` : correspond à la vitesse de l'object sans direction. Lecture et écriture.
- `direction` : correspond à la direction de mouvement de l'object sous forme d'angle. Lecture et écriture.
- `friction` : correspond à la force de frottement appliquée à de l'object. Lecture et écriture.
- `gravity` : correspond à la force de gravité appliquée à l'object. Lecture et écriture.
- `gravity_direction` : correspond à la direction de la gravité appliquée à l'object. Lecture et écriture.

#### Créer une instance

Pour créer une instance sur un calque spécifique, utilisez la fonction `instance_create_layer`. Elle vous permet de créer une nouvelle instance d'un object sur un calque particulier. Elle prend en argument la position `x` et `y`, le nom d'un calque de la room active (sous forme de chaîne) et le nom de l'object à instancier.

```js
var identifiant_instance = instance_create_layer(position_x, position_y, "nom_calque", nom_objet);
```
Pour créer une instance sur le calque du game object contenant ce script, utilisez la variable prédéfinie `layer`.

```js
var identifiant_instance = instance_create_layer(position_x, position_y, layer, nom_objet);
```

Pour créer une instance sur un nouveau calque (qui n'est pas accessible) à une profondeur donnée (entre -16000 (devant) et 16000 (derrière)), utilisez la fonction `instance_create_depth`.

```js
var identifiant_instance = instance_create_depth(position_x, position_y, profondeur, nom_objet);
```

**Remarque :** Vous pouvez utiliser la variable prédéfine `depth` avec cette fonction.

Ces fonctions renvoie un identifiant unique de l'instance créée.

#### Détruire une instance

La fonction `instance_destroy` vous permet de détruire une instance existante d'un game object. Sans argument, elle détruit l'instance du game object associée à ce script.

```js
instance_destroy(); // détruit l'instance de l'object possédant ce script
```

Elle peut également prendre l'identifiant d'une instance particulière à détruire.

```js
instance_destroy(identifiant_instance);
```

Enfin, elle peut également prendre le nom d'un game object. Dans ce cas, toutes les instances de ce game object sont détruites.

```js
instance_destroy(nom_objet);
```

#### Vérifier si une instance existe

La fonction `instance_exists` vous permet de vérifier si une instance existe bien dans la room.

```js
if (instance_exists(identifiant_instance))
{
    // instructions
}
```

#### Consulter les propriétés d'une instance dans une room

Dans le panneau `Room Editor`, onglet `Instances Layer Properties` ou dans la vue éditeur, double cliquez sur l'instance.

#### Tester si une instance entre en collision avec une autre instance

Utilisez la fonction `place_meeting` qui prend la position à tester et le nom de l'object.

```js
if (place_meeting(position_x, position_y, nom_objet))
{
    // instructions
}
```

#### Déterminer le nombre d'instances d'un object contenues dans une Room

La fonction `instance_number` vous permet de savoir combien d'instances d'un  object spécifique passé en paramètre existent dans la room.

```js
if (instance_number(nom_objet) > limite)
{
    // instructions
}
```

#### Déterminer si une instance est située en dehors de la room

L'évènement `Outside Room` se déclenche lorsqu'une instance sort des limites de la room.

#### Déplacer automatiquement une instance vers un point

La fonction `move_towards_point` (à placer dans un évènement `Create` par exemple) déplace automatiquement une instance vers un point.

- Le premier paramètre correspond à la position horizontale du point vers lequel doit se diriger l'instance.
- Le deuxième paramètre correspond à la position verticale du point vers lequel doit se diriger l'instance.
- Le dernier paramètre correspond à la vitesse à laquelle doit se déplacer l'instance.

```js
move_towards_point(position_x, position_y, vitesse_objet);
```

### Sprites

#### Retourner ou redimensionner un sprite

Les propriétés `image_xscale` et `image_yscale` définissent le taux d'agrandissement du *Sprite*. Utilisez une valeur négative pour retourner le *Sprite* autour de son origine.

#### Propriétés prédéfines des sprites

- `image_alpha` : correspond à l'opacité du sprite (entre 0 et 1). Lecture et écriture.
- `image_blend` : correspond à la teinte à appliquer au sprite sous la forme d'une couleur (par défaut `c_white`). Lecture et écriture.
- `image_index` : correspond à l'indice de l'image à afficher par le sprite. Lecture et écriture.
- `sprite_index` : correspond à l'index du sprite définit dans le dossier `Sprites` du panneau `Resources`. Lecture et écriture.
- `image_xscale` : correspond à l'échelle horizontale du sprite (par défaut 1). Lecture et écriture.
- `_mage_yscale` : correspond à l'échelle verticale du sprite (par défaut 1). Lecture et écriture.
- `image_speed` : correspond à la vitesse de lecture des images composant le sprite. Lecture et écriture.
- `image_width` : correspond à la largeur du sprite. Lecture et écriture.
- `image_height` : correspond à la hauteur du sprite. Lecture et écriture.
- `image_number` : correspond au nombre d'images totales du sprite. Lecture et écriture.
- `sprite_xoffset` : correspond à la distance horizontale de l'origine du sprite par rapport au bord gauche. Cette valeur (en pixels) est relative à la propriété `image_xscale`. Lecture seule.
- `sprite_yoffset` : correspond à la distance verticale de l'origine du sprite par rapport au bord supérieur. Cette valeur (en pixels) est relative à la propriété `image_yscale`. Lecture seule.
- `bbox_left` : correspond à la position horizontale du côté gauche de la boite de collision du sprite par rapport à son origine. Lecture seule.
- `bbox_right` : correspond à la position horizontale du côté droit de la boite de collision du sprite par rapport à son origine. Lecture seule.
- `bbox_top` : correspond à la position verticale du côté supérieur de la boite de collision du sprite par rapport à son origine. Lecture seule.
- `bbox_bottom` : correspond à la position verticale du côté inférieur de la boite de collision du sprite par rapport à son origine. Lecture seule.

**Remarque :** Les propriétés `bbox_left`, `bbox_right`, `bbox_top` et `bbox_bottom` prennent la valeur 1 si l'instance n'a pas de sprite assigné.

#### Dessiner le rectangle de collision

Dans l'évènement `Draw` de l'objet, utilisez la fonction `draw_rectangle` avec les positions de la boîte de collision du sprite.

```js
draw_self();
draw_rectangle(bbox_left, bbox_top, bbox_right, bbox_bottom, true);
```

**Attention !** Pensez à appeler la fonction `draw_self` ou le sprite de l'objet ne s'affichera pas.

### Shaders

```js
shader_set(nom_shader);
draw_self();
shader_reset();
```

Un shader est un programme qui s'exécute sur la carte graphique. GameMaker Studio 2 utilise le langage *GLSL* pour programmer ses shaders.

Il existe deux sortes de shaders.

- Les vertex shaders servent à manipuler la géométrie des images.
- Les fragment shaders servent à manipuler les pixels constituants une image.



```js
void main() {
    // instructions
}
```

[A SUIVRE...]

### Effets de particules

#### Effets prédéfinis

GameMaker Studio propose un ensemble de système de particules simple à mettre en oeuvre.

Crée un effet en dessous d'une instance :

```js
effect_create_below(effet, x, y, taille, couleur);
```

Crée un effet au dessus d'une instance:

```js
effect_create_above(effet, x, y, taille, couleur);
```

- Le paramètre `effet` correspond au type d'élement graphique à utiliser en tant que particule. Peut avoir l'une des valeurs suivantes :
  - `ef_cloud`
  - `ef_ellipse`
  - `ef_explosion`
  - `ef_firework`
  - `ef_flare`
  - `ef_rain`
  - `ef_ring`
  - `ef_smoke`
  - `ef_smokeup`
  - `ef_snow`
  - `ef_spark`
  - `ef_star`
- Le paramètre `x` correspond à la position horizontale de l'effet.
- Le paramètre `y` correspond à la position verticale de l'effet.
- Le paramètre `taille` correspond à la taille des particules de l'effet. Valeur numérique comprise entre 0 et 2.
- Le paramètre `couleur` correspond à la couleur de l'effet. Une constante prédéfinie ou un code numérique spécifique à GameMaker. Utilisez le [color picker](https://chrisanselmo.com/tools/#/gm/color-picker) pour trouver la valeur.

Exemple :

```js
// dans un step event

// déclenche un effet d'explosion lorsque la souris est cliquée
if (mouse_check_button_pressed(mb_left)) {
    effect_create_above(ef_ring, mouse_x, mouse_y, 0.5, c_red);
}

// affiche une pluie en continue en haut de l'écran à une position horizontale entre 0 et 600
var totally_random = irandom_range(0, 600);
effect_create_above(ef_rain, totally_random, 0, 0, c_blue);
```

#### Système de particules personnalisé

##### Système de particule

Créez un système de particules :

```js
systeme_de_particules = part_system_create();
```

##### Création et configuration d'une particule

###### Type de particule

Créez un type de particule :

```js
type_particule = part_type_create();
```

###### Forme prédéfinie

Vous pouvez utiliser des formes prédéfinies :

```js
part_type_shape(type_particule, forme);
```

Le paramètre `forme` peut prendre les valeurs suivantes :

- `pt_shape_pixel` : un pixel 1x1. Par défaut.
- `pt_shape_disk` : Un cercle plein.
- `pt_shape_square` : Un carré plein.
- `pt_shape_line` : Une ligne horizontale de 8 pixels de large.
- `pt_shape_star` : Une étoile pleine à cinq branches.
- `pt_shape_circle` : Un contour de cercle de 3 pixels.
- `pt_shape_ring` : Un cercle avec un reflet intérieur (comme une bulle).
- `pt_shape_sphere` : Un cercle avec un reflet extérieur.
- `pt_shape_flare` : Une étincelle avec un halo.
- `pt_shape_spark` : Une étincelle.
- `pt_shape_explosion` : Une explosion.
- `pt_shape_cloud` : Un nuage.
- `pt_shape_smoke` : Une fumée.
- `pt_shape_snow` : Un flocon de neige.

![Les différentes formes](gms2_particles_shapes.png)

###### Sprite personnalisé

Ou vous pouvez utiliser un sprite personnalisé :

```js
part_type_sprite(type_particule, sprite, animer, etirer, sous_image_aleatoire);
```

Les paramètres sont les suivants :

- `type_particule` : La particule à paramétrer.
- `sprite` : Le nom du sprite à utiliser pour cette particule.
- `animer` : Un booléen pour indiquer si la particule doit utiliser l'animation du sprite (true) ou non (false).
- `etirer` : Un booléen pour indiquer si la particule aligne l'animation du sprite sur la durée de vie de la particule (true) ou non (false).
- `sous_image_aleatoire` : Un booléen pour indiquer si la particule choisit une image de l'animation du sprite au hasard (true) ou non (false). Le paramètre animer doit être false.

###### Durée de vie

Définissez la durée de vie (en steps) de la particule :

```js
part_type_life(type_particule, duree_minimale, duree_maximale);
```

La durée de vie sera définie aléatoirement entre les deux valeurs. Pour définir une durée de vie constante, donnez aux deux paramètres la même valeur.

###### Echelle

Définissez l'échelle horizontale et / ou verticale de la particule :

```js
part_type_scale(type_particule, echelle_x, echelle_y);
```

###### Taille

Définissez la taille de la particule :

```js
part_type_size(type_particule, taille_debut_min, taille_debut_max, variation_fixe, variation_aleatoire);
```

Les paramètres sont les suivants :

- `type_particule` : La particule à paramétrer.
- `taille_debut_min` : Un nombre (positif) indiquant la taille minimale possible de la particule à sa création. `1` par défaut.
- `taille_debut_max` : Un nombre (positif) indiquant la taille maximale possible de la particule à sa création. `1` par défaut.
- `variation_fixe` : Un nombre indiquant la valeur à ajouter à la taille chaque step (peut être une valeur négative).
- `variation_aleatoire` : Un nombre (compris entre `-20` et `20`) indiquant la valeur aléatoire à ajouter à la taille chaque step.

Pour définir une taille initiale constante, donnez la même valeur aux paramètres `taille_debut_min` et `taille_debut_max`.

###### Orientation

Définissez l'orientation de l'image de la particule :

```js
part_type_orientation(type_particule, angle_debut_min, angle_debut_max, variation_fixe, variation_aleatoire, aligner_sur_trajectoire);
```

Les paramètres sont les suivants :

- `type_particule` : La particule à paramétrer.
- `angle_debut_min` : Un nombre indiquant l'angle (en degrés) minimum possible de la particule à sa création. `0` par défaut.
- `angle_debut_max` : Un nombre indiquant l'angle (en degrès) maximum possible de la particule à sa création. `0` par défaut.
- `variation_fixe` : Un nombre indiquant la valeur à ajouter à l'angle chaque step (peut être une valeur négative).
- `variation_aleatoire` : Un nombre (compris entre `-20` et `20`) indiquant la valeur aléatoire à ajouter à l'angle chaque step.
- `aligner_sur_trajectoire` : Un booléen indiquant si la particule doit orienter automatiquement son angle sur sa trajectoire (true) ou non (false).

Pour définir une orientation initiale constante, donnez la même valeur aux paramètres `angle_debut_min` et `angle_debut_max`.

###### Couleur

Définissez la couleur de la particule :

```js
part_type_color1(type_particule, couleur);
part_type_color2(type_particule, couleur_debut, couleur_fin);
part_type_color3(type_particule, couleur_debut, couleur_milieu, couleur_fin);
```

Les différentes versions vous permettent de définir la couleur de la particule durant sa durée de vie.

###### Mélange

Définissez le mélange de la particule avec les autres :

```js
part_type_blend(type_particule, melange);
```

Les paramètres sont les suivants :

- `type_particule` : La particule à paramétrer.
- `melange` : Un booléen indiquant si la particule se mélange ou non avec les autres.

###### Direction

Définissez la direction de la particule :

```js
part_type_direction(type_particule, angle_debut_minimum, angle_debut_maximum, variation_fixe, variation_aleatoire);
```

Les paramètres sont les suivants :

- `type_particule` : La particule à paramétrer.
- `angle_debut_min` : Un nombre indiquant l'angle (de `0` à `359` degrés) minimum possible de la particule à sa création. 0 par défaut.
- `angle_debut_max` : Un nombre indiquant l'angle (de `0` à `359` degrès) maximum possible de la particule à sa création. 0 par défaut.
- `variation_fixe` : Un nombre indiquant la valeur à ajouter à l'angle chaque step (peut être une valeur négative).
- `variation_aleatoire` : Un nombre (compris entre `-20` et `20`) indiquant la valeur aléatoire à ajouter à l'angle chaque step.

Pour définir une direction initiale constante, donnez la même valeur aux paramètres `angle_debut_min` et `angle_debut_max`.

###### Vitesse

Définissez la vitesse de la particule :

```js
part_type_speed(type_particule, vitesse_debut_minimum, vitesse_debut_maximum, variation_fixe, variation_aleatoire);
```

Les paramètres sont les suivants :

- `type_particule` : La particule à paramétrer.
- `vitesse_debut_min` : Un nombre indiquant la vitesse minimale possible de la particule à sa création. `0` par défaut.
- `vitesse_debut_max` : Un nombre indiquant la vitesse maximale possible de la particule à sa création. `0` par défaut.
- `variation_fixe` : Un nombre indiquant la valeur à ajouter à la vitesse chaque step (peut être une valeur négative).
- `variation_aleatoire` : Un nombre (compris entre `-20` et `20`) indiquant la valeur aléatoire à ajouter à la vitesse chaque step.

Pour définir une vitesse initiale constante, donnez la même valeur aux paramètres `vitesse_debut_min` et `vitesse_debut_max`.

###### Force de gravité

Définissez la force de gravité appliquée sur la particule :

```js
part_type_gravity(type_particule, force, direction);
```

Les paramètres sont les suivants :

- `type_particule` : La particule à paramétrer.
- `force` : Un nombre indiquant l'amplitude de la force de gravité à appliquer sur la particule.
- `direction` : Un nombre (entre `0` et `359` degrés) indiquant la direction de la force de gravité à appliquer sur la particule. 270 par défaut.

###### Opacité

Définissez l'opacité de la particule :

```js
part_type_alpha1(type_particule, opacite);
part_type_alpha2(type_particule, opacite_debut, opacite_fin);
part_type_alpha3(type_particule, opacite_debut, opacite_milieu, opacite_fin);
```

Les différentes versions vous permettent de définir l'opacité de la particule durant sa durée de vie.

##### Génération de particules

Après avoir créé un système de particule, créé et  paramétré une particule, vous pouvez générer un effet de particules. Il y a deux méthodes.

###### Génération sur un point

Cette méthode vous permet de générer des particules sur un point précis :

```js
part_particles_create(systeme_de_particules, position_x, position_y, type_particule, quantite);
```

Les paramètres sont les suivants :

- `systeme_de_particules` : Le système de paticules à utiliser pour la génération.
- `position_x` : La position horizontale du point de génération.
- `position_y` : La position verticale du point de génération.
- `type_particule` : Le type de particule à générer.
- `quantite` : Le nombre de particules à générer.

###### Génération dans une région

Cette méthode vous permet de contrôler finement la génération de particules via l'utilisation d'un émetteur.

Commencez par créer un émetteur :

```js
var emetteur = part_emitter_create(systeme_de_particules);
```

Définissez ensuite la région où les particules seront générées. La région est définie par deux points formant un rectangle :

```js
part_emitter_region(systeme_de_particules, emetteur, point_1_position_x, point_1_position_y, point_2_position_x, point_2_position_y, forme, distribution);
```

Les paramètres sont les suivants :

- `systeme_de_particules` : Le système de paticules à utiliser pour la génération.
- `emetteur` : L'émetteur à utiliser pour la génération.
- `point_1_position_x` : La position horizontale du premier point de la région.
- `point_1_position_y` : La position verticale du premier point de la région.
- `point_2_position_x` : La position horizontale du second point de la région.
- `point_2_position_y` : La position verticale du second point de la région.
- `forme` : La forme de la région où aura lieue la génération.
  - `ps_shape_rectangle` : Une forme rectangulaire.
  - `ps_shape_ellipse` : Une forme elliptique.
  - `ps_shape_diamond` : Une forme de losange.
  - `ps_shape_line` : Une ligne droite.
- `distribution` : Le type de distribution des particules générées dans la région.
  - `ps_distr_linear` : Une distribution linéaire où les particules sont réparties .
  - `ps_distr_gaussian` : Une distribution gaussienne où les particules ont plus de chances d'être générées au centre de la région.
  - `ps_distr_invgaussian` : Une distribution gaussienne inversée où les particules ont plus de chances d'être générées sur les bords de la région.

Vous pouvez ensuite générer des particules de deux manières dans la région définie.

La première manière vous permet de générer toutes les particules au même instant comme dans une explosion :

```js
part_emitter_burst(systeme_de_particules, emetteur, type_particule, quantite);
```

Les paramètres sont les suivants :

- `systeme_de_particules` : Le système de paticules à utiliser pour la génération.
- `emetteur` : L'émetteur à utiliser pour la génération.
- `type_particule` : Le type de particule à générer.
- `quantite` : Le nombre de particules à générer.

La seconde manière vous permet de générer les particules en continu :

```js
part_emitter_stream(systeme_de_particules, emetteur, type_particule, quantite);
```

Les paramètres sont les suivants :

- `systeme_de_particules` : Le système de paticules à utiliser pour la génération.
- `emetteur` : L'émetteur à utiliser pour la génération.
- `type_particule` : Le type de particule à générer.
- `quantite` : Le nombre de particules à générer.

##### Cleanup

Une fois que vous avez terminé l'utilisation des particules, vous devez libérer la mémoire.

```js
part_emitter_destroy(emetteur);
part_type_destroy(type_particule);
part_system_destroy(systeme_de_particules);
```

### Exemple de code pour retourner un personnage avec les flèches du clavier

```js
var x_input = keyboard_check(vk_right) - keyboard_check(vk_left);
var y_input = keyboard_check(vk_down) - keyboard_check(vk_up);

if x_input == 0 and y_input == 0 {
	image_index = 0;
	image_speed = 0;
} else {
	image_speed = 0.6;
	if x_input != 0 {
		image_xscale = x_input;	
	}
}
```

### Trouver la doc des variables prédéfinies

`GML Reference -> Instances -> Instance variables`

### Surfaces

- Créez un game object vide et définir les évènements `Create`, `Draw` et `Destroy`.
- Faites glisser le game object dans la Room de votre choix.

Dans l'évènement `Create`, créez la surface :

```js
surface = surface_create(Room_width, Room_height);
```

Dans l'évènement `Destroy`, détruisez la surface :

```js
surface_free(surface);
```

Dans l'évènement `Draw`, affichez la surface :

```js
if (surface_exists(surface))
{
    draw_surface(surface, 0, 0);
}
```

Ensuite, dans l'évènement `Draw` d'un game object, affichez ce que vous voulez :

```js
if (surface_exists(game_object_surface.surface))
{
    // où dessiner
    surface_set_target(game_object_surface.surface);
    //quoi dessiner
    draw_sprite_ext(sprite_index, image_index, x, y, x_scale, y_scale, image_angle, c_white, image_alpha);
    // réinitialiser
    surface_reset_target(game_object_surface.surface);
}
else
{
    // créer une nouvelle surface
    o_surface.surface = surface_create(Room_width, Room_height);
}
```

### Contrôles

#### Souris

##### Masquer le pointeur de la souris

Dans le panneau `Resources`, déployez la section `Options` puis double cliquez sur `Windows`, `macOS` ou `Ubuntu`. Dans la section `Graphics`, décochez l'option `Display cursor`.

##### Position du pointeur

GameMaker Studio 2 définit deux variables prédéfinies (en lecture seule) pour indiquer la position du pointeur de la souris. Elle peuvent être utilisées sur des appareils tactiles dans le cas de touchers uniques.

- `mouse_x` contient la coordonnée X de la souris dans la room.
- `mouse_y` contient la coordonnée Y de la souris dans la room.

##### Appui d'un bouton de souris

GameMaker Studio 2 fournit trois fonctions pour vérifier si un bouton de souris est enfoncé ou non.

- La fonction `mouse_check_button_pressed` renvoie un booléen indiquant si un bouton de souris vient d'être cliqué. Equivalent à l'évènement `Mouse -> X Pressed`.
- La fonction `mouse_check_button_released` renvoie un booléen indiquant si un bouton de souris vient d'être relâché. Equivalent à l'évènement `Mouse -> X Released`.
- La fonction `mouse_check_button` renvoie un booléen indiquant si un bouton de souris est cliqué.  Equivalent à l'évènement `Mouse -> X Down`.

##### Constantes prédéfinies liées à la souris

Les fonctions précédents prennent en argument une des constantes prédéfinies par GameMaker Studio 2.

- `mb_left` correspond au bouton gauche de la souris.
- `mb_middle` correspond au bouton du milieu de la souris.
- `mb_right` correspond au bouton droit de la souris.
- `mb_none` correspond à aucun bouton de la souris.
- `mb_any` correspond à n'importe quel bouton de la souris.

#### Clavier

#### Appui d'une touche du clavier

GameMaker Studio 2 fournit trois fonctions pour vérifier si une touche du clavier est enfoncée ou non.

- La fonction `keyboard_check_button_pressed` renvoie un booléen indiquant si une touche du clavier vient d'être enfoncée. Equivalent à l'évènement `Key Pressed -> X`.
- La fonction `keyboard_check_button_released` renvoie un booléen indiquant si une touche du clavier vient d'être relâché. Equivalent à l'évènement `Key Up -> X`.
- La fonction `keyboard_check_button` renvoie un booléen indiquant si une touche du clavier est enfoncée. Equivalent à l'évènement `Key Down -> X`.

##### Constantes prédéfinies liées au clavier

Les fonctions précédents prennent en argument une des constantes prédéfinies par GameMaker Studio 2.

- `vk_nokey` correspond à aucune touche du clavier.
- `vk_anykey` correspond à n'importe quelle touche du clavier.
- `vk_left` correspond à la touche flèche gauche du clavier.
- `vk_right` correspond à la touche flèche droite du clavier.
- `vk_up` correspond à la touche flèche haute du clavier.
- `vk_down` correspond à la touche flèche basse du clavier.
- `vk_enter` correspond à la touche `Entrée` du clavier.
- `vk_escape` correspond à la touche `Echap` du clavier.
- `vk_space` correspond à la touche `Espace` du clavier.
- `vk_shift` correspond à une des touches `Shift` du clavier.
- `vk_control` correspond à une des touches `Control` du clavier.
- `vk_alt` correspond à la touche `Alt` du clavier.
- `vk_backspace` correspond à la touche `Del` du clavier.
- `vk_tab` correspond à la touche `Tab` du clavier.
- `vk_home` correspond à la touche `Home` du clavier.
- `vk_end` correspond à la touche `Fin` du clavier.
- `vk_delete` correspond à la touche `Suppr` du clavier.
- `vk_insert` correspond à la touche `Inser` du clavier.
- `vk_pageup` correspond à la touche PageHaut` du clavier.
- `vk_pagedown` correspond à la touche `PageBas` du clavier.
- `vk_pause` correspond à la touche `Pause` du clavier.
- `vk_printscreen` correspond à la touche `Impécr` du clavier.
- `vk_f1` ... `vk_f12` correspond à l'une des touches de fonction du clavier (`F1` à `F12`).
- `vk_numpad0` ... `vk_numpad9` correspond à l'une des touches du pavé numérique du clavier (`0` à `9`).
- `vk_multiply` correspond à la touche `*` du pavé numérique du clavier.
- `vk_divide` correspond à la touche `/` du pavé numérique du clavier.
- `vk_add` correspond à la touche `+` du pavé numérique du clavier.
- `vk_subtract` correspond à la touche `-` du pavé numérique du clavier.
- `vk_decimal` correspond à la touche `.` du pavé numérique du clavier.

##### Touches alphanumériques du clavier

GameMaker Studio 2 ne définit pas de constante prédéfinie pour les touches alphanumériques du clavier (`A` à `Z` et `0` à `9`). Pour désigner une touche alphanumérique, utiliser la fonction `ord` en lui passant en argument une chaîne contenant la lettre en majuscule ou le chiffre de la touche correspondante.

```js
if (keyboard_check_button(ord("A"))) {
	// instructions
}
```

**Remarque :** Normalement, la fonction `ord` convertit une chaîne en une version *UTF-8* mais pour la gestion du clavier, on lui passe une seule lettre majuscule ou un seul chiffre.

##### Associer une touche du clavier à une autre

La fonction `keyboard_set_map` vous permet d'associer une touche du clavier à une autre. Cela vous permet de combiner plusieurs touches du clavier à un seul évènement et cela vous évite de dupliquer du code. Enfin, cela évite que plusieurs évènements se déclenchent et exécutent plusieurs fois le même code. Le premier paramètre correspond à une touche réelle du clavier (accessible via la fonction `ord` qui prend en paramètre une chaîne correspondant à une touche). Le dernier paramètre correspond à une constante associée à une touche du clavier virtuel.

```js
keyboard_set_map(ord("W"), vk_up);
```

#### Gamepads

Documentation *GameMaker* sur les gamepads : `Scripting -> GML Reference -> Controls -> Gamepad Input`.

GameMaker ne fournit pas d'évènement dédié aux gamepads. Vous devez donc gérer manuellement les contrôles dans un évènement `Step`. Vous pouvez gérer jusqu'à quatre gamepads XInput (manettes Xbox 360 et compatibles) et jusqu'à huit gamepads DirectInput (autres modèles).

##### Vérifier si la plateforme cible prend en charge les gamepads

Certaines plateformes cibles peuvent ne pas prendre en charge les gamepads. Pour le déterminez, utilisez la fonction `gamepad_is_supported`. Elle renvoie un booléen indiquant si les gamepads sont pris en charge. 

```js
if (gamepad_is_supported()) {
    // instructions
}
```

##### Vérifier si un gamepad est connecté

La fonction `gamepad_is_connected` renvoie un booléen indiquant si un gamepad est connecté au moment de l'appel. Vous devez lui passer en paramètre l'indice (commençant à 0) d'un gamepad. Appelez cette fonction avant de gérer les contrôles d'un gamepad.

```js
if (gamepad_is_connected(indice_gamepad))
{
    // instructions
}
```

L'`indice_de_gamepad` commence à `0`. Les indices de `0` à `3` sont dédiés aux gamepads XInput. Les indices de `4` à `11` sont dédiés aux gamepads DirectInput.

###### Obtenir le nombre de gamepads connectés

Selon la plateforme, la fonction `gamepad_get_device_count` renvoie soit le nombre de gamepads connectés, soit le nombre de gamepads que l'on peut connecté à l'appareil. C'est pourquoi il est conseillé d'utiliser cette fonction en conjonction avec la fonction `gamepad_is_connected`. Elle ne prend pas de paramètre.

```js
var nombre_gamepads = gamepad_get_device_count();
for (var i = 0; i < nombre_gamepads; i++) {
    global.gamepad[i] = gamepad_is_connected(i);
}
```

###### Obtenir l'intitulé du gamepad

Chaque gamepad possède une chaîne de caractères décrivant son modèle. Vous pouvez accéder à cette information en utilisant la fonction `gamepad_get_description`. Elle prend en paramètre l'indice du gamepad à accéder.

```js
var modele_gamepad = gamepad_get_description(indice_gamepad);
```

###### Obtenir le GUID du gamepad

Chaque gamepad se voit associé un numéro de série unique sur la plateforme à laquelle il est connecté. Vous pouvez obtenir ce numéro sous la forme d'une chaîne de caractères en utilisant la fonction `gamepad_get_guid`. Elle prend en paramètre l'indice du gamepade à accéder.

```js
var gamepad_GUID = gamepad_get_guid(indice_gamepad);
```

- Si le gamepad n'est pas connecté ou si le numéro est inaccessible, la fonction renvoie `"none"`.
- Si l'indice passé n'est pas dans la limite prise en charge par la plateforme, la fonction renvoie `"device index out of range"`.

Cette fonction est souvent utilisée en conjonction avec la fonction `gamepad_get_description` pour remapper les boutons d'un gamepad.

###### Obtenir le nombre de directions

La fonction `gamepad_hat_count` renvoie le nombre de directions (*hats*) fournies par un gamepad DirectInput. Elle prend en paramètre l'indice du gamepad à accéder.

```js
var nombre_direction_gamepad = gamepad_hat_count(indice_gamepad);
```

**Attention !** Cette fonction n'est disponible que pour les gamepads DirectInput. Vous ne pouvez donc utiliser qu'un indice de gamepad compris entre `4` et `11`.

###### Obtenir la valeur d'une direction

La fonction `gamepad_hat_value` renvoie la valeur (entre `0` et `1`) d'une direction (*hat*) d'un gamepad Directinput. Elle prend en paramètre :

- L'indice du gamepad à accéder.
- Un masque de bit correspondant à une ou plusieurs directions (vous pouvez combiner plusieurs directions).
  - `1` (motif binaire `0001`) pour haut
  - `2` (motif binaire `0010`) pour droite
  - `4` (motif binaire `0100`) pour bas
  - `8` (motif binaire `1000`) pour gauche

```js
var valeur_direction = gamepad_hat_value(indice_gamepad, masque_bit_direction);
```

##### Sticks analogiques

###### Obtenir le nombre d'axes disponibles

La fonction `gamepad_axis_count` renvoie le nombre d'axes disponibles sur le gamepad. Le paramètre correspond à l'indice du gamepad. Sur un gamepad classique à deux sticks analogiques, le nombre d'axes disponible est de quatre.

```js
if (gamepad_axis_count(indice_gamepad) == 4) {
    // instructions
}
```

###### Obtenir la valeur d'un axe

La fonction `gamepad_axis_value` renvoie la valeur d'un axe de stick d'un gamepad.

- Le premier paramètre correspond à l'indice du gamepad.
- Le second paramètre correspond à l'indice de l'axe à accéder. En général, vous utiliserez les quatre constantes prédéfinies associées à une direction d'un des deux sticks possibles mais pour des gamepads plus "exotiques", vous pouvez également utiliser un indice compris entre `0` et `gamepad_axis_count(indice_gamepad) - 1`.
  - `gp_axislh` pour stick gauche direction horizontale.
  - `gp_axislv` pour stick gauche direction verticale.
  - `gp_axisrh` pour stick droit direction horizontale.
  - `gp_axisrv` pour stick droit direction verticale).


```js
if (gamepad_is_connected(indice_gamepad))
{
    var stickGaucheHorizontal = gamepad_axis_value(indice_gamepad, gp_axislh);
    var stickGaucheVertical = gamepad_axis_value(indice_gamepad, gp_axislv);
    var stickDroitHorizontal = gamepad_axis_value(indice_gamepad, gp_axisrh);
    var stickDroitVertical = gamepad_axis_value(indice_gamepad, gp_axisrv);
}
```

###### Obtenir la zone morte des axes

La fonction `gamepad_get_axis_deadzone` renvoie la valeur de la zone morte des axes d'un gamepad. elle prend en paramètre l'indice du gamepad à accéder.

```js
var zone_morte_axes = gamepad_get_axis_deadzone(indice_gamepad);
```

###### Définir la zone morte des axes

Un stick au repos n'a jamais de valeur horizontale et verticale totalement nulle. Pour éviter de gérer ces valeurs parasites, la fonction `gamepad_set_axis_deadzone` vous permet de paramétrer la zone morte des sticks d'un gamepad. Placez-la dans un évènement `Create` et passez-lui comme argument l'indice du gamepad et une valeur limite comprise en `0` et `1` (`0.2` par exemple). Les valeurs comprises entre `0` et cette limite seront considérées comme nulles.

```js
if (gamepad_get_axis_deadzone(indice_gamepad) > valeur) {
    gamepad_set_axis_deadzone(indice_gamepad, valeur);
}
```

Vous pouvez également traiter les sticks analogiques comme de simples boutons (pour un déplacement sur huit directions par exemple). consultez la section suivante pour ce genre d'utilisation.

##### Boutons et croix de direction

###### Obtenir le nombre de boutons

La fonction `gamepad_button_count` renvoie le nombre de boutons dont dispose un gamepad.

```js
var nombre_boutons_gamepad = gamepad_button_count(indice_gamepad);
```

###### Obtenir l'état des boutons

La fonction `gamepad_button_check_` renvoie un booléen indiquant si un bouton est enfoncé dans le step actuel.
La fonction `gamepad_button_check_pressed` renvoie un booléen indiquant si un bouton vient d'être enfoncé dans le step actuel.
La fonction `gamepad_button_check_released` renvoie un booléen indiquant si un bouton vient d'être relâché dans le step actuel.

Ces fonctions prennent en paramètres :

- l'indice du gamepad.
- Une constante prédéfinie correspondant à un bouton de gamepad :
  - `gp_padl` correspond à la direction gauche de la croix directionnelle.
  - `gp_padr` correspond à la direction droite de la croix directionnelle.
  - `gp_padu` correspond à la direction haute de la croix directionnelle.
  - `gp_padd` correspond à la direction basse de la croix directionnelle.
  - `gp_axislh` correspond à la direction horizontale du stick gauche.
  - `gp_axislv` correspond à la direction verticale du stick gauche.
  - `gp_axisrh` correspond à la direction horizontale du stick droit.
  - `gp_axisrv` correspond à la direction verticale du stick droit.
  - `gp_stickl` correspond au clic du stick gauche.
  - `gp_stickr` correspond au clic du stick droit.
  - `gp_select` correspond au bouton *Select*.
  - `gp_start` correspond au bouton *Start*.
  - `gp_face1` correspond au bouton *A* d'une manette Xbox (bas).
  - `gp_face2` correspond au bouton *B* d'une manette Xbox (droite).
  - `gp_face3` correspond au bouton *X* d'une manette Xbox (gauche).
  - `gp_face4` correspond au bouton *Y* d'une manette Xbox (haut).
  - `gp_shoulderl` correspond au bouton *LB* d'une manette Xbox (L1).
  - `gp_shoulderlb` correspond au bouton *LT* d'une manette Xbox (L2).
  - `gp_shoulderr` correspond au bouton *RB* d'une manette Xbox (R1).
  - `gp_shoulderrb` correspond au bouton *RT* d'une manette Xbox (R2).

![gamepad et constantes associées](gms2_gamepad_constants.png)

```js
if (gamepad_is_connected(0))
{
    var padLeftPressed = gamepad_button_check_pressed(0, gp_padl);
    var padRightPressed = gamepad_button_check_pressed(0, gp_padr);
    var padUpPressed = gamepad_button_check_pressed(0, gp_padu);
    var padDownPressed = gamepad_button_check_pressed(0, gp_padd);
    var leftStickHorizontalPressed = gamepad_button_check_pressed(0, gp_axislh);
    var leftStickVerticalPressed = gamepad_button_check_pressed(0, gp_axislv);
    var rightStickHorizontalPressed = gamepad_button_check_pressed(0, gp_axisrh);
    var rightStickVerticalPressed = gamepad_button_check_pressed(0, gp_axisrv);
    var leftStickClicked = gamepad_button_check_pressed(0, gp_stickl);
    var rightStickClicked = gamepad_button_check_pressed(0, gp_stickr);
    var selectPressed = gamepad_button_check_pressed(0, gp_select);
    var startPressed = gamepad_button_check_pressed(0, gp_start);
    var buttonAPressed = gamepad_button_check_pressed(0, gp_face1);
    var buttonBPressed = gamepad_button_check_pressed(0, gp_face2);
    var buttonXPressed = gamepad_button_check_pressed(0, gp_face3);
    var buttonYPressed = gamepad_button_check_pressed(0, gp_face4);
    var buttonLbPressed = gamepad_button_check_pressed(0, gp_shoulderl);
    var buttonLtPressed = gamepad_button_check_pressed(0, gp_shoulderlb);
    var buttonRbPressed = gamepad_button_check_pressed(0, gp_shoulderr);
    var buttonRtPressed = gamepad_button_check_pressed(0, gp_shoulderrb);
}
```

###### Obtenir la zone morte des boutons analogiques

La fonction `gamepad_get_button_threshold` renvoie la zone morte (entre `0` et `1`) des boutons analogiques. Cette valeur définit la limite de la valeur des boutons analogiques qui doit être dépassée pour que le bouton soit considéré comme enfoncé. La valeur par défaut est de `0.5`. Cette fonction prend en paramètre l'indice du gamepad à accéder.

```js
var zone_morte_boutons = gamepad_get_button_threshold(indice_gamepad);
```

###### Définir la zone morte des boutons analogiques

La fonction `gamepad_set_button_threshold` définit la zone morte des boutons analogiques. Elle prend en paramètres :

- L'indice du gamepad à paramétrer.
- La valeur de la zone morte (entre `0` et `1`).

```js
gamepad_set_button_threshold(indice_gamepad, zone_morte_boutons);
```

###### Obtenir la valeur des boutons analogiques

La fonction `gamepad_button_value` renvoie la valeur (entre `0` et `1`) d'un bouton analogique. Elle prend en paramètres :

- l'indice du gamepad.
- Une constante prédéfinie correspondant à un bouton de gamepad.

```js
gamepad_button_value(device, button);
```

##### Simuler l'appui d'une touche du clavier

Pour combiner la gestion du gamepad avec une gestion du clavier, vous pouvez simuler l'appui d'une touche du clavier avec la fonction `keyboard_key_press`.

```js
if (buttonAPressed)
{
    keyboard_key_press(vk_space);
    keyboard_key_release(vk_space);
}
```

**Attention !** Cette fonction simule l'appui d'une touche de manière permanente. Pensez à appeler aussitôt la fonction `keyboard_key_release` pour simuler le relâchement de la touche.

###### Contrôler la vibration

La fonction `gamepad_set_vibration` vous permet de contrôler la quantité de vibration des moteurs droit et gauche d'un gamepad. Elle prend en paramètres :

- L'indice du gamepad.
- L'intensité de la vibration (une valeur entre `0` (pas de vibration) et `1` (vibration maximale)) du moteur gauche.
- L'intensité de la vibration (une valeur entre `0` (pas de vibration) et `1` (vibration maximale)) du moteur droit.

```js
gamepad_set_vibration(indice_gamepad, vibration_moteur_gauche, vibration_moteur_droit);
```

**Remarque :** Cette fonction actionne les moteurs de vibration du gamepad de manière continue. Pensez à remettre à zéro l'intensité de vibration des moteurs après usage pour stopper la vibration.

**Attention !** Cette fonction n'est prise en charge que pour les plateformes Windows, PS4 et XBox One.

##### Définir la couleur des LEDS du gamepad PS4

La fonction `gamepad_set_colour` vous permet d'attribuer une couleur aux LEDs d'une manette PS4.

```js
gamepad_set_colour(indice_gamepad, couleur);
```

###### Fonctions avancées

Les fonctions suivantes sont relativement complexes et je ne les maîtrise pas bien. Pour plus d'informations, consultez la documentation officielle.

La fonction `gamepad_get_mapping` renvoie une chaîne de caractères contenant les informations de mapping des touches d'un gamepad.

```js
var mapping_gamepad = gamepad_get_mapping(indice_gamepad);
```

La fonction `gamepad_remove_mapping` supprime le mapping actuel des touches d'un gamepad.

```js
gamepad_remove_mapping(indice_gamepad);
```

La fonction `gamepad_test_mapping` vous permet de modifier le mapping des touches d'un gamepad.

```js
gamepad_test_mapping(indice_gamepad, chaine_nouveau_mapping);
```

La fonction `gamepad_get_option` renvoie l'information d'une option spécifique. Elle prend en paramètres :

- L'indice du gamepad.
- Un nom d'option (sous forme de chaîne de caractères) parmi :
  - "allow_rotation".
  - "dpad_absolute".

```js
gamepad_get_option(indice_gamepad, nom_option);
```

La fonction `gamepad_set_option` modifie l'information d'une option spécifique. Elle prend en paramètres :

- L'indice du gamepad.
- Un nom d'option (sous forme de chaîne de caractères) parmi :
  - "allow_rotation".
  - "dpad_absolute".
  - La valeur à attribuer à l'option.

```js
gamepad_set_option(indice_gamepad, nom_option, valeur);
```

### Génération aléatoire

Par défaut, GameMaker Studio 2 génère des nombres aléatoire avec la même graine (*seed*). Cela produit à chaque exécution du jeu la même suite de valeurs. Pour réellement générer des suites de nombres aléatoires, appelez la fonction `randomize` (ou `randomise`) avant d'utiliser les fonctions suivantes.

```js
randomize();
```

La fonction `random` avec un argument génère un nombre à virgule compris entre 0 et le paramètre (non inclus).

```js
random_number = random(20); // génère un nombre entre 0 et 19.99999
```

La fonction `irandom` avec un argument entier génère un nombre entier compris entre 0 et le paramètre (inclus).

```js
random_number = irandom(20); // génère un nombre entier entre 0 et 20
```

La fonction `irandom_range` prend deux entiers en arguments et génère un nombre entier compris entre le premier argument et le second (inclus).

```js
random_number = irandom_range(10, 20); // génère un nombre entre 10 et 20
```

La fonction `choose` prend une suite d'arguments et renvoie aléatoirement un de ces arguments.

```js
prenom_aleatoire = choose("Sophie", "Sonia", "Marie", "Audrey", "Laetitia", "Dana");
```

### Scripting associé aux rooms

#### Dimensions d'une room

Les variables prédéfinies `room_width` et `room_height` vous permettent de connaître les dimensions de la room en cours.

```js
random_x = irandom_range(0, room_width);
random_y = irandom_range(0, room_height);
```

#### Ajouter du code à une room

Ouvrez la room à éditer. Dans le panneau `Properties`, cliquez sur le bouton `Creation Code` pour ouvrir le script associé à une room. Vous pouvez par exemple utilisez la fonction `audio_play_sound`.

#### Organisation des rooms

GameMaker Studio 2 gère les rooms en leur associant un indice selon leur organisation dans le panneau `Resources`. Dans ce panneau, vous pouvez déplacer les différentes rooms par cliquer-glisser. Si vous cliquez-glissez une room sur une autre, cette dernière s'illumine différemment selon la position du pointeur de la souris.

- Si le pointeur de la souris est sur la partie supérieure de la room, la room glissée sera placée au dessus de la room située sous le pointeur de souris.
- Si le pointeur de la souris est sur la partie inférieure de la room, la Room glissée sera placée au dessous de la room située sous le pointeur de souris.
- Si le pointeur de la souris est sur la partie centrale de la room, la room glissée deviendra un enfant de la room située sous le pointeur de souris. Elle héritera de ses propriétés.

- La variable prédéfinie `room` contient l'indice associé à la room actuelle (en cours d'exécution).
- La variable prédéfinie `room_first` contient l'indice associé à la première Room dans la liste du panneau `Resources`.
- La variable prédéfinie `room_last` contient l'indice associé à la dernière Room dans la liste du panneau `Resources`.

La fonction `room_exist` prend un indice en paramètre et renvoie une booléen indiquant si une room associé à l'indice existe bien ou non.

```js
if (room_exist(indice_de_room))
{
    room_goto(indice_de_room);
}
```

La fonction `room_next` prend un indice de room en paramètre et renvoie l'indice de la room suivante ou `-1` s'il n'y a pas de room suivante.

```js
if (room_next(room) != -1)
{
    room_goto_next();
}
```

La fonction `room_previous` prend un indice de room en paramètre et renvoie l'indice de la room précédente ou `-1` s'il n'y a pas de room précédente.

```js
if (room_previous(room) != -1)
{
    room_goto_previous();
}
```

La fonction `room_restart` redémarre la room actuelle comme si elle venait de se charger.

```js
room_restart();
```

**Remarque :** Cette instruction prend effet une fois que l'évènement qui la contient se termine. Le script exécute donc les instructions qui suivent avant de redémarrer l'écran de jeu.

La fonction `room_goto` vous permet de passer à une room spécifique en passant l'indice associé à une room en paramètre.

```js
room_goto(indice_de_room);
```

La fonction `room_goto_next` vous permet de passer à la room suivant celle actuelle dans le panneau `Resources`. Vérifiez qu'une room existe bien après celle actuelle avant d'appeler cette fonction ou une erreur se produira.

```js
if (room_exists(room_next(room)))
{
    room_goto_next();
}
```

La fonction `room_goto_previous` vous permet de passer à la room précédant celle actuelle dans le panneau `Resources`. Vérifiez qu'une room existe bien avant celle actuel avant d'appeler cette fonction ou une erreur se produira.

```js
if (room_exists(room_previous(room)))
{
    room_goto_previous();
}
```

### Sons et musiques

#### Lecture

La fonction `audio_play_sound` vous permet de lancer la lecture d'un son ou d'une musique.  Elle renvoie un entier correspondant à un indice associé au son lu.

```js
audio_play_sound(nom_de_son, priorite, lecture_en_boucle);
```

- Le premier paramètre est le nom du son ou de la musique à jouer.
- Le deuxième paramètre est un entier indiquant la priorité du son.
- Le dernier paramètre est un booléen indiquant si le son ou la musique doit jouer en boucle ou non.

```js
indice_de_son = audio_play_sound(nom_de_son, 1, true);
```

#### Vérifier qu'un son est en lecture

La fonction `audio_is_playing` renvoie un booléen indiquant si un son est en lecture. Elle prend en argument le nom de la ressource de type `Sound` à tester.

#### Modifier le gain

La fonction `audio_sound_gain` vous permet de faire une interpolation sur le gain (l'amplitude) d'un son en lecture.

- Le premier paramètre correspond à l'indice associé à un son lu.
- Le deuxième paramètre est un nombre compris entre 0 et 1 et il correspond au nouveau gain à atteindre depuis le gain actuel.
- Le dernier paramètre indique la durée de l'interpolation en millisecondes.

```js
audio_sound_gain(indice_de_son, gain_cible, duree);
```

**Remarque :** Pour changer le gain instantannément, donnez une durée de 0.

### Dessin

Utilisez les fonctions de dessin dans un évènement `Draw` d'un object si vous souhaitez dessiner directement dans la room ou `Draw GUI` si vous souhaitez dessiner sur une surface qui suit un viewport de caméra (vous n'aurez donc pas besoin de calculer le décalage de la caméra par rapport à la room).

Avant toute chose, si l'object contient un sprite à afficher, appelez la fonction `draw_self` sinon le sprite ne s'affichera pas.

```js
draw_self();
```

#### Définir la couleur de dessin

La fonction `draw_set_color` vous permet de définir la couleur à utiliser pour les fonctions de dessin suivantes. La couleur par défaut est blanche.

```js
draw_set_colour(couleur);
```

#### Couleurs

La fonction `make_colour_rgb` renvoie un entier correspondant à une couleur. Elle prend trois arguments correspondant aux composantes rouge, verte et bleue (une valeur comprise entre 0 et 255) d'une couleur.

```js
var couleur = make_colour_rgb(rouge, vert, bleu);
```

**Remarque :** Il existe également la fonction `make_colour_hsv` qui fonctionne de la même manière que la fonction précédente mais dont les arguments correspondent à la teinte, la saturation et la luminosité d'une couleur.

```js
var couleur = make_colour_hsv(teinte, saturation, luminosite);
```

Vous pouvez également utiliser la notation hexadécimale pour représenter une couleur en faisant précéder la valeur du signe `$`.

```js
var couleur = $FFFFFF.
```

**Attention !** Contrairement aux notations habituelles, cette notation est inversée. D'abord bleu, puis vert et enfin rouge.

##### Couleurs prédéfinies

GameMaker Studio 2 propose un ensemble de constantes prédéfinies pour représenter des couleurs usuelles.

- `c_aqua`
- `c_black`
- `c_blue`
- `c_dkgray`
- `c_fuchsia`
- `c_gray`
- `c_green`
- `c_lime`
- `c_ltgray`
- `c_maroon`
- `c_navy`
- `c_olive`
- `c_orange`
- `c_purple`
- `c_red`
- `c_silver`
- `c_teal`
- `c_white`
- `c_yellow`


```js
draw_set_font(font_hud);
draw_set_halign(fa_center);
draw_set_colour(c_black);
draw_text(250, 280, "Highscore: " + string(global.highscore));
```

#### Dessiner un sprite

La fonction `draw_sprite` affiche un Sprite.

- Le premier paramètre correspond au Sprite à afficher.
- Le deuxième paramètre correspond à l'indice de l'image de l'animation du Sprite à afficher. Si c'est une image fixe, passez la valeur `0`.
- Le troisième paramètre correspond à la position horizontale où afficher le Sprite.
- Le dernier paramètre correspond à la position verticale où afficher le Sprite.

```js
draw_sprite(nom_sprite, indice, position_x, position_y);
```

La fonction `draw_sprite_ext` affiche un Sprite. Elle possède plus de paramètres que la fonction précédente.

- Le premier paramètre correspond au Sprite à afficher.
- Le deuxième paramètre correspond à l'indice de l'image de l'animation du Sprite à afficher. Si c'est une image fixe, passez la valeur `0`.
- Le troisième paramètre correspond à la position horizontale où afficher le Sprite.
- Le quatrième paramètre correspond à la position verticale où afficher le Sprite.
- Le cinquième paramètre correspond à l'échelle horizontale du Sprite.
- Le sixième paramètre correspond à l'échelle verticale du Sprite.
- Le septième paramètre correspond à l'angle d'inclinaison du Sprite.
- Le huitième paramètre correspond à la teinte à attribuer au Sprite.
- Le dernier paramètre correspond à la transparence du Sprite.

```js
draw_sprite_ext(nom_sprite, indice, position_x, position_y, echelle_x, echelle_y, angle, couleur, alpha);
```

#### Dessiner une barre de vie

La fonction `draw_healthbar` affiche une barre de vie. Elle doit être utilisée dans les évènements `Draw`.

- Le premier paramètre correspond à la position gauche du rectangle de la barre de vie.
- Le deuxième paramètre correspond à la position haute du rectangle de la barre de vie.
- Le troisième paramètre correspond à la position droite du rectangle de la barre de vie.
- Le quatrième paramètre correspond à la position basse du rectangle de la barre de vie.
- Le cinquième paramètre correspond à la quantité de vie (de 0 à 100).
- Le sixième paramètre correspond à la couleur arrière.
- Le septième paramètre correspond à la couleur de la valeur minimale.
- Le huitième paramètre correspond à la couleur de la valeur maximale.
- Le neuvième paramètre correspond à la direction d'ancrage de la barre de vie.
  - `0` indique que la barre de vie est alignée à gauche.
  - `1` indique que la barre de vie est alignée à droite.
  - `2` indique que la barre de vie est alignée en haut.
  - `3` indique que la barre de vie est alignée en bas.
- Le dixième paramètre définit si la couleur arrière doit être visible (`true`) ou si la barre de vie doit être transparente (`false`).
- Le onzième paramètre définit si une bordure noire de un pixel d'épaisseur doit être visible (`true`) ou non (`false`).

```js
var pourcent_vie = (vie_actuelle / vie_max) * 100;
draw_healthbar(
    position_gauche,
    position_haute,
    position_droite,
    position_basse,
    pourcent_vie,
    couleur_arrière,
    couleur_valeur_minimale,
    couleur_valeur_maximale,
    direction_ancrage,
    couleur_arrière_visible,
    couleur_bordure_visible
    );
```

### Techniques d'animation automatique

#### Interpolation linéaire

La fonction `lerp` vous permet d'effectuer une interpolation linéaire entre deux valeurs. Le premier paramètre est la valeur minimale. Le deuxième paramètre est la valeur maximale. Le troisième paramètre est une nombre compris entre 0 et 1. Si cette valeur est 0, la fonction renvoie la valeur minimale. Si cette valeur est 1, la fonction renvoie la valeur maximale. Si c'est une valeur quelconque, la fonction renvoie une valeur proportionnelle relative à la valeur minimale et la valeur maximale.

Utiliser cette fonction pour déplacer une élément vers un point permet de faire ralentir progressivement l'objet à mesure qu'il se rapproche de l'objectif.

```js
x = lerp(x, objectif_x, 0.1)
y = lerp(y, objectif_y, 0.1)
```

#### Easing

SECTION A RETRAVAILLER

```js
#define Default_Ease_Algorithms
/*
* TERMS OF USE - EASING EQUATIONS
* Open source under the BSD License.
* Copyright (c)2001 Robert Penner
* All rights reserved.
* Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:
* Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
* Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
* Neither the name of the author nor the names of contributors may be used to endorse or promote products derived from this software without specific prior written permission.
* THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
*/

ease-linear #define EaseLinear
/// EaseLinear(inputvalue,outputmin,outputmax,inputmax)

return argument2 * argument0 / argument3 + argument1;


ease-inquad #define EaseInQuad
/// EaseInQuad(inputvalue,outputmin,outputmax,inputmax)

argument0 /= argument3;
return argument2 * argument0 * argument0 + argument1;


ease-outquad #define EaseOutQuad
/// EaseOutQuad(inputvalue,outputmin,outputmax,inputmax)

argument0 /= argument3;
return -argument2 * argument0 * (argument0 - 2) + argument1;


ease-inoutquad #define EaseInOutQuad
/// EaseInOutQuad(inputvalue,outputmin,outputmax,inputmax)

argument0 /= argument3 * 0.5;

if (argument0 < 1)
{
    return argument2 * 0.5 * argument0 * argument0 + argument1;
}

return argument2 * -0.5 * (--argument0 * (argument0 - 2) - 1) + argument1;


ease-incubic #define EaseInCubic
/// EaseInCubic(inputvalue,outputmin,outputmax,inputmax)

return argument2 * power(argument0/argument3, 3) + argument1;


ease-outcubic #define EaseOutCubic
/// EaseOutCubic(inputvalue,outputmin,outputmax,inputmax)

return argument2 * (power(argument0/argument3 - 1, 3) + 1) + argument1;


ease-inoutcubic #define EaseInOutCubic
/// EaseInOutCubic(inputvalue,outputmin,outputmax,inputmax)

argument0 /= argument3 * 0.5;

if (argument0 < 1)
{
   return argument2 * 0.5 * power(argument0, 3) + argument1;
}

return argument2 * 0.5 * (power(argument0 - 2, 3) + 2) + argument1;


ease-inquart #define EaseInQuart
/// EaseInQuart(inputvalue,outputmin,outputmax,inputmax)

return argument2 * power(argument0 / argument3, 4) + argument1;


ease-outquart #define EaseOutQuart
/// EaseOutQuart(inputvalue,outputmin,outputmax,inputmax)

return -argument2 * (power(argument0 / argument3 - 1, 4) - 1) + argument1;


ease-inoutquart #define EaseInOutQuart
/// EaseInOutQuart(inputvalue,outputmin,outputmax,inputmax)

argument0 /= argument3 * 0.5;

if (argument0 < 1) 
{
    return argument2 * 0.5 * power(argument0, 4) + argument1;
}

return argument2 * -0.5 * (power(argument0 - 2, 4) - 2) + argument1;


ease-inquint #define EaseInQuint
/// EaseInQuint(inputvalue,outputmin,outputmax,inputmax)

return argument2 * power(argument0 / argument3, 5) + argument1;


ease-outquint #define EaseOutQuint
/// EaseOutQuint(inputvalue,outputmin,outputmax,inputmax)

return argument2 * (power(argument0 / argument3 - 1, 5) + 1) + argument1;


ease-inoutquint #define EaseInOutQuint
/// EaseInOutQuint(inputvalue,outputmin,outputmax,inputmax)

argument0 /= argument3 * 0.5;

if (argument0 < 1)
{
    return argument2 * 0.5 * power(argument0, 5) + argument1;
}

return argument2 * 0.5 * (power(argument0 - 2, 5) + 2) + argument1;


ease-insine #define EaseInSine
/// EaseInSine(inputvalue,outputmin,outputmax,inputmax)

return argument2 * (1 - cos(argument0 / argument3 * (pi / 2))) + argument1;


ease-outsine #define EaseOutSine
/// EaseOutSine(inputvalue,outputmin,outputmax,inputmax)

return argument2 * sin(argument0 / argument3 * (pi / 2)) + argument1;


ease-inoutsine #define EaseInOutSine
/// EaseInOutSine(inputvalue,outputmin,outputmax,inputmax)

return argument2 * 0.5 * (1 - cos(pi * argument0 / argument3)) + argument1;


ease-incirc #define EaseInCirc
/// EaseInCirc(inputvalue,outputmin,outputmax,inputmax)
// This is a really radical curve... haha hidden programmer joke.

argument0 /= argument3;
return argument2 * (1 - sqrt(1 - argument0 * argument0)) + argument1;


ease-outcirc #define EaseOutCirc
/// EaseOutCirc(inputvalue,outputmin,outputmax,inputmax)

argument0 = argument0 / argument3 - 1;
return argument2 * sqrt(1 - argument0 * argument0) + argument1;


ease-inoutcirc #define EaseInOutCirc
/// EaseInOutCirc(inputvalue,outputmin,outputmax,inputmax)

argument0 /= argument3 * 0.5;

if (argument0 < 1)
{
    return argument2 * 0.5 * (1 - sqrt(1 - argument0 * argument0)) + argument1;
}

argument0 -= 2;
return argument2 * 0.5 * (sqrt(1 - argument0 * argument0) + 1) + argument1;


ease-inexpo #define EaseInExpo
/// EaseInExpo(inputvalue,outputmin,outputmax,inputmax)

return argument2 * power(2, 10 * (argument0 / argument3 - 1)) + argument1;


ease-outexpo #define EaseOutExpo
/// EaseOutExpo(inputvalue,outputmin,outputmax,inputmax)

return argument2 * (-power(2, -10 * argument0 / argument3) + 1) + argument1;


ease-inoutexpo #define EaseInOutExpo
/// EaseInOutExpo(inputvalue,outputmin,outputmax,inputmax)

argument0 /= argument3 * 0.5;

if (argument0 < 1) 
{
    return argument2 * 0.5 * power(2, 10 * --argument0) + argument1;
}

return argument2 * 0.5 * (-power(2, -10 * --argument0) + 2) + argument1;


ease-inelastic #define EaseInElastic
/// EaseInElastic(inputvalue,outputmin,outputmax,inputmax)

var _s = 1.70158;
var _p = 0;
var _a = argument2;

if (argument0 == 0 || _a == 0) 
{
    return argument1; 
}

argument0 /= argument3;

if (argument0 == 1) 
{
    return argument1+argument2; 
}

if (_p == 0) 
{
    _p = argument3*0.3;
}

if (_a < abs(argument2)) 
{ 
    _a = argument2; 
    _s = _p*0.25; 
}
else
{
    _s = _p / (2 * pi) * arcsin (argument2 / _a);
}

return -(_a * power(2,10 * (--argument0)) * sin((argument0 * argument3 - _s) * (2 * pi) / _p)) + argument1;


ease-outelastic #define EaseOutElastic
/// EaseOutElastic(inputvalue,outputmin,outputmax,inputmax)

var _s = 1.70158;
var _p = 0;
var _a = argument2;

if (argument0 == 0 || _a == 0)
{
    return argument1;
}

argument0 /= argument3;

if (argument0 == 1)
{
    return argument1 + argument2;
}

if (_p == 0)
{
    _p = argument3 * 0.3;
}

if (_a < abs(argument2)) 
{ 
    _a = argument2;
    _s = _p * 0.25; 
}
else 
{
    _s = _p / (2 * pi) * arcsin (argument2 / _a);
}

return _a * power(2, -10 * argument0) * sin((argument0 * argument3 - _s) * (2 * pi) / _p ) + argument2 + argument1;


ease-inoutelastic #define EaseInOutElastic
/// EaseInOutElastic(inputvalue,outputmin,outputmax,inputmax)

var _s = 1.70158;
var _p = 0;
var _a = argument2;

if (argument0 == 0 || _a == 0)
{
    return argument1;
}

argument0 /= argument3*0.5;

if (argument0 == 2)
{
    return argument1+argument2; 
}

if (_p == 0)
{
    _p = argument3 * (0.3 * 1.5);
}

if (_a < abs(argument2)) 
{ 
    _a = argument2; 
    _s = _p * 0.25; 
}
else
{
    _s = _p / (2 * pi) * arcsin (argument2 / _a);
}

if (argument0 < 1)
{
    return -0.5 * (_a * power(2, 10 * (--argument0)) * sin((argument0 * argument3 - _s) * (2 * pi) / _p)) + argument1;
}

return _a * power(2, -10 * (--argument0)) * sin((argument0 * argument3 - _s) * (2 * pi) / _p) * 0.5 + argument2 + argument1;


ease-inback #define EaseInBack
/// EaseInBack(inputvalue,outputmin,outputmax,inputmax)

var _s = 1.70158;

argument0 /= argument3;
return argument2 * argument0 * argument0 * ((_s + 1) * argument0 - _s) + argument1;


ease-outback #define EaseOutBack
/// EaseOutBack(inputvalue,outputmin,outputmax,inputmax)

var _s = 1.70158;

argument0 = argument0/argument3 - 1;
return argument2 * (argument0 * argument0 * ((_s + 1) * argument0 + _s) + 1) + argument1;


ease-inoutback #define EaseInOutBack
/// EaseInOutBack(inputvalue,outputmin,outputmax,inputmax)

var _s = 1.70158;

argument0 = argument0/argument3*2

if (argument0 < 1)
{
    _s *= 1.525;
    return argument2 * 0.5 * (argument0 * argument0 * ((_s + 1) * argument0 - _s)) + argument1;
}

argument0 -= 2;
_s *= 1.525

return argument2 * 0.5 * (argument0 * argument0 * ((_s + 1) * argument0 + _s) + 2) + argument1;


ease-inbounce #define EaseInBounce
/// EaseInBounce(inputvalue,outputmin,outputmax,inputmax)

return argument2 - EaseOutBounce(argument3 - argument0, 0, argument2, argument3) + argument1


ease-outbounce #define EaseOutBounce
/// EaseOutBounce(inputvalue,outputmin,outputmax,inputmax)

argument0 /= argument3;

if (argument0 < 1/2.75)
{
    return argument2 * 7.5625 * argument0 * argument0 + argument1;
}
else
if (argument0 < 2/2.75)
{
    argument0 -= 1.5/2.75;
    return argument2 * (7.5625 * argument0 * argument0 + 0.75) + argument1;
}
else
if (argument0 < 2.5/2.75)
{
    argument0 -= 2.25/2.75;
    return argument2 * (7.5625 * argument0 * argument0 + 0.9375) + argument1;
}
else
{
    argument0 -= 2.625/2.75;
    return argument2 * (7.5625 * argument0 * argument0 + 0.984375) + argument1;
}


ease-inoutbounce #define EaseInOutBounce
/// EaseInOutBounce(inputvalue,outputmin,outputmax,inputmax)

if (argument0 < argument3*0.5) 
{
    return (EaseInBounce(argument0*2, 0, argument2, argument3)*0.5 + argument1);
}

return (EaseOutBounce(argument0*2 - argument3, 0, argument2, argument3)*0.5 + argument2*0.5 + argument1);
```

Voici un exemple d'animation utilisant l'easing :

That’s the end of all the easing functions I have. Let’s look at how you can use that in an example.

This is the code to animate this button bounce.
GameMaker Easing Animation

Dans l'évènement `Create` :

```js
/// animation engine 

buttonwidth = 120 
buttonheight = 26

frame = 0 
framesmax[1] = 20 // heading towards the button
framesmax[2] = 20 // squishing against the button 
framesmax[3] = 20 // going back 
framesmax[4] = 20 // bouncing out

part = 1 // what part of the animation we are on 

distancebounce = 30
strechamountx = 0.4
strechamounty = 1.0
```

Dans l'évènement `Step` :

```js
frame++;
if (frame >= framesmax[part]) { // this part of the animation has finished move onto the next one
    part++;
    frame = 0;
    if (part >= array_length_1d(framesmax)) { // the whole animation has finished so reset the whole thing
        part = 1;
    }
}
```

Dans l'évènement `Draw` :

```js
switch (part)
{
    case 1: 
        var distance = distancebounce-EaseInCubic(frame, 0, distancebounce, framesmax[part])
        draw_sprite_ext(spr_buttonselect, 0,x-distance,y,1,1,0,c_white,1)
    break;
    case 2: 
        var strechh = 1-(EaseOutCubic(frame,1,100,framesmax[part])/100)*strechamountx
        var strechv = EaseOutCubic(frame,1,strechamounty/2,framesmax[part])
        draw_sprite_ext(spr_buttonselect, 0,x,y,strechh,strechv,0,c_white,1)
    break;
    case 3: 
        var strechh = (1-(EaseOutCubic(framesmax[part]-frame,1,100,framesmax[part])/100)*strechamountx)
        var strechv = EaseOutCubic(framesmax[part]-frame,1,strechamounty/2,framesmax[part])
        draw_sprite_ext(spr_buttonselect, 0,x,y,strechh,strechv,0,c_white,1)
    break;
    case 4: 
        var distance = EaseOutCubic(frame, 0, distancebounce, framesmax[part])
        draw_sprite_ext(spr_buttonselect, 0,x-distance,y,1,1,0,c_white,1)
    break;
}
```

### Utiliser des fichiers

#### Fichiers INI

GameMaker Studio 2 vous permet d'utiliser des fichiers *INI* pour sauvegarder des petites données (maximum 64 Ko). Si vous souhaitez utiliser des caractères accentués ou créez manuellement ce fichier et sauvegardez-le au format *UTF-8* car GameMaker Studio 2 sauvegarde par défaut un fichier *INI* inexistant au format *ANSI*.

Un fichier *INI* est simplement un fichier texte avec la structure suivante :

```
[section1]
cle1 = valeur1
cle2 = valeur2
[section2]
cle3 = valeur3
cle4 = valeur4
...
```

Pour résumer, une valeur est associée à une clé dans une section particulière.

**Remarque :** Sur Windows, les fichiers INI sont stockés dans un dossier spécial. Dans la barre de recherche de Windows, saisissez `%localappdata%` puis validez pour ouvrir l'emplacement. Cherchez un dossier portant le même nom que votre projet. Le fichier INI se trouve à l'intérieur.

##### Ouvrir un fichier *INI*

La fonction `ini_open` ouvre un fichier *INI*. Elle prend une chaîne de caractère correspondant au nom du fichier *INI*. Si le fichier n'existe pas et que vous utilisez des fonctions d'écriture, le fichier sera créé. Un seul fichier *INI* peut être ouvert à la fois.

```js
ini_open("nom_de_fichier.ini");
```

Vous pouvez également ouvrir un fichier *INI* virtuel en passant à la fonction `ini_open_from_string` une chaîne avec une structure identique au contenu d'un fichier *INI*.

```js
ini_open_from_string("[section]\ncle1 = valeur1\ncle2 = valeur\n");
```

**Attention !** Pensez toujours à refermer un fichier ouvert.

##### Lecture d'un fichier *INI*

Utilisez la fonction `ini_read_real` pour accéder à un nombre que vous pouvez affecter à une variable.

```js
nombre = ini_read_real("section", "cle", nombre_par_defaut);
```

Utilisez la fonction `ini_read_string` pour accéder à une chaîne que vous pouvez affecter à une variable.

```js
chaine = ini_read_string("section", "cle", "defaut");
```

##### Ecriture dans un fichier *INI*

Utilisez la fonction `ini_write_real` pour sauvegarder un nombre.

```js
ini_write_real("section", "cle", nombre_a_sauvegarder);
```

Utilisez la fonction `ini_write_string` pour sauvegarder une chaîne.

```js
ini_write_string("section", "cle", "chaine_a_sauvegarder");
```

##### Fermeture d'un fichier *INI*

Une fois que vous n'avez plus besoin d'utiliser le fichier *INI*, n'oubliez pas de le refermer avec la fonction `ini_close`. Si vous avez sauvegardé des données, elles sont réellement sauvegardées dans le fichier lors de la fermeture.

```js
ini_close();
```

## Divers

### Redémarrer le jeu

La fonction `game_restart` vous permet de redémarrer votre jeu.

```js
game_restart();
```

### Quitter le jeu

La fonction `game_end` vous permet de quitter le jeu.

```js
if keyboard_check_pressed(vk_escape)
{
    game_end();
}
```

## Caméras et viewports

Créer un objet `objet_camera` persistant.

Dans l'évènement `Room Start` :

```js
///@description Camera setup

// Camera
cameraX = 0;
cameraY = 0;
target = objet_a_suivre;
cameraWidth = 640;
cameraHeight = 360;

view_enabled = true;
view_visible[0] = true;
camera_set_view_size(view_camera[0], cameraWidth, cameraHeight);

// Display
displayScale = 2;
displayWidth = cameraWidth * displayScale;
displayHeight = cameraHeight * displayScale;
window_set_size(displayWidth, displayHeight);
surface_resize(application_surface, displayWidth, displayHeight);

// GUI
display_set_gui_size(cameraWidth, cameraHeight);

alarm[0] = 1;
```

Dans l'évènement `Alarm[0]` :

```js
window_center();
```

Dans l'évènement `Step` :

```js
if (instance_exsits(target)) {
    cameraX = target.x - cameraWidth / 2;
    cameraY = target.y - cameraHeight / 2;
    cameraX = clamp(cameraX, 0, room_width - cameraWidth);
    cameraY = clamp(cameraY, 0, room_height - cameraHeight);
}
camera_set_view_position(view_camera[0], cameraX, cameraY);
```

### Propriétés de viewports

- `view_xview[numero_viewport]` : correspond à la position horizontale du côté gauche du rectangle de viewport numéro `numero_viewport`.
- `view_yview[numero_viewport]` : correspond à la position verticale du côté supérieur du rectangle de viewport numéro `numero_viewport`.
- `view_wview[numero_viewport]` : correspond à la largeur du rectangle de viewport numéro `numero_viewport`.
- `view_hview[numero_viewport]` : correspond à la hauteur du rectangle de viewport numéro `numero_viewport`.

Par exemple, pour dessiner un rectangle dans un viewport, utilisez le code suivant dans un évènement `Draw` :

```js
draw_rectangle(
	view_xview[0],
	view_yview[0],
	view_xview[0] + view_wview[0],
	view_yview[0] + view_hview[0],
	false
	);
```

### L'affichage du jeu

- Une room sans viewport définit une surface d'application aux dimensions de la room.
- Une room avec un viewport définit une dimension de viewport qui est étirée (elle peut être déformée) sur la surface d'application.
- La surface d'application est mise à l'échelle de la fenêtre (ou de l'écran si le jeu est en plein écran). La surface d'application conserve ses proportions et des bandes noires apparaissent su les proportions de la surface d'application et celles de la fenêtre ou de l'écran sont différentes.
- Un calque GUI est affiché par dessus la surface d'application et est étirée (il peut être déformée) sur la surface d'application.

### Résolution

Les fonctions `display_get_width` et `display_get_height` renvoie la largeur et la hauteur de la résolution de l'écran principal de l'appareil.

Les fonctions `window_get_width` et `window_get_height` renvoie la largeur et la hauteur de la résolution de la fenêtre du jeu. Pour un jeu en plein écran ou sur mobile, ces dimensions sont les mêmes que celles renvoyées par les fonctions liées à l'écran principal.

La fonction `window_set_size` vous permet de modifier les dimensions de la fenêtre de jeu.

La fonction `window_center` positionne la fenêtre de jeu au centre de l'écran principale.

**Remarque :** Vous ne pouvez pas centrer une fenêtre dont vous avez modifié les dimensions dans la même étape. Attendez le prochain rafraichissement d'affichage pour le faire.

### La surface d'application

GameMaker Studio 2 affiche le jeu sur une surface spécifique référencée par une variable prédéfinie appelée `application_surface`. Cette surface sert de base à tous les évènements `Draw` des objects et est automatiquement remise à l'échelle de la fenêtre. Les proportions de la surface d'application sont conservées et des bandes noires sont affichées sur les côtés si nécessaire. En revanche, si la room définit un viewport, la vue du viewport est étirée sur la fenêtre et peut provoquer des déformations.

**Conseil :** Veillez à ce que le rectangle du viewport ait toujours les même proportions que votre surface d'application.

Vous pouvez obtenir ses dimensions avec les fonctions `surface_get_width` et `surface_get_height` en passant cette surface prédéfinie.

Vous pouvez modifier ses dimensions avec la fonction `surface_resize` en passant cette surface prédéfinie, la nouvelle largeur et la nouvelle hauteur.

### Le calque GUI

Par dessus la surface d'application, un calque GUI sert de base aux évènements `Draw GUI` des objects. Ce calque apparaît au dessus de tous les autres éléments et ne dépend pas d'un viewport.

Les fonctions `display_get_gui_width` et `display_get_gui_height` renvoient les dimensions de ce calque.

Vous pouvez modifier ses dimensions avec la fonction `display_set_gui_size` en passant la nouvelle largeur et la nouvelle hauteur. Ce calque est automatiquement étiré sur la surface d'application

**Conseil :** Veillez à ce que le calque GUI ait toujours les même proportions que votre surface d'application.

**Remarque :** Vous pouvez définir les dimensions de ce calque avec une résolution HD même si votre jeu est en pixel art.

### Ecran splitté

Dans un évènement `Create`.

```js
// définit les dimensions du jeu
var largeur_jeu = 640;
var hauteur_jeu = 360;

// active les viewports
view_enabled = true;

// paramètre la première vue (joueur 1)
// rend la vue visible
view_visible[0] = true;
// définit le coin supérieur gauche de la vue
view_xport[0] = 0;
view_yport[0] = 0;
// définit la taille de la vue
view_wport[0] = largeur_jeu / 2;
view_hport[0] = hauteur_jeu;
// crée une caméra
view_camera[0] = camera_create_view(0, 0, largeur_jeu / 2, hauteur_jeu, 0, object_joueur_1, -1, -1, largeur_jeu, hauteur_jeu);

// paramètre la seconde vue (joueur 2)
// rend la vue visible
view_visible[1] = true;
// définit le coin supérieur gauche de la vue
view_xport[1] = largeur_jeu / 2;
view_yport[1] = 0;
// définit la taille de la vue
view_wport[1] = largeur_jeu / 2;
view_hport[1] = hauteur_jeu;
// crée une caméra
view_camera[1] = camera_create_view(0, 0, largeur_jeu / 2, hauteur_jeu, 0, object_joueur_2, -1, -1, largeur_jeu, hauteur_jeu);

// récupère les dimension de l'écran physique
var largeur_ecran = display_get_width();
var hauteur_ecran = display_get_height();
// place la fenêtre au centre de l'écran
window_set_rectangle((largeur_ecran - largeur_jeu) / 2), (hauteur_ecran - hauteur_jeu) / 2), largeur_jeu, hauteur_jeu);
// redéfinit la taille de la fenêtre
surface_resize(application_surface, largeur_jeu, hauteur_jeu);
```

### Bitmap fonts

Les bitmap fonts vous permettent de convertir un sprite animé (constitué de plusieurs images) en caractères d'une police personnalisée.

Commencez par importer votre bitmap font.

- Créez un sprite et importez le fichier image comportant les caractères.
- Cliquez sur le bouton `Edit Image`.
- Dans l'éditeur de sprites, cliquez sur le menu `Image -> Convert to Frames`.
- Paramétrez les valeurs pour bien découper l'image.

Créez un objet vide et définissez la bitmap font.

- Créez un évènement `Create`.
- Créez une chaîne contenant chaque caractère de la bitmap font dans l'ordre exact où elles se trouvent dans la séquence d'images du sprite. Pensez à faire précéder certains caractères (`\` et `"`) du caractère d'échappement `\ `.
- Définissez une variable d'instance pour représenter la bitmap font.
- Utilisez la fonction `font_add_sprite_ext` pour générer la bitmap font.
  - Le premier paramètre correspond au sprite comportant la séquence d'images de chaque caractère.
  - Le deuxième paramètre correspond à la chaîne comportant tous les caractères de la bitmap font dans l'ordre.
  - Le troisième paramètre correspond à un booléen indiquant si chaque caractère de la bitmap font a une largeur différent (`true`) ou non (`false`).
  - Le dernier paramètre correspond à la séparation entre chaque caractère.

Il vous suffit ensuite d'utiliser la fonction `draw_set_font` avec cette variable d'instance pour définir la bitmap font comme police à utiliser pour les affichages de textes.

### Convertir une direction en un nombre

```js
number = round(direction / 90);
```

ou

```js
number = round(direction / 45);
```

## Des booléens aux vecteurs

Dans la plupart des tutos sur youtube, on trouve ce genre de chose pour les déplacements d'un objet avec le clavier :

```js
hsp = keyboard_check(vk_right) - keyboard_check(vk_left);
vsp = keyboard_check(vk_down) - keyboard_check(vk_up);
```

Je voudrais vous présenter une autre approche plus générale (portable sur d'autres moteurs) basée sur la notion de vecteur.

Un déplacement est constitué d'une direction et d'une distance à parcourir ou plus précisément, une amplitude. C'est ce qu'on appelle une vélocité (contrairement à une vitesse qui n'est que l'amplitude du déplacement). La vélocité est un vecteur c'est à dire un simple couple (pour la 2D) de valeurs numériques (ou scalaire). Je vais donc renommer les variables `hsp` et `vsp` pour qu'elles soient vraiment plus claires. A leur place je vais utiliser les variables `velocite_x` et `velocite_y`.

Maintenant, voici le principe de base : Au début de l'évènement `Step`, j'initialise ces variables avec la valeur `0` car je n'ai au départ aucun déplacement.

```js
var velocite_x = 0;
var velocite_y = 0;
```

**Remarque :** J'ai mis le mot clé `var` car je ne me servirai pas de ces variables dans d'autres évènements mais vous pouvez le supprimer si vous le souhaitez.

Ensuite, pour chaque touche du clavier, ou de la manette, je vais ajouter ou soustraire `1` à une de ces variables selon la touche enfoncée.

```js
if (keyboard_check(vk_left)) {
  velocite_x--;
}
if (keyboard_check(vk_right)) {
  velocite_x++;
}
if (keyboard_check(vk_up)) {
  velocite_y--;
}
if (keyboard_check(vk_down)) {
  velocite_y++;
}
```

**Remarque :** Notez que le code précédent est strictement équivalent à celui-ci :

```js
hsp = keyboard_check(vk_right) - keyboard_check(vk_left);
vsp = keyboard_check(vk_down) - keyboard_check(vk_up);
```

Mais ce code est très spécifique à GameMaker. Et je ne veux pas m'arrêter là.

Le plus important, c'est que je dois normaliser ma vélocité si je vais en diagonale. Je m'explique : Si j'appuie sur droite et bas en même temps, j'aurais à la fois un déplacement horizontal de `1` et un déplacement vertical de `1` soit une distance de `sqrt(2)` (théorème de Pythagore) qui vaut environ `1,4`. Je vais donc plus vite en diagonale qu'en ligne droite.

**Remarque :** La fonction `sqrt` calcule la racine carrée d'un nombre positif.

Normaliser un vecteur, c'est lui donner une amplitude égale à `1`. Vous comprendrez pourquoi une longueur de `1` est importante un peu plus tard. Pour normaliser un vecteur, il suffit de diviser chacune de ses composantes par sa longueur (son amplitude). Et comment calcule-t-on la longueur d'un vecteur ? A nouveau, théorème de Pytagore :

```js
var longueur_velocite = sqrt(velocite_x * velocite_x + velocite_y * velocite_y);
```

**Remarque :** GameMaker Studio 2 fournit la fonction `point_distance` pour calculer la distance entre deux points. Pour un vecteur, il suffit d'utiliser l'origine du repère comme point de départ et les composantes du vecteurs comme coordonnées du point d'arrivée.

```js
var longueur_velocite = point_distance(0, 0, velocite_x, velocite_y);
```

Comme on n'a pas besoin de conserver les anciennes valeurs de notre vecteur vélocité, nous allons directement les écraser avec leur nouvelle valeur. Mais attention ! Si on n'appuie sur aucune touche, on n'a pas de déplacement. On a ce qu'on appelle un vecteur nul. Et bien évidemment, un vecteur nul a une longueur égale à `0` et on ne peut donc pas le normaliser.

```js
if (longueur_velocite != 0) {
    velocite_x /= longueur_velocite;
    velocite_y /= longueur_velocite;
}
```

Maintenant, nous avons une vélocité normalisée (de longueur `1`). Et grâce à cette transformation, nous pouvons multiplier ce vecteur par un nombre de notre choix pour lui donner l'amplitude (la vitesse) que l'on veut. En effet, multiplier un vecteur de longueur `1` par un nombre, donne un vecteur de longueur égale à ce nombre.

**Remarque :** Multiplier les deux composantes d'un vecteur par un même nombre utilise le principe du théorème de Thalès.

Par exemple, si je définis ma vitesse comme ceci dans l'évènement `Create` :

```js
VITESSE = 60;
```

Il me suffit de multiplier chaque composante de ma vélocité pour avoir le déplacement que je veux avec la longueur `VITESSE` :

```js
velocite_x *= VITESSE;
velocite_y *= VITESSE;
```

Et maintenant, j'ai mon déplacement exact qui fonctionne quelles que soient les touches que j'appuie. J'en fais ce que je veux. Par exemple, déplacer mon objet :

```js
x += velocite_x;
y += velocite_y;
```

J'espère que cette explication aura été suffisamment claire pour vous donner envie de passer aux vecteurs. N'hésitez pas à me poser des questions si besoin.

# Trucs à réorganiser

## Tuiles

### Obtenir la tilemap d'un tile layer

La fonction `layer_tilemap_get_id` prend le nom d'un calque tile en paramètre et renvoie l'identifiant de la tilemap associée.

```js
tilemap = layer_tilemap_get_id("nom_calque_tuiles");
```

### Gestion de collisions entre un objet et des tuiles

Créez votre tilemap sur un tile layer pour définir votre niveau dans la room.
Créez un tileset composé de tuiles de la même taille que la tilemap précédente. Ce tileset est simplement composé d'une tuile transparente et d'une tuile de couleur semi transparente (pour voir les tuiles de la vraie tilemap dessous).
Dans la room, créez un calque de tuiles **au dessus** du calque de tuiles définissant votre niveau dans la room. Par exemple, appelez ce calque `"collisions"`.
Placez la tuile de couleur semi transparente au dessus des tuiles devant être testées par les collisions.
Dans l'événement `Create` de votre objet, récupérez la tilemap de collision.

```js
tilemap = layer_tilemap_get_id("collisions");
```

## Macros

While not exactly variables, macros are similar to them in how they are used, ie: they are named values that you can use throughout your code to replace hard-coded values. Basically, a macro is a named variable that holds a constant single value of any data type. You can define your own macros using the Script Editor and then use them in your code and DnD™ as if they were regular variables, with the one difference being that they can't be changed in the game.

The syntax structure for a macro is as follows:

|||
#macro <variable> <value>

For example say you define the following macro "total_weapons" (note the preceding "#" and the lack of a colon ";" at the end):

#macro total_weapons 10

You would then call this in your code like this:

if ++pos == total_weapons
    {
    pos = 0;
    }

Note that you would not be able to change the constant value, so code like this will cause the game to crash:

total_weapons = 11;

You can define a macro anywhere in your code or in a script and it will be pre-compiled and included in your game as if it was there from the start, but we recommend that you create a dedicated script asset and define all your macros in there. It will be easier to organise and debug later!

If you need the value of a macro to change at run-time then you should probably make it a global variable, since these can be changed from code during a game, unless you set the macro to be a runtime  function. By setting the macro to a function it means that this function will be called every time you use the macro. For example:

#macro col make_colour_hsv(irandom(255), 255, 255)

You would then call this macro something like this:

image_blend = col;

Using this code will make the image blend a different colour every time the macro is used. It is worth noting that you can also split macros over multiple lines using the \ character to show where the line breaks. An example would be something like:

#macro hello show_debug_message("Hello" + \
string(player_name) + \
", how are you today?");

This is purely cosmetic, in that splitting a macro like this will have no effect over the result of the final macro when used, and is simply to provide support for multi-line text on macros that have longer lines of code.

One very important feature of macros is that they can be defined for use with specific Configurations (configs), meaning you can have the same macro name but give it different values based on the currently selected config. For example, say you have a configuration for Android Ads and another for iOS Ads, then you could define a single macro to hold the required app ID value:

#macro ad_id "";
#macro Android:ad_id "com.yoyogames.googlegame"
#macro iOS:ad_id "com.yoyogames.appstoregame"

As you can see, you give the config name first then a colon : and then the macro name and value. Note that you cannot have any white-space between the colon : and either the config name nor the macro name otherwise you will get an error.




## Structure de données

GameMaker Studio 2 fournit une structure de données appelée DS Map. C'est une structure qui vous permet de stocker des données sous la forme d'une association entre une clé et une valeur. La clé correspond à l'identifiant unique de la valeur associée. Elle permet de retrouver ou modifier la donnée dans la DS Map. Une clé peut être soit un nombre soit une chaîne de caractères. La valeur est simplement la donnée que vous souhaitez stocker.

### Créer une DS Map

La fonction `ds_map_create` vous permet de créer une DS Map. Elle ne prend pas de paramètre. Elle renvoie un nombre correspondant à l'identifiant de la nouvelle structure créée.

```js
structure_ds_map = ds_map_create();
```

**Attention !** Cette fonction réserve de la place en mémoire. Vous devez donc toujours penser à libérer la mémoire lorsque vous n'en avez plus besoin.

### Détruire une DS Map

La fonction `ds_map_destroy` vous permet de détruire une DS Map existante. Elle prend en paramètre la DS Map à détruire.

```js
if (ds_exists(structure_ds_map, ds_type_map)) {
    ds_map_destroy(structure_ds_map);
}
```

**Attention !** Si la DS Map n'existe pas, une erreur se produira. Vérifiez toujours l'existence de la DS Map avec la fonction `ds_exists` avant de la détruire.

## Système de sauvegarde

Créer une DS Map dans l'évènement `Create` d'un objet responsable de la sauvegarde.

```js
save_date = ds_map_create();
```

La fonction `ds_map_add` vous permet d'ajouter une donnée à la structure. La fonction `ds_map_replace` vous permet de mettre à jour une donnée ou de l'ajouter si elle n'existe pas encore. Vous pouvez donc généralement utiliser `ds_map_replace` à la place de `ds_map_add`.



`ds_map_secure_save` et `ds_map_secure_load`