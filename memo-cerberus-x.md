# Mémo Cerberus X

*par flashjaysan*

## Présentation



## Langage

### Structure d'un projet

Un projet est constitué d'un ou plusieurs fichiers sources. Ceux-ci contiennent une série de déclaration. Les types de déclarations possible sont les suivants :

- Modules.
- Constantes.
- 2numérations d'entiers.
- Variables locales, globales et champs.
- Classes.
- Fonctions.
- Méthodes.

### Module

Un module est représenté par un seul fichier source. Son nom est déterminé par le nom de ce fichier source. Par exemple, un fichier source nommé `vecteur.cxs` définit un module nommé `vecteur`.

Un module peut importer d'autres modules.

### Mode strict

En tête de vos fichiers sources, vous pouvez spécifier le mode.

- Si vous ne précisez pas de mode, vous n'êtes pas obligé de définir le type de vos variables ni celui de la valeur de retour des fonctions/méthodes ainsi que leurs paramètres. Par défaut, un type manquant est automatiquement `Int`. Une fonction qui n'a pas d'instruction `Return` dans son corps se voit ajouter automatiquement une instruction avec une valeur par défaut par le compilateur.
  - `False` pour les booléens.
  - `0` pour les types numériques.
  - `""` pour les chaines.
  - `[]` pour les tableaux.
  - `Null` pour les objets.
- Si vous préciser le mode `Strict`, vous devez attribuer explicitement un type à toutes les variables, toutes les valeurs de retour des fonctions/méthodes et tous leurs paramètres. Une fonction qui renvoie une valeur (qui n'est pas déclarée avec le type `Void`) doit posséder une instruction `Return` dans son corps.

**Conseil :** Utilisez systématiquement le mode `Strict`.

```
Strict
```

### Point d'entrée

Chaque projet doit contenir un module contenant une fonction Main qui définit le point d'entrée du programme. Cette fonction ne prend pas de paramètre et renvoie un entier.

```
Strict


Function Main:Int()

	Return 0
End
```

### Instructions

Une instruction se termine généralement par un retour à la ligne. Il est possible de placer plusieurs instructions sur une même ligne en les séparant par `;`. Il est également possible de diviser des instructions longues mais uniquement après:

- `,` dans une liste de paramètres, des éléments d'un tableau et les énumérations.
- `[`
- `.`
- Tous les opérateurs. 

**Conseil :** Evitez d'écrire plusieurs instructions sur une même ligne.

### Commentaires

Les commentaires sont ignorés par le compilateur. Ils servent à ajouter des informations à votre code pour expliquer ce qu'il fait ou à désactiver temporairement certaines instructions.

Un commentaire sur une seule ligne commence par `'`. Vous pouvez utiliser ce type de commentaire sur la même ligne après une instruction.

```
' Ceci est un commentaire.
Print("Hello, world!") ' Affiche Hello, World! dans la console.
```

Les commentaires de blocs commencent par la directive de préprocesseur `#Rem` et se terminent par la directive `#End`. Ils ne peuvent pas suivre une instruction sur la même ligne. Ils peuvent toutefois être imbriqués.

```
#Rem
    Ceci est un
    commentaire.
#End
```

### Identificateurs

Les identificateurs introduisent de nouveaux noms dans le programme. Ils doivent commencer par une lettre ou `_` (suivi par une lettre). Ils peuvent ensuite être constitués de lettres, de chiffres ou de `_`. Ils sont sensibles à la casse.

Les mots clés du langage ne peuvent servir d'identificateurs.

### Mots clés

Les mots clés du langages ne peuvent servir d'identificateurs. Ils ne sont pas sensibles à la casse. Les mots réservés sont les suivants :

- `Abstract`
- `And`
- `Array` (non utilisé mais réservé pour de futurs utilisations)
- `Bool`
- `Case`
- `Catch`
- `Class`
- `Const`
- `Continue`
- `Default`
- `Eachin`
- `Else`
- `ElseIf`
- `End`
- `EndIf`
- `Enumerate`
- `Exit`
- `Extends`
- `Extern`
- `False`
- `Field`
- `Final`
- `Float`
- `For`
- `Forever`
- `Function`
- `Global`
- `If`
- `Implements`
- `Import`
- `Include`
- `Inline` (non utilisé mais réservé pour de futurs utilisations)
- `Int`
- `Interface`
- `Local`
- `Method`
- `Mod`
- `Module` (non utilisé mais réservé pour de futurs utilisations)
- `New`
- `Next`
- `Not`
- `Object`
- `Or`
- `Private`
- `Property`
- `Public`
- `Repeat`
- `Return`
- `Select`
- `Self`
- `Shl`
- `Shr`
- `Step`
- `Strict`
- `String`
- `Super`
- `Then`
- `Throw`
- `To`
- `True`
- `Try`
- `Until`
- `Void`
- `Wend`
- `While`

### Conventions de nommage

Les modules standards de Cerberus X utilisent les conventions suivantes :

- `ALL_CAPS` : Pour les constantes.
- `PascalCase` : Pour les variables globales, les noms de fonctions, de classes et les propriétés.
- `camelCase` : Pour les champs, les variables locales et les paramètres de fonctions.

**Conseils :** Utilisez ces conventions afin de faciliter les échanges avec d'autres utilisateurs.

### Littéraux

```
True            ' littéral booléen
False
1234            ' littéral entier
$CAFEBABE       ' littéral hexadécimal
9.81            ' littéral à virgule flottante
"Hello, World!" ' littéral chaine
`A`             ' littéral caractère
[2,4,6]         ' littéral tableau
Null            ' littéral référence vide
```

### Types

Les types suivants sont pris en charge :

- Booléens : `Bool` (`?`)
- Entiers : `Int` (`%`)
- Nombres à virgule flottante : `Float` (`#`)
- Chaines : `String` (`$`) (immutables)
- Tableaux : `NomType[]`
- Objets : `NomClasse`

### Chaines

Caractères d'échappement.

- `~q` : `34` (`"`)
- `~g` : `96` (`\``)
- `~n` : `10` (retour à la ligne)
- `~r` : `13` (return)
- `~t` : `9` (tabulation)
- `~z` : `0` (nul)
- `~u006F` : caractère unicode `0x006F`
- `~~` : `126` (`~`)

### Variables

```
Local Identificateur: type [= valeur]
Global Identificateur: type [= valeur]
```

### Constantes

```
Const Identificateur: type = valeur
```

### Enumérations

```
Enumerate Identificateur [= valeurDépart], Identificateur, Identificateur [= valeurDépart] [ , ...]
```

### Opérateurs

Les opérateurs suivants sont disponibles par ordre de précédence :

- `New` : Crée une instance.
- `Null` : objet vide.
- `True` : vrai.
- `False` : faux.
- `Self` : réference à l'objet courant.
- `Super` : réference à l'objet parent.
- `Literal` : Literal.
- `.` : accès à un membre.
- `(ExpressionSeq)` : appel.
- `[IndexExpression]` : index.
- `+` : posation.
- `-` : négation.
- `~` : inversion de bit.
- `Not` : NON logique.
- `*` : multiplication.
- `/` : division.
- `Mod` : modulo
- `Shl` : décalage de bit à gauche.
- `Shr` : décalage de bit à droite (signé).
- `+` : addition.
- `-` : soustraction.
- `&` : ET bit.
- `~` : XOR bit.
- `|` : OU bit.
- `=` : égal à.
- `<` : inférieur à.
- `>` : supérieur à.
- `<=` : inférieur ou égal à.
- `>=` : supérieur ou égal à.
- `<>` : différent de.
- `And` : ET logique.
- `Or` : OU logique.

### Affectation

```
variable = valeur ' affectation classique
variable += valeur ' équivalent à variable = variable + valeur
variable -= valeur ' équivalent à variable = variable - valeur
variable *= valeur ' équivalent à variable = variable * valeur
variable /= valeur ' équivalent à variable = variable / valeur
variable Mod= valeur ' équivalent à variable = variable Mod valeur
variable Shl= valeur ' équivalent à variable = variable Shl valeur
variable Shr= valeur ' équivalent à variable = variable Shr valeur
variable &= valeur ' équivalent à variable = variable & valeur
variable ~= valeur ' équivalent à variable = variable ~ valeur
variable |= valeur ' équivalent à variable = variable | valeur
```

### Afficher du texte

```
Print(valeur)
```

### Branchement conditionnel

```
If Expression [Then]
    Statements
ElseIf Expression [Then]
    Statements
Else
    Statements
EndIf 
```

```
Select Expression
Case Expression [, Expression]
    Statements
Default
    Statements
End [Select] 
```

## Boucles

Trois variantes de boucles `while` :

```
While Expression
    Statements
Wend
```

```
While Expression
    Statements
End
```

```
While Expression
    Statements
End While
```

Deux variantes de boucles `repeat` :

```
 Repeat
    Statements
Until Expression
```

```
Repeat
    Statements
Forever 
```

Trois variantes de boucles `for` :

```
For [Local] IndexVariable = FirstValue To | Until LastValue [Step StepValue]
    Statements
Next
```

```
For [Local] IndexVariable = FirstValue To | Until LastValue [Step StepValue]
    Statements
End
```

```
For [Local] IndexVariable = FirstValue To | Until LastValue [Step StepValue]
    Statements
End For
```

Trois variantes de boucles `For EachIn` :

```
For [Local] IndexVariable = EachIn Collection
    Statements
Next
```

```
For [Local] IndexVariable = EachIn Collection
    Statements
End
```

```
For [Local] IndexVariable = EachIn Collection
    Statements
End For
```

### Fonctions

```
Function Identifier: ReturnType (Parameters)
    Statements
End [Function] 
```

Cerberus X prend en charge la surcharge de fonctions.

### Propriétés

The optional `Property` keyword can be used to declare a 'property method'.

A property method with 0 parameters can be invoked without any brackets. A property method with 1 parameter can be invoked be using it as the left-hand-side of an assignment statement, in which case the right-hand-side expression of the assignment is passed to the property method.

You can therefore create methods that behave like fields, but actually execute code when they are read or written. You can use method overloading to provide both read and write property methods, or provide just a read method, or even just a write method. For example:

```
Class MyClass
    Field _value:Int
    Method Value( val:Int ) Property
        _value = val
        Print "Set _value to "+_value
    End
End

Function Main()
    Local myObject := New MyClass
    myObject.Value = 100          ' sets _value and outputs "Set _value to 100"
End
```

It is illegal to declare a property method with 2 or more parameters.

### Classes

```
Class Identifier [<Parameters>] [Extends BaseClass] [Implements Interfaces]
    Declarations
End [Class] 
```

#### Constructeurs



#### Champs



### Méthodes

```
Method Identifier: ReturnType (Parameters) [Property]
    Statements
End [Method]
```

Within a method you can also use the `Self` and `Super` keywords:

- `Self` may be used within a method to access the object the method is associated with.
- `Super` may be used within a method to call 'super class' methods.

#### Visibilité



#### Généricité



#### Héritage



### Interfaces

```
Interface Identifier [Extends Interfaces]
    Declarations
End [Interface] 
```

### Exceptions

```
Try
    
Catch exception: Throwable
    
End
```

## Mojo

### Point d'entrée

Comme précisé précédemment dans la section `Langage`, le point d'entrée d'un projet se fait dans une fonction `Main`. Pour un projet utilisant le module `mojo`, vous devez étendre la classe `mojo.app` et créer une instance dans la fonction `Main`.

```
Import mojo.app
Import mojo.graphics


Class MyApp Extends App
    Method OnRender()
        DrawText("Hello World!", 0, 0)
    End
End


Function Main:Int()
    New MyApp
End
```
