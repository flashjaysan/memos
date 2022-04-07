# Mémo AppGameKit

_par flashjaysan_

## Point d'entrée

Le programme principal doit s'appeler `main.agc`.

## Forcer le moteur de rendu

```
#renderer "moteur"
```

La chaîne désignant le moteur peut être :

- `"Basic"` : Force l'utilisation D'OpenGL 2.0 ou OpenGL 2.0 ES selon la plateforme d'exécution. Si ce n'est pas disponible, l'application se termine.
- `"Advanced"` : Force l'utilisation de Vulkan. Si ce n'est pas disponible, l'application se termine.
- `"Prefer Best"` : Force l'utilisation de Vulkan si disponible et utilise OpenGL dans le cas contraire.

Le moteur est défini au démarrage de l'application et ne peut plus être modifié.

Les shaders sont convertis automatiquement dans un format adapté au moteur de rendu sélectionné.

## Syntaxe du langage

Le langage n'est pas sensible à la casse.

### Macros

Les macros sont des instructions spéciales avec un suffixe `#`.

#### include

La macro `#include` permet d'importer le contenu d'un autre fichier source.

```
#include "nom_fichier"
```

**Attention !** Cette macro peut être enchainée mais vous ne devez pas redéfinir des identificateurs dans les différents fichiers sources.

**Remarque :** Le fichier source importé n'est pas intégré à l'emplacement de la macro.

#### insert

La macro `#insert` permet d'insérer à l'emplacement de la macro le contenu d'un autre fichier source.

```
#insert "nom_fichier"
```

**Attention !** Vous devez éviter d'insérer plusieurs fois un même fichier source s'il définit de nouveaux identificateurs.

#### constant

La macro `#constant` vous permet de définir un nom symbolique à une valeur arbitraire.

```
#constant nom valeur
```

**Attention !** Evitez de redéfinir un identificateur ou un mot clé réservé dans cette macro.

#### option_explicit

La macro `#option_explicit` peut être placée n'importe où dans le fichier source et force le compilateur à vérifier qu'une variable est bien déclarée avant d'être utilisée.

```
#option_explicit
```

#### company_name

La macro `#company_name` vous permet de définir un nom d'entreprise ce qui permet de générer une application au chemin `nom_societe/nom_application` au lieu de `nom_application`. Cela permet d'éviter les conflits avec d'autres applications du même nom mais conçues par d'autres personnes.

```
#company_name "nom_societe"
```

### Terminer l'exécution

L'instruction `end` termine le programme.

```
end
```

### Types de données

#### Entiers

```
42
10000
-233000
-100
```

#### Réels

```
20.0005
99.9
-5000.12
-9999.9991
```

#### Chaînes de caractères

```
""
"A"
"Hello World"
"Telephone"
"I am 99 years old"
"1.2.3.4.5.6.7.8.9"
"a" + "b"
```

### Variables

Par défaut, une variable est de type integer.

```
nom_variable = valeur
```

Pour définir une variable de type real, il faut ajouter le suffixe `#`.

```
variable_reel# = 4.3
```

Pour définir une variable de type string, il faut ajouter le suffixe `$`.

```
variable_chaine$ = "hello"
```

Il est également possible d'éviter les suffixes en déclarant explicitement le type des variables.

```
a as string
b as float
c as integer
```

### Conversion en string

```
Str(valeur)
```

### Variables globales

Utilisez le mot clé `global` pour définir une variable accessible depuis n'importe où dans le code.

```
global nom_variable
```

### Tableaux

```
DIM lottery$[52]
lottery$[1]="43,76,12,34,12,11"
lottery$[2]="76,12,34,12,11,44"
lottery$[3]="12,34,12,02,05,07"

FOR T=1 TO 52
PRINT ( lottery$[T] )
NEXT T
```

```
dim a [ 5 ] as integer = [ 10, 20, 30, 40, 50 ]
dim b [ 3 ] as float = [ 1.2, 1.3, 1.4 ]
```

#### Tableau à plusieurs dimensions

```
DIM lottery[52,6]
```

Il est possible d'aller jusqu'à 5 dimensions.

### Type personnalisé

```
TYPE MyType
 Fieldname1
 Fieldname2
 Fieldname3
ENDTYPE
```

```
TYPE MyType
 Fieldname1
 Fieldname2
 Fieldname3
 Fieldname4 AS integer
 Fieldname5 AS float
 Fieldname6 AS string
ENDTYPE
```

```
TYPE AccountEntryType
 Number AS INTEGER
 Name AS STRING
 Amount AS FLOAT
ENDTYPE
```

```
MyVariable AS MyType
MyVariable.Fieldname1 = 41
MyVariable.Fieldname2 = 42
MyVariable.Fieldname3 = 43
```

### Tableau de type personnalisé

```
DIM Accounts[100] AS AccountEntryType
Accounts[1].Number=12345
Accounts[1].Name="Lee"
Accounts[1].Amount=0.42
```

```
TYPE AmountsType
 CurrentBalance AS FLOAT
 SavingsBalance AS FLOAT
 CreditCardBalance AS FLOAT
ENDTYPE
TYPE AccountEntryType
 Number AS INTEGER
 Name AS STRING
 Amount AS AmountsType
ENDTYPE
DIM Accounts[100] AS AccountEntryType
Accounts[1].Number=12345
Accounts[1].Name="Lee"
Accounts[1].Amount.CurrentBalance=0.42
Accounts[1].Amount.SavingsBalance=100.0
Accounts[1].Amount.CreditCardBalance=-5000.0
```

### Commentaires

```
rem commentaire
```

```
// commentaire
```

```
remstart
  commentaire
remend
```

### Branchement conditionnel

#### If

```
if condition

endif
```

```
if condition

else

endif
```

```
if condition1

elseif condition2

endif
```

#### Select

```
select expression
    case constante1

    endcase
    case constante22

    endcase
endselect
```

```
select expression
    case constante1:

    endcase
    case constante2:

    endcase
    case default:

    endcase
endselect
```

### Boucles

L'instruction `do` `loop` permet de répéter indéfiniment une boucle.

```
do

loop
```

```
repeat

until condition
```

```
while condition

endwhile
```

```
for i = valeur_initiale to valeur_finale

next i
```

```
for i = valeur_initiale to valeur_finale step pas

next i
```

- Le mot clé `exit` permet de sortir immédiatement d'une boucle.
- Le mot clé `continue` permet de terminer immédiatement l'itération en cours et de passer à la suivante.

### Fonctions

```
function nom_fonction()

endfunction
```

```
function nom_function()
    valeur_retour = valeur
endfunction valeur_retour
```

`exitfunction` termine immédiatement l'exécution de la fonction.

```
function nom_fonction()
    exitfunction
endfunction
```

```
function nom_function()
    exit_function valeur_retour
endfunction
```

### Techniques essentielles

### Programme de base

```
running as integer = 1

while running
	Sync()
endwhile
```

### Définir la taille de la fenêtre

```
SetWindowSize(largeur, hauteur, plein_ecran)
```

### Définir la résolution virtuelle

```
SetVirtualResolution(largeur, hauteur)
```

### Définir le taux de rafraichissement de l'affichage

```
SetSyncRate(fps, mode)
```

Passez `1` au paramètre `mode` pour forcer le taux de rafraichissement. Passez `0` pour autoriser l'appareil à économiser de la batterie si besoin.

**Remarque :** Passez `0` au paramètre `fps` pour un taux de rafraichissement illimité.

**Conseil :** Utilisez plutôt la commande `SetVSync`.

### Activer la synchronisation verticale

```
SetVSync(1)
```

**Remarque :** Utilisez la valeur `0` pour désactiver la synchronisation verticale.

### Afficher les FPS

```
Print(ScreenFPS())
```

### Charger une image

```
image = LoadImage("fichier_image")
```

### Créer un sprite à partir d'une image

```
sprite = CreateSprite(image)
```

### Définir la position d'un sprite

```
SetSpritePosition(sprite, x, y)
```

## Scènes

### Inclure une scène

```
#include "nom_scene.scene"
```

### Initialiser une scène

Utilisez le suffixe `_setup` sur le nom de la scène pour appeler une fonction qui initialise la scène.

```
nom_scene_setup()
```

### Dessiner une scène

Utilisez le suffixe `_sync` sur le nom de la scène pour appeler une fonction qui initialise la scène.

```
nom_scene_sync()
```

**Remarque :** Utilisez cette fonction dans la boucle principale avant d'appeler la commande `Sync`.

### Ajuster l'opacité d'une scène

```
scenename_fade(valeur)
```

Le paramètre `valeur` est un entier compris entre `0` (totalement transparent) et `100` (totalement opaque).

### Libérer les ressources d'une scène

```
scenename_cleanup()
```

### Accéder aux éléments d'une scène

Utilisez simplemement le nom défini dans propriété `Unique Variable` de l'éditeur de scène pour faire référence à un élément en particulier.
