# Mémo BlitzMax

*par flashjaysan*

## Introduction

BlitzMax est un langage de programmation open source conçu pour créer des jeux vidéos et des applications graphiques. Il est fortement typé, orienté objet, modulaire et embarque un ramasse miette.

Il est fournit avec un éditeur complet appelé *MaxIDE* qui vous permet de compiler nativement vos projets vers les plateformes suivantes :

- Windows
- Linux
- macOS
- Android
- iOS
- Raspberry Pi

## Installation

- [Téléchargez](https://blitzmax.org/downloads/) la version adaptée à votre plateforme et dézippez l'archive à l'emplacement de votre choix.
- Lancez l'éditeur MaxIDE.

**Remarque :** Vous pouvez également codez vos projets BlitzMax dans VS Code et utiliser l'excellente extension BlitzMax de Hezkore. Par ce biais vous n'aurez pas accès à la documentation intégrée de MaxIDE mais vous pourrez bénéficier de toutes les fonctionnalités fournies par VS Code ainsi que l'autocomplétion et la compilation via un bouton dans l'éditeur.

## Interface

- Cliquez sur le bouton `New` (ou le menu `File -> New` ou `CTRL+N`) pour créer un nouveau fichier source.
- Cliquez sur le bouton `Open` (ou le menu `File -> Open` ou `CTRL+O`) pour ouvrir un fichier source existant.
- Cliquez sur le bouton `Close` (ou le menu `File -> Close Tab` ou `CTRL+W`) pour fermer le fichier source actif.
- Cliquez sur le bouton `Save` (ou le menu `File -> Save` ou `CTRL+S`) pour enregistrer le fichier source actif.
- Cliquez sur la fusée à la verticale (ou le menu `Program -> Build` ou `CTRL+B`) pour compiler le fichier source actif.
- Cliquez sur la fusée inclinée (ou le menu `Program -> Build and Run` ou `CTRL+R`) pour compiler et exécuter le fichier source actif.

## Langage

### Attention à la casse

Ce langage n'est pas sensible à la casse. Les mot-clés ou les identificateurs sont identiques que vous utilisiez des majuscules ou des minuscules.

```
Rem ' identique à rem
While ' identique à wHiLe
Player ' identique à playeR
```

### Commentaires

Les commentaires sont ignorés par le compilateur. Ils servent à ajouter des informations à votre code pour expliquer ce qu'il fait ou à désactiver temporairement certaines instructions.

Un commentaire sur une seule ligne commence par une apostrophe. Vous pouvez utiliser ce type de commentaire sur la même ligne après une instruction.

```
' Ceci est un commentaire.
Print("Hello.") ' Affiche Hello dans la console.
```

Un commentaire sur plusieurs lignes commence par le mot-clé `Rem` et se termine par le mot-clé `End Rem`.

```
Rem
    Ceci est un
    commentaire.
End Rem
```

### Afficher du texte dans la console

```
Print(chaine)
```

### Récupérer la saisie utilisateur dans la console

```
NomVariable = Input(message)
```

**Remarque :** La fonction `Input` renvoie une valeur de type `String`.

### End

Le mot clé `End` indique que le programme est terminé. Tout ce qui suit n'est pas exécuté.

### Modes de contrôle

En tête de vos fichiers sources, vous pouvez spécifier un mode.

- Si vous ne précisez pas de mode, le mode Strict est sélectionné par défaut. Vous pouvez également préciser le mode `Strict` explicitement en tête de vos fichiers sources. Dans ce mode, vous devez déclarer toutes vos variables. Leur attribuer un type est optionnel. Par défaut, les variables sans type sont de type `Int` et les fonctions/méthodes qui ne déclarent pas de type de retour renvoient le type `Int`.
- Si vous précisez le mode `SuperStrict`, vous devez déclarer toutes vos variables et leur attribuer à toutes un type. Les fonctions/méthodes doivent également déclarer un type de retour.

**Remarque :** La version BlitzMax NG force le mode Strict par défaut mais les versions antérieurs de BlitzMax utilisaient un mode "libre" où vous n'étiez pas obligé de déclarer vos variables ou le type de retour de vos fonctions/méthodes.

**Conseil :** Il est généralement conseillé d'utiliser au minimum le mode `Strict`. Pour la meilleure sécurité de code, utilisez le mode `SuperStrict`.

```
SuperStrict
```

### Variables

#### Déclarer une variable

Pour déclarer une variable avec une portée locale, utilisez le mot-clé `Local` suivi du nom de la variable. Une variable de portée locale est accessible uniquement dans le bloc contenant sa déclaration et tous ses sous-blocs. Une variable locale déclarée au niveau le plus élevé d'un fichier source (en dehors de tout bloc) n'est pas accessible dans les fonctions.

```
Local nom_de_variable
```

**Remarque :** BlitzMax n'étant pas sensible à la casse, j'ai choisi d'utiliser la convention `snake_case` pour nommer mes variables de manière à les identifier plus facilement.

Vous pouvez également déclarer plusieurs variables sur la même ligne en séparant chaque variable avec une virgule `,`.

```
Local nom_de_variable_1, nom_de_variable_2
```

**Remarque :** Techniquement, vous pouvez également déclarer vos variables avec le mot-clé `Global` mais cela en fait des variables avec une portée globale au projet (accessibles partout dans le projet) et cette pratique est fortement déconseillée.

```
Global nom_de_variable
```

Pour définir le type d'une variable, utilisez deux point `:` suivis du nom du type ou faites suivre (sans espace) le nom de la variable d'un caractère spécial pour les types de base.

```
Local nom_de_variable_1:Int     ' identique à Local nom_de_variable_1 (en mode Strict) ou nom_de_variable_1%
Local nom_de_variable_2:Float   ' identique à Local nom_de_variable_2#
Local nom_de_variable_3:Double  ' identique à Local nom_de_variable_2!
Local nom_de_variable_4:String  ' identique à Local nom_de_variable_3$
Local nom_de_variable_5:NomType
```

Vous pouvez également tout déclarer sur la même ligne en séparant les variables avec une virgule `,`.

```
' identique à Local nom_de_variable_1, nom_de_variable_2#, nom_de_variable_3$
Local nom_de_variable_1:Int, nom_de_variable_2:FLoat, nom_de_variable_2:String
```

Enfin, vous pouvez initialiser les variables lors de leur déclaration. Utiliser le symbole égal `=`.

```
Local nom_de_variable_1:Int = 10            ' identique à Local nom_de_variable_1 = 10
Local nom_de_variable_2:Float = 10.01       ' identique à Local nom_de_variable_2# = 10.01
Local nom_de_variable_2:Double = 10.01      ' identique à Local nom_de_variable_2! = 10.01
Local nom_de_variable_3:String = "Hello"    ' identique à Local nom_de_variable_3$ = "Hello"
```

Vous pouvez également le faire sur une seule ligne en utilisant la virgule `,` comme séparateur.

```
' identique à Local nom_de_variable_1 = 10, nom_de_variable_2# = 10.01, nom_de_variable_3$ = "Hello"
Local nom_de_variable_1:Int = 10, nom_de_variable_2:FLoat = 10.01, nom_de_variable_3:String = "Hello"
```

### Constantes

Une constante ne peut plus être modifiée après sa déclaration et provoque une erreur si vous tentez de le faire. C'est une protection utile pour un code plus sûr.

Pour déclarer une constante, utilisez le mot-clé `Const` suivi du nom de la constante, du signe égal `=` et d'une expression constante (qui peut être constituée d'autres constantes déjà déclarées) ou d'un littéral.  Comme pour les variables, vous pouvez définir le type de la constante avec deux points `:` suivi du type et déclarer plusieurs constantes sur une même ligne avec une virgule `,`. Une constante déclarée sans type explicite est de type `Int` par défaut.

```
Const STARTUP_SIZE = 1000                               ' type Int par défaut
Const SCREEN_WIDTH:Int = 640, SCREEN_HEIGHT:Int = 480   ' déclaration multiple
Const SCREEN_AREA:Int = SCREEN_WIDTH * SCREEN_HEIGHT    ' utilisation d'expression constante
Const SCALE_FACTOR:Float = 1.5
Const DEFAULT_TITLE:String = "Mark Sibly"
```

**Remarque :** Même si le langage n'est pas sensible à la casse, utilisez de préférence la convention `ALL_CAPS` pour nommer vos constantes (tous les mots en majuscules séparés par un signe *underscore* `_`).

### Manipuler des chaînes

Les chaînes sont immutables.

Utiliser l'opérateur `+` pour concaténer des chaînes.

```
Local hello_string:String = "Hello"
Local world_string:String = "World"
Local message:String = hello_string + ", " + world_string
Print(message) ' affiche "Hello, World"
```

**Remarque :**  Indexer une chaîne renvoie une valeur de type `Short`. Vous devez caster la valeur en `Chr` pour l'utiliser comme un caractère.

```
Local lettre:Chr = Chr(chaine[N])
```

Utilisez la fonction Bin pour convertir un nombre en une chaine sous sa forme binaire.

```
Print(Bin(nombre))
```

### Caster une valeur

```
Int(valeur)
Float(valeur)
Double(valeur)
String(valeur)
```

### Littéraux

#### Littéraux entiers

```
100 ' forme décimale
$CAFEBABE ' forme hexadécimale (base 16)
%10101010 ' forme binaire (base 2)
```

#### Littéraux nombre à virgule

```
.5
10.0
1e6
1.5e-6
```

#### Littéraux chaines

```
"Hello, World!"
"" ' chaine vide
```

**Remarque :** Concaténer des chaînes constantes (définies à la compilation) créera une nouvelle chaîne constante.

#### Caractères d'échappement

```
~0                          ' Null character (code ASCII 0)
~t                          ' Tab character (code ASCII 9)
~r                          ' Return character (code ASCII 13)
~n                          ' Newline character (code ASCII 10)
~q                          ' Quote character (code ASCII 34)
~~                          ' Tilde character (code ASCII 126)
~n~ .. ~nnnn~               ' Unicode character, e.g. ~65~ = A
~$n~ .. ~$nnnn~             ' Hexadecimal character, e.g. ~$41~ = A
~%n~ .. ~%nnnnnnnnnnnnnnnn~ ' Binary character, e.g. ~%1000001~ = A
```

#### Casting de littéraux

Il est possible de caster un littéral en ajoutant deux points (`:`) suivi du nom du type.

```
$8000000000000000:Long
10:Double
```

### Opérateur d'affectation

D'une manière générale, le signe `=` correspond à une affectation. Mais dans le cas de conditions, ce symbole correspond à une notion d'égalité mathématique.

```
Local nom_de_variable:Int = 10  ' déclaration + affectation
nom_de_variable = 20            ' affectation
If nom_de_variable = 20         ' test d'égalité
    nom_de_variable = 30        ' affectation
End If
```

### Opérateurs mathématiques

```
A + B   ' addition
A - B   ' soustraction
A * B   ' multiplication
A / B   ' division
A Mod B ' modulo
A ^ B   ' puissance
-A      ' négation
```

### Opérateurs sur les bits

```
~A      ' inversion de bits
A & B   ' ET sur les bits
A | B   ' OU sur les bits
A ~ B   ' OU exclusif sur les bits
A Shl B ' décalage de bits vers la gauche
A Shr B ' décalage de bits vers la droite
A Sar B ' décalage arithmétique de bits vers la droite
```

### Opérateurs d'affectation composés

```
A :+ B      ' identique à A = A + B
A :- B      ' identique à A = A - B
A :* B      ' identique à A = A * B
A :/ B      ' identique à A = A / B
A :Mod B    ' identique à A = A Mod B
A :& B      ' identique à A = A & B
A :| B      ' identique à A = A \ B
A :~ B      ' identique à A = A ~ B
A :Shl B    ' identique à A = A Shl B
A :Shr B    ' identique à A = A Shr B
A :Sar B    ' identique à A = A Sar B
```

### Opérateurs logiques

```
A = B               ' A est égal à B
A <> B              ' A est différent de B
A < B               ' A est inférieur à B
A > B               ' A est supérieur à B
A <= B              ' A est inférieur ou égal à B
A >= B              ' A est supérieur ou égal à B
Not A = B           ' A n'est pas égal à B (A est différent de B)
Not A <> B          ' A n'est pas différent de B (A est égal à B)
Not A < B           ' A n'est pas inférieur à B (A est inférieur ou égal à B)
Not A > B           ' A n'est pas supérieur à B (A est supérieur ou égal à B)
Not A <= B          ' A n'est pas inférieur ou égal à B (A est inférieur à B)
Not A >= B          ' A n'est pas supérieur ou égal à B (A est supérieur à B)
A = B And B = C     ' A est égal à B et B est égal à C
A = C Or B = C      ' A est égal à B ou B est égal à C
```

### Constantes prédéfinies

```
False   ' équivalent à 0
True    ' équivalent à 1
Pi      ' équivalent à 3.1415926535897932384626433832795
```

**Remarque :** Il n'y a pas de type booléen. Utilisez le type entier `Int`.

### Tableaux

Créez un tableau avec `[]`. Un tableau a une dimension fixe et ne contient que des éléments du même type.

```
Local nom_tableau:NomType[] ' définit un tableau vide
```

ou

```
Local nom_tableau:NomType[taille] ' définit un tableau de Taille éléments
```

**Remarque :** Les éléments sont initialisés à la valeur par défaut du type.

Utilisez l'opérateur `New` pour créer un nouveau tableau.

```
Local nom_tableau:NomType[] = New NomType[taille]
```

Utilisez `[]` pour accéder à un élément particulier.

```
nom_tableau[0] = valeur_1
nom_tableau[1] = valeur_2
nom_tableau[3] = valeur_3
...
```

**Remarque :** Le premier élément d'un tableau commence à l'indice `0`.

Vous pouvez également initialiser un tableau lors de sa déclaration.

```
Local nom_tableau:NomType[] = [valeur1, valeur2, valeur3, ...]
```

ou

```
Local nom_tableau: NomType[taille] = [valeur1, valeur2, valeur3, ...]
```

#### Parcourir un tableau

Une fois créé, parcourez le tableau avec une boucle `For EachIn Next`.

```
For Local element:NomType = EachIn nom_tableau
    
Next
```

#### Longueur d'un tableau

Utilisez la propriété `Length` pour déterminer la longueur d'un tableau.

```
nom_tableau.Length
```

#### Trier un tableau

Appelez la méthode `Sort`.

```
nom_tableau.Sort() ' Trie le tableau par ordre croissant
```

**Remarque :** Par défaut, la méthode trie le tableau par ordre croissant. Passez la valeur `False` pour inverser l'ordre du tri.

```
nom_tableau.Sort(False) ' Trie le tableau par ordre décroissant
```

#### Tableaux à plusieurs dimensions

Séparez les dimensions par une virgule.

```
Local nom_tableau:NomType[, ]
```

Utilisez l'opérateur `New` pour créer un nouveau tableau.

```
Local nom_tableau:NomType[, , ] = New NomType[taille1, taille2, ...]
```

Ou précisez les dimensions.

```
Local nom_tableau:NomType[m, n]
```

#### Parcourir un tableau à plusieurs dimensions

Une fois créé, parcourez le tableau avec N boucles `For To Next` imbriquées.

``` 
For Local x = 0 To m
    For Local y = 0 To n
        
    Next
Next
```

#### Longueur d'un tableau à plusieurs dimensions

Utilisez la méthode `Dimensions` pour obtenir un tableau constitué d'un tableau d'`Int` à N dimensions contenant la longueur de chaque dimension.

```
Local longueurs:Int[] = nom_tableau.Dimensions()
```

**Exemple :**

```
Local nom_tableau:Int[10,5]
Local longueurs:Int[2] = nom_tableau.Dimensions() ' contient [10,5]
```

#### Tableaux de tableaux

Enchainez les `[]`.

```
Local nom_tableau:Int[][]
```

**Remarque :** Cette technique permet de créer des sous-tableaux de tailles différentes.

```
Local grille:Int[][] = [[1, 2, 3, 4], [5, 6, 7], [8, 9]]
```

#### Tranches de tableaux

Utilisez `..` pour trancher (*slice*) un tableau.

```
Local nom_tableau_2:NomType[] = nom_tableau_1[..]   ' copie le contenu du tableau
Local nom_tableau_2:NomType[] = nom_tableau_1[..n]  ' slice [0, n[
Local nom_tableau_2:NomType[] = nom_tableau_1[n..]  ' slice [n, nom_tableau_1.Length[
Local nom_tableau_2:NomType[] = nom_tableau_1[m..n] ' slice [m, n[
```

**Remarque :** Fonctionne aussi sur le type `String`.

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
        Instructions
    Default
        Instructionss
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
For nom_de_variable = premiere_valeur To derniere_valeur
    Instructions
Next
```

**Remarque :** Par défaut, la valeur d'incrémentation est 1. Vous pouvez préciser un pas spécifique pour l'incrémentation de la variable avec le mot-clé `Step`.

```
For nom_de_variable = premiere_valeur To derniere_valeur Step valeur_de_pas
    Instructions
Next
```

**Remarque :** La variante suivante arrête la répétition quand la variable devient égale à la dernière valeur. Cela exclut donc cette valeur.

```
For nom_de_variable = premiere_valeur Until derniere_valeur Step valeur_de_pas
    Instructions
Next
```

**Remarque :** La variable `nom_de_variable` peut avoir une portée locale à la boucle en faisant précéder son nom du mot-clé `Local`.

```
For Local nom_de_variable = premiere_valeur To derniere_valeur Step valeur_de_pas
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
For nom_de_variable = premiere_valeur To derniere_valeur Step valeur_de_pas
    If ContinueCondition
        Continue
    End If
    Instructions
Next
```

### Définir une fonction

```
Function NomFonction:NomType(parametre: NomType, ...)
    Return valeur
End Function
```

**Remarque :** Vous pouvez également indiquer une valeur par défaut pour les derniers paramètres.

```
Function NomFonction:NomType(parametre1: NomType, parametre2: NomType = valeur, ...)
    Return valeur
End Function
```

Vous pouvez également passer des paramètres par référence pour modifier leur valeur.

```
Function NomFunction:NomType(parametre1:NomType Var, ...)
    ...
    parametre1 = valeur
End Function
```

### Appeler une fonction

```
Local nom_variable:NomType = NomFonction(arguments)
```

### Objets

#### Créer un nouveau type

```
Type NomType
    
End Type
```

**Conseil :** Comme le langage n'est pas sensible à la casse, on fait généralement précéder le nom d'un type par le suffixe `T`.

#### Créer une instance du type

```
instance:NomType = New NomType()
```

**Remarque :** Pensez à libérer la mémoire en affectant `Null` à la variable une fois que vous n'en avez plus besoin.

```
instance:NomType = Null
```

#### Définir un champ

```
Type NomType
    Field NomChamp:NomType
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
    Method NomMethode:NomType()
        
    End Method
End Type
```

**Remarque :** Une méthode ne précisant pas le type de retour renvoie le type `Int`.

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
        Field NomChampPublique:NomType


        Method NomMethodePublique:NomType()
            
        End Method

    Protected
        Field NomChampProtege:NomType


        Method NomMethodeProtegee:NomType()
            
        End Method

    Private
        Field NomChampPrive:NomType


        Method NomMethodePrivee:NomType()
            
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
    Method NomMethode:NomType() Abstract
End Type
```

#### Définir un type abstrait

```
Type NomType Abstract
    Method NomMethode:NomType() Abstract
End Type
```

#### Redéfinir une méthode héritée

```
Type NomTypeEnfant Extends NomTypeParent
    Method NomMethode:NomType() Override

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
    Global NomVariableStatique:NomTypeStatique
End Type
```

**Remarque :** Ce champ est utilisable sans instancier le type.

#### Définir un champ constant

```
Type NomType
    Const NomConstante:NOM_TYPE_CONSTANTE = valeur
End Type
```

**Remarque :** Ce champ est utilisable sans instancier le type. Il doit être initialisé lors de la déclaration.

#### Définir un champ en lecture seule

Un champ défini avec le mot clé `ReadOnly` empêche la modification après l'instanciation.

```
Type TType
    Field champ_1:Int
    Field ReadOnly champ_2:Int


    Method New(parametre_1:Int, parametre_2:Int)
        champ_1 = parametre_1
        champ_2 = parametre_2
    End Method
End Type


Local instance:TType = New TType(0, 0) ' instanciation
instance.champ_1 = 10                  ' modification autorisée
instance.champ_2 = 10                  ' modification interdite (provoque une erreur)
```

#### Définir une méthode statique

```
Type NomType
    Function NomMethodeStatique:NomType()
        
    End Function
End Type
```

**Remarque :** Cette méthode est utilisable sans instancier le type mais ne peut accéder qu'aux champs statiques ou constants.

#### Définir une structure

Une structure est un type passé par valeur. La définition d'une structure est strictement identique à celle d'un type à la différence près que l'on utilise le mot clé `Struct` au lieu du mot clé `Type`.

```
Struct SVector2
    Private
        Field x:Int
        Field y:Int


    Public
        Method New(x:Int, y:Int)
            Self.x = x
            Self.y = y
        End Method


        Method Add(other:SVector2)
            Return New SVector2(Self.x + other.x, Self.y + other.y)
        End Method
End Structure
```

#### Définir une interface

```
Interface NomInterface
    Method NomMethode:NomType()
End Interface
```

**Conseil :** Comme le langage n'est pas sensible à la casse, on fait généralement précéder le nom d'une interface par le suffixe `I`.

#### Implémenter une interface

```
Type NomType Implements NomInterface
    Methode NomMethode:NomType()
        
    End Methode
End Type
```

**Remarque :** Le type doit implémenter chaque méthode que l'interface définit.

## Système de coordonnées

Le coin supérieur gauche correspond à l'origine du repère. L'axe vertical augmente vers le bas.

## Graphismes

### Définir la taille de la fenêtre

Utilisez la fonction `Graphics` (en dehors de la boucle principale) pour définir la largeur et la hauteur de la vue et si la vue doit être en plein écran (rien) ou non (`0`).

```
Graphics(640, 360, 0) ' résolution 640x360 en mode fenêtré
```

### Créer la boucle principale

Utilisez la boucle de votre choix. Voici un exemple de boucle `While` avec comme condition la fin de l'application ou l'appui sur la touche `ECHAP`.

```
While Not (KeyHit(KEY_ESCAPE) Or AppTerminate())
    
Wend
```

### Effacer la vue

Pour effacer la surface d'application, utilisez la fonction `Cls`.

```
Cls()
```

### Echanger les tampons d'affichage

Pour échanger les tampons d'affichage avant et arrière, utilisez la fonction `Flip` à la fin de la boucle principale. Passez la valeur 

```
Flip()
```

### Définir la couleur de dessin

Utilisez la fonction `SetColor` pour définir la couleur de dessin à utiliser par les fonctions de dessin. Passez les composantes rouge, vert et bleu avec des valeurs comprises entre 0 et 255.

```
SetColor(valeur_rouge, valeur_vert, valeur_bleu)
```

### Afficher un point

Utilisez la fonction `Plot` pour afficher un point dans la vue dans la couleur de dessin définie précédemment.

```
Plot(x, y)
```

### Afficher un segment

Utilisez la fonction `DrawLine` pour tracer une ligne entre deux points dans la vue dans la couleur de dessin définie précédemment.

```
DrawLine(x_1, y_1, x_2, y_2)
```

### Afficher un rectangle

Utilisez la fonction `DrawRect` pour tracer un rectangle plein dans la vue dans la couleur de dessin définie précédemment.

```
DrawRect(x, y, largeur, hauteur)
```

### Afficher un oval

Utilisez la fonction `DrawOval` pour tracer un oval plein dans la vue dans la couleur de dessin définie précédemment. L'oval est dessiné dans un rectangle défini par les arguments passés.

```
DrawOval(x, y, largeur, hauteur)
```

### Afficher du texte

Utilisez la fonction `DrawText` pour afficher du texte dans la vue dans la couleur de dessin définie précédemment.

```
DrawText(chaine, x, y)
```

### Charger une image

Utilisez la fonction `LoadImage` pour charger une image dans une variable de type `Timage`. 

```
Local image:TImage = LoadImage("chemin_vers_image.bmp")
```

### Afficher une image

Utilisez la fonction `DrawImage` pour afficher une image de type `Timage`.

```
DrawImage(image, x, y)
```

## Structures de données utiles



## Contrôles

SetAutoPoll

### Application

AppSuspended
AppTerminate

### Souris

#### Constantes liées à la souris

- `MOUSE_LEFT` : Bouton gauche de la souris.
- `MOUSE_RIGHT` : Bouton droite de la souris.
- `MOUSE_MIDDLE` : Bouton central de la souris.

#### Fonctions liées à la souris

FlushMouse
MouseDown
MouseHit
MouseX
MouseXSpeed
MouseY
MouseYSpeed
MouseZ
MouseZSpeed
WaitMouse

### Clavier

#### Constantes liées au clavier

##### Touches

- `KEY_BACKSPACE` : Backspace
- `KEY_TAB` : Tab
- `KEY_CLEAR` : Clear
- `KEY_RETURN` : Return
- `KEY_ENTER` : Enter
- `KEY_PAUSE` : Pause
- `KEY_ESCAPE` : Escape
- `KEY_SPACE` : Space
- `KEY_PAGEUP` : Page Up
- `KEY_PAGEDOWN` : Page Down
- `KEY_END` : End
- `KEY_HOME` : Home
- `KEY_LEFT` : Cursor (Left)
- `KEY_UP` : Cursor (Up)
- `KEY_RIGHT` : Cursor (Right)
- `KEY_DOWN` : Cursor (Down)
- `KEY_SELECT` : Select
- `KEY_PRINT` : Print
- `KEY_EXECUTE` : Execute
- `KEY_SCREEN` : Screen
- `KEY_INSERT` : Insert
- `KEY_DELETE` : Delete
- `KEY_HELP` : Help
- `KEY_0` : 0
- `KEY_1` : 1
- `KEY_2` : 2
- `KEY_3` : 3
- `KEY_4` : 4
- `KEY_5` : 5
- `KEY_6` : 6
- `KEY_7` : 7
- `KEY_8` : 8
- `KEY_9` : 9
- `KEY_A` : A
- `KEY_B` : B
- `KEY_C` : C
- `KEY_D` : D
- `KEY_E` : E
- `KEY_F` : F
- `KEY_G` : G
- `KEY_H` : H
- `KEY_I` : I
- `KEY_J` : J
- `KEY_K` : K
- `KEY_L` : L
- `KEY_M` : M
- `KEY_N` : N
- `KEY_O` : O
- `KEY_P` : P
- `KEY_Q` : Q
- `KEY_R` : R
- `KEY_S` : S
- `KEY_T` : T
- `KEY_U` : U
- `KEY_V` : V
- `KEY_W` : W
- `KEY_X` : X
- `KEY_Y` : Y
- `KEY_Z` : Z
- `KEY_LSYS` : Sys key (Left)
- `KEY_RSYS` : Sys key (Right)
- `KEY_NUM0` : Numpad 0
- `KEY_NUM1` : Numpad 1
- `KEY_NUM2` : Numpad 2
- `KEY_NUM3` : Numpad 3
- `KEY_NUM4` : Numpad 4
- `KEY_NUM5` : Numpad 5
- `KEY_NUM6` : Numpad 6
- `KEY_NUM7` : Numpad 7
- `KEY_NUM8` : Numpad 8
- `KEY_NUM9` : Numpad 9
- ` : Numpad` : `KEY_NUMMULTIPLY
- `KEY_NUMADD` : Numpad +
- `KEY_NUMSUBTRACT` : Numpad -
- `KEY_NUMDECIMAL` : Numpad .
- `KEY_NUMDIVIDE` : Numpad /
- `KEY_F1` : F1
- `KEY_F2` : F2
- `KEY_F3` : F3
- `KEY_F4` : F4
- `KEY_F5` : F5
- `KEY_F6` : F6
- `KEY_F7` : F7
- `KEY_F8` : F8
- `KEY_F9` : F9
- `KEY_F10` : F10
- `KEY_F11` : F11
- `KEY_F12` : F12
- `KEY_NUMLOCK` : Num Lock
- `KEY_SCROLL` : Scroll Lock
- `KEY_LSHIFT` : Shift (Left)
- `KEY_RSHIFT` : Shift (Right)
- `KEY_LCONTROL` : Control (Left)
- `KEY_RCONTROL` : Control (Right)
- `KEY_LALT` : Alt key (Left)
- `KEY_RALT` : Alt key (Right)
- `KEY_TILDE` : Tilde
- `KEY_MINUS` : Minus
- `KEY_EQUALS` : Equals
- `KEY_OPENBRACKET` : Bracket (Open)
- `KEY_CLOSEBRACKET` : Bracket (Close)
- `KEY_BACKSLASH` : Backslash
- `KEY_SEMICOLON` : Semi-colon
- `KEY_QUOTES` : Quote
- `KEY_COMMA` : Comma
- `KEY_PERIOD` : Period
- `KEY_SLASH` : Slash


##### Modificateur du clavier

- `MODIFIER_SHIFT`: Touche SHIFT du clavier.
- `MODIFIER_CONTROL` : Touche CTRL du clavier.
- `MODIFIER_OPTION` : Touche OPTION du clavier.
- `MODIFIER_SYSTEM` : Touche SYSTEM du clavier.
- `MODIFIER_COMMAND` : Touche COMMAND du clavier.

#### Fonctions liées au clavier

FlushKeys
GetChar
KeyDown
KeyHit
WaitChar
WaitKey

### Manettes

#### Fonctions liées aux manettes



## Audio



## Génération de nombres aléatoires

```
Rand(nombre_entier)                     ' renvoie un nombre dans l'intervalle [1, nombre_entier]
Rand(nombre_entier_1, nombre_entier_2)  ' renvoie un nombre dans l'intervalle [nombre_entier_1, nombre_entier_2]
```

## Modules

### Importer un fichier source

```
import "nomfichier.bmx"
```

**Attention !** Le nom du fichier est sensible à la casse.

## Déboggage

Voir la documentation sur les outils (*Tools*).

`Null` it can be converted to any type, and results in the types default value
for most classes that will be a null reference, so it will act the same as the null you may know from the likes of java or c#
strings are arrays have default values of "" and [] respectively,
