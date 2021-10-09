# Mémo BlitzMax

*par flashjaysan*

## Introduction



## Installation



## Interface

- Cliquez sur le bouton `New` (ou le menu `File -> New` ou `CTRL+N`) pour créer un nouveau fichier source.
- Cliquez sur le bouton `Open` (ou le menu `File -> Open` ou `CTRL+O`) pour ouvrir un fichier source existant.
- Cliquez sur le bouton `Close` (ou le menu `File -> Close Tab` ou `CTRL+W`) pour fermer le fichier source actif.
- Cliquez sur le bouton `Save` (ou le menu `File -> Save` ou `CTRL+S`) pour enregistrer le fichier source actif.
- Cliquez sur la fusée droite (ou le menu `Program -> Build` ou `CTRL+B`) pour compiler le fichier source actif.
- Cliquez sur la fusée inclinée (ou le menu `Program -> Build and Run` ou `CTRL+R`) pour compiler et exécuter le fichier source actif.

## Langage

### Attention à la casse

Ce langage n'est pas sensible à la casse. Les mot-clés ou les identificateurs sont identiques que vous utilisiez des majuscules ou des minuscules.

```
rem = Rem
while = wHiLe
player = playeR
```

### Commentaires

Les commentaires sont ignorés par le compilateur. Ils servent à ajouter des informations à votre code pour expliquer ce qu'il fait ou à désactiver temporairement certaines instructions.

Un commentaire sur une seule ligne commence par une apostrophe. Vous pouvez utiliser ce type de commentaire sur la même ligne après une instruction.

```
' Ceci est un commentaire.
Print "Hello." ' Affiche Hello dans la console.
```

Un commentaire sur plusieurs lignes commence par le mot-clé `Rem` et se termine par le mot-clé `End Rem`.

```
Rem
    Ceci est un
    commentaire.
End Rem
```

### End

Le mot clé `End` indique que le programme est terminé. Tout ce qui suit n'est pas exécuté.

### Variables

#### Modes de contrôle des variables

Vous pouvez spécifier un mode en tête de vos fichiers sources.

- Si vous ne précisez pas de mode, le mode par défaut est sélectionné. Dans ce mode, vous n'êtes pas obligé de déclarer vos variables ou le type de retour des fonctions/méthodes.
- Si vous préciser le mode `Strict`, vous devez déclarer toutes vos variables. Leur attribuer un type est optionnel. Par défaut, les variables sans type sont de type `Int` et les fonctions/méthodes qui ne déclarent pas de type de retour renvoient le type `Int`.
- Si vous précisez le mode `SuperStrict`, vous devez déclarer toutes vos variables et leur attribuer à toutes un type. Les fonctions/méthodes doivent également déclarer un type de retour.

**Conseil :** Il est généralement conseillé de choisir le mode `Strict`.

```
Strict
```

#### Déclarer une variable

Contrairement aux autres modes, dans le mode par défaut, vous n'êtes pas obligé de déclarer vos variables.

Pour déclarer une variable avec une portée locale, utilisez le mot-clé `Local` suivi du nom de la variable. Une variable de portée locale est accessible uniquement dans le bloc contenant sa déclaration et tous ses sous-blocs.

```
Local NomDeVariable
```

Vous pouvez également déclarer plusieurs variables sur la même ligne en séparant chaque variable avec une virgule (`,`).

```
Local NomDeVariable1, NomDeVariable2
```

**Remarque :** Techniquement, vous pouvez également déclarer vos variables avec le mot-clé `Global` mais cela en fait des variables avec une portée globale au projet (accessibles partout dans le projet) et cette pratique est fortement déconseillée si vous pouvez l'éviter.

```
Global NomDeVariable
```

Pour définir le type d'une variable, utilisez deux point (`:`) suivis du nom du type ou faites suivre (sans espace) le nom de la variable d'un caractère spécial pour les types de base.

```
Local NomDeVariable1: Int ' identique à Local NomDeVariable1 ou NomDeVariable1%
Local NomDeVariable2: Float ' identique à Local NomDeVariable2#
Local NomDeVariable2: Double ' identique à Local NomDeVariable2!
Local NomDeVariable3: String 'identique à Local NomDeVariable3$
Local NomDeVariable4: NomType
```

Vous pouvez également tout déclarer sur la même ligne en séparant les variables avec le signe *virgule*.

```
' identique à Local NomDeVariable1, NomDeVariable2#, NomDeVariable3$
Local NomDeVariable1 : Int, NomDeVariable2 : FLoat, NomDeVariable2 : String
```

Enfin, vous pouvez initialiser les variables lors de leur déclaration. Utiliser le signe égal (`=`).

```
Local NomDeVariable1 : Int = 10 ' identique à Local NomDeVariable1 = 10
Local NomDeVariable2 : Float = 10.01 ' identique à Local NomDeVariable2# = 10.01
Local NomDeVariable3 : String = "Hello" 'identique à Local NomDeVariable3$ = "Hello"
```

Vous pouvez également le faire sur une seule ligne en utilisant la virgule (`,`) comme séparateur.

```
' identique à Local NomDeVariable1 = 10, NomDeVariable2# = 10.01, NomDeVariable3$ = "Hello"
Local NomDeVariable1 : Int = 10, NomDeVariable2 : FLoat = 10.01, NomDeVariable3 : String = "Hello"
```

### Constantes

Une constante ne peut plus être modifiée après sa déclaration et provoque une erreur si vous tentez de le faire. C'est une protection utile pour un code plus sur.

Pour déclarer une constante, utilisez le mot-clé `Const` suivi du nom de la constante, du signe égal (`=`) et d'une expression constante (qui peut être constituée d'autres constantes déjà déclarées) ou d'un littéral.  Comme pour les variables, vous pouvez définir le type de la constante avec deux points (`:`) suivi du type et déclarer plusieurs constantes sur une même ligne avec une virgule (`,`). Une constante déclarée sans type explicite est de type `Int` par défaut.

```
Const STARTUP_SIZE = 1000
Const SCREEN_WIDTH = 640, SCREEN_HEIGHT = 480
Const SCREEN_AREA = SCREEN_WIDTH * SCREEN_HEIGHT
Const SCALE_FACTOR : Float = 1.5
Const DEFAULT_TITLE : String = "Mark Sibly"
```

**Remarque :** Utilisez de préférence la convention `ALL_CAPS` pour nommer vos constantes (tous les mots en majuscules séparés par un signe *underscore* (`_`)).

### Objets

#### Créer un nouveau type

```
Type NomType
    
End Type
```

**Conseil :** Comme le langage n'est pas sensible à la casse, on fait généralement précéder le nom d'un type par le suffixe `T`.

#### Créer une instance du type

```
instance: NomType = New TNomType
```

**Remarque :** Pensez à libérer la mémoire en affectant `Null` à la variable.

```
instance: NomType = Null
```

#### Définir un champ

```
Type NomType
    Field NomChamp: NomType
End Type
```

#### Accéder à un champ

```
instance.NomChamp = valeur
```

**Remarque :** Le champ ne doit pas être privé.

#### Définir une méthode

```
Type NomType
    Method NomMethode()
        
    End Method
End Type
```

#### Appeler une méthode

```
instance.NomMethode()
```

#### Définir un constructeur

```
Type NomType
    Method New()
        
    End Method
End Type
```

#### Définir un destructeur

```
Type NomType
    Method Delete()
        
    End Method
End Type
```

**Remarque :** Cette méthode est appelée automatiquement par le garbage collector.

#### Contrôler l'accès aux membres

```
Type NomType
    Public
        Field NomChampPublique: NomType
        Method NomMethodePublique()
            
        End Method

    Protected
        Field NomChampProtege: NomType
        Method NomMethodeProtegee()
            
        End Method

    Private
        Field NomChampPrive: NomType
        Method NomMethodePrivee()
            
        End Method
End Type
```

#### Héritage

```
Type NomTypeEnfant Extends NomTypeParent
    
End Type
```

**Remarque :** Par défaut, un nouveau type hérite du type `Object`. Un nouveau type ne peut hériter que d'un seul autre type.

#### Définir une méthode abstraite

```
Type NomType
    Method NomMethode() Abstract
End Type
```

#### Définir un type abstrait

```
Type NomType Abstract
    Method NomMethode() Abstract
End Type
```

#### Redéfinir une méthode héritée

```
Type NomTypeEnfant Extends NomTypeParent
    Method NomMethode() Override

    End Method
End Type
```

#### Redéfinir un constructeur

```
Type NomTypeEnfant Extends NomTypeParent
    Method New()
        super.New()

    End Method
End Type
```

#### Définir un champ statique

```
Type NomType
    Global NomVariableStatique: NomTypeStatique
End Type
```

**Remarque :** Ce champ est utilisable sans instancier le type.

#### Définir un champ constant

```
Type NomType
    Const NomConstante: NomTypeConstante = valeur
End Type
```

**Remarque :** Ce champ est utilisable sans instancier le type.

#### Définir une méthode statique

```
Type NomType
    Function NomMethodeStatique()
        
    End Function
End Type
```

**Remarque :** Cette méthode est utilisable sans instancier le type mais ne peut accéder qu'aux champs statiques ou constants.

#### Définir une interface

```
Interface NomInterface
    Method NomMethode()
End Interface
```

#### Implémenter une interface

```
Type NomType Implements NomInterface
    Methode NomMethode()
        
    End Methode
End Type
```

**Remarque :** Le type doit implémenter chaque méthode que l'interface définit.

### Opérateur d'affectation

D'une manière générale, le signe `=` correspond à une affectation. Mais dans le cas de conditions, ce signe correspond à une notion d'égalité mathématique.

```
Local NomDeVariable : Int = 10 ' déclaration + affectation
NomDeVariable = 20 'affectation
If NomDeVariable = 20 ' test d'égalité
    NomDeVariable = 30 ' affectation
End If
```

### Opérateurs mathématiques

```
A + B ' addition
A - B ' soustraction
A * B ' multiplication
A / B ' division
A Mod B ' modulo
A ^ B ' puissance
-A ' négation
```

### Opérateurs logiques

```
A = B ' A est égal à B
A <> B ' A est différent de B
A < B ' A est inférieur à B
A > B ' A est supérieur à B
A <= B ' A est inférieur ou égal à B
A >= B ' A est supérieur ou égal à B
Not A = B ' A n'est pas égal à B (A est différent de B)
Not A <> B ' A n'est pas différent de B (A est égal à B)
Not A < B ' A n'est pas inférieur à B (A est inférieur ou égal à B)
Not A > B ' A n'est pas supérieur à B (A est supérieur ou égal à B)
Not A <= B ' A n'est pas inférieur ou égal à B (A est inférieur à B)
Not A >= B ' A n'est pas supérieur ou égal à B (A est supérieur à B)
A = B And B = C ' A est égal à B et B est égal à C
A = C Or B = C ' A est égal à B ou B est égal à C
```

### Opérateurs sur les bits

```
~A ' inversion de bits
A & B ' ET sur les bits
A | B ' OU sur les bits
A ~ B ' OU exclusif sur les bits
A Shl B ' décalage de bits vers la gauche
A Shr B ' décalage de bits vers la droite
A Sar B ' décalage arithmétique de bits vers la droite
```

### Opérateurs d'affectation composés

```
A :+ B ' identique à A = A + B
A :- B ' identique à A = A - B
A :* B ' identique à A = A * B
A :/ B ' identique à A = A / B
A :Mod B ' identique à A = A Mod B
A :& B ' identique à A = A & B
A :| B ' identique à A = A \ B
A :~ B ' identique à A = A ~ B
A :Shl B ' identique à A = A Shl B
A :Shr B ' identique à A = A Shr B
A :Sar B ' identique à A = A Sar B
```

### Constantes prédéfinies

```
False ' équivalent à 0
True ' équivalent à 1
Pi ' équivalent à 3.1415926535897932384626433832795
```

### Instruction conditionnelle

#### Instruction Si Alors Sinon

L'instruction conditionnelle *Si Alors Sinon* commence par le mot-clé `If` et se termine par le mot-clé `End If`. Vous pouvez ajouter plusieurs clauses `Else If` et une clause `Else`. Les expressions des conditions évaluées à `0` ou `Null` sont fausses (`False`). Les autres valeurs sont vraies (`True`).

`True` et `False` sont des expressions constantes entières valant respectivement `1` et `0`.

```
If Condition1
    Instructions1
Else If Condition2
    Instructions2
Else
    Instructions3
End If
```

**Remarque :** Vous pouvez utilisez le mot-clé `Then` après une condition mais cela n'est pas nécessaire et ne rend pas vraiment le code plus lisible. Ce mot-clé peu être utile pour une instruction conditionnelle rédigée sur une seule ligne.

```
If Condition Then Instruction End If
```

#### Instruction Sélection

L'instruction *Sélection* commence par le mot-clé `Select` suivi d'une expression et se termine par le mot-clé `End Select`. Le bloc doit contenir une ou plusieurs sections `Case` avec une ou plusieurs expressions constantes séparées par une virgule, d'une section `Default` optionnelle. Cette instruction est utile lorsque vous souhaitez tester une expression qui doit prendre plusieurs valeurs spécifiques.

```
Select Expression
    Case Expressions
        Statements
    Default
        Statements
End Select
```

### Boucles

#### Boucle Tant que

La boucle *Tant que* commence par le mot-clé `While` et se termine par le mot-clé `Wend`.

```
While Condition
    Instructions
Wend
```

#### Boucle Répéter jusqu'à

La boucle *Répéter jusqu'à* commence par le mot-clé `Repeat` et se termine par le mot-clé `Until`.

```
Repeat
    Instructions
Until Condition
```

#### Boucle Répéter indéfiniment

La boucle *Répéter indéfiniment* commence par le mot-clé `Repeat` et se termine par le mot-clé `Forever`.

```
Repeat
    Instructions
Forever
```

#### Boucle Pour

La boucle *Pour* commence par le mot-clé `For` et se termine par le mot-clé `Next`.

```
For NomDeVariable = PremièreValeur To DernièreValeur
    Instructions
Next
```

**Remarque :** Par défaut, la valeur d'incrémentation est 1. Vous pouvez préciser un pas spécifique pour l'incrémentation de la variable avec le mot-clé `Step`.

```
For NomDeVariable = PremièreValeur To DernièreValeur Step ValeurDePas
    Instructions
Next
```

**Remarque :** La variante suivante arrête la répétition quand la variable devient égale à la dernière valeur. Cela exclut donc cette valeur.

```
For NomDeVariable = PremièreValeur Until DernièreValeur Step ValeurDePas
    Instructions
Next
```

**Remarque :** La variable `NomDeVariable` peut avoir une portée locale à la boucle en faisant précéder son nom du mot-clé `Local`.

```
For Local NomDeVariable = PremièreValeur To DernièreValeur Step ValeurDePas
    Instructions
Next
```

#### Commandes Exit et Continue

La commande `Exit` permet de sortir d'une des boucles précédentes et de continuer l'exécution à la première instruction après la boucle. C'est très utile pour une boucle infinie.

```
Repeat
    If ExitCondition
        Exit
    End If
    Instructions
Forever
```

La commande `Continue` permet de stopper l'exécution de la répétion en cours et de reprendre la boucle à la répétition suivante. Cela peut être utile dans une boucle *Pour*.

```
For NomDeVariable = PremièreValeur To DernièreValeur Step ValeurDePas
    If ContinueCondition
        Continue
    End If
    Instructions
Next
```

## Système de coordonnées

Le coin supérieur gauche correspond à l'origine du repère. L'axe vertical augmente vers le bas.

## API

### Définir la taille de la fenêtre

Utilisez la fonction `Graphics` (en dehors de la boucle principale) pour définir la largeur et la hauteur de la vue et si la vue doit être en plein écran (rien) ou non (`0`).

```
Graphics 640, 360, 0 ' résolution 640x360 en mode fenêtré
```

### Créer la boucle principale

Utilisez la boucle de votre choix. Voici un exemple de boucle `While` avec comme condition la fin de l'application ou l'appui sur la touche `ECHAP`.

```
While Not (KeyHit(KEY_ESCAPE) Or AppTerminate())
Wend
```

### Effacer la vue

Pour effacer la vue dans la boucle principale, utilisez la fonction `Cls`.

```
Cls
```

### Echanger les tampons d'affichage

Pour échanger les tampons d'affichage avant et arrière, utilisez la fonction `Flip` à la fin de la boucle principale. Passez la valeur 

```
Flip
```

### Définir la couleur de dessin

Utilisez la fonction `SetColor` pour définir la couleur de dessin à utiliser par les fonctions de dessin. Passez les composantes rouge, vert et bleu avec des valeurs comprises entre 0 et 255.

```
SetColor 255, 255, 255
```

### Afficher un point

Utilisez la fonction `Plot` pour afficher un point dans la vue dans la couleur de dessin définie précédemment.

```
Plot PointX, PointY
```

### Afficher un segment

Utilisez la fonction `DrawLine` pour tracer une ligne entre deux points dans la vue dans la couleur de dessin définie précédemment.

```
DrawLine Point1X, Point1Y, Point2X, Point2Y
```

### Afficher un rectangle

Utilisez la fonction `DrawRect` pour tracer un rectangle plein dans la vue dans la couleur de dessin définie précédemment.

```
DrawRect X, Y, Largeur, Hauteur
```

### Afficher un oval

Utilisez la fonction `DrawOval` pour tracer un oval plein dans la vue dans la couleur de dessin définie précédemment. L'oval est dessiné dans un rectangle défini par les arguments passés.

```
DrawOval X, Y, Largeur, Hauteur
```

### Afficher du texte

Utilisez la fonction `DrawText` pour afficher du texte dans la vue dans la couleur de dessin définie précédemment.

```
DrawText Chaîne, X, Y
```

### Charger une image

Utilisez la fonction `LoadImage` pour charger une image dans une variable de type `Timage`. 

```
Global Image:Timage = LoadImage("NomImage.bmp")
```

### Afficher une image

Utilisez la fonction `DrawImage` pour afficher une image de type `Timage`.

```
DrawImage(Image, X, Y)
```












































