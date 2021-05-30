# Mémo Python

par *flashjaysan*

Ce document est un aide mémoire personnel que je mets à disposition de tous sous la licence *MIT*. Faites-en ce que vous voulez.

## Table des matières

- [Présentation de Python](#prsentation-de-python)
- [Pourquoi utiliser Python ?](#pourquoi-utiliser-python-)
- [Installation](#installation)
- [Interpréteur Python](#interprteur-python)
- [IDE](#ide)
    - [PyCharm](#pycharm)
    - [Geany](#geany)
    - [Visual Studio Code](#visual-studio-code)
- [Vérifier la version de Python installée](#vrifier-la-version-de-python-installe)
- [Lancer le mode interactif](#lancer-le-mode-interactif)
- [Quitter le mode interactif](#quitter-le-mode-interactif)
- [Utiliser pip](#utiliser-pip)
- [Environnements virtuels](#environnements-virtuels)
- [Afficher une donnée](#afficher-une-donne)
- [Créer un fichier source](#crer-un-fichier-source)
- [Exécuter un fichier source](#excuter-un-fichier-source)
- [Commentaire](#commentaire)
- [Déclarer une variable](#dclarer-une-variable)
- [Supprimer une variable](#supprimer-une-variable)
- [Obtenir le type d'une donnée](#obtenir-le-type-dune-donne)
- [Booléens](#boolens)
    - [Créer un objet booléen ](#crer-un-objet-boolen-)
    - [Opérateurs logiques](#oprateurs-logiques)
- [Chaînes de caractères](#chanes-de-caractres)
    - [Littéraux](#littraux)
    - [Littéraux multi-lignes](#littraux-multi-lignes)
    - [Créer une chaîne vide](#crer-une-chane-vide)
    - [Accéder à un caractère](#accder--un-caractre)
    - [Méthodes](#mthodes)
    - [Concaténation](#concatnation)
    - [Répétition d'une chaîne](#rptition-dune-chane)
    - [Longueur d'une chaîne](#longueur-dune-chane)
    - [Slicing](#slicing)
    - [Chaîne formatée](#chane-formate)
    - [Chaînes formattées de type fstrings](#chanes-formattes-de-type-fstrings)
    - [Assembler plusieurs chaînes](#assembler-plusieurs-chanes)
    - [Convertir une chaîne en une liste](#convertir-une-chane-en-une-liste)
    - [Lire une chaîne saisie par l'utilisateur](#lire-une-chane-saisie-par-lutilisateur)
- [Nombres](#nombres)
    - [Nombres Littéraux](#nombres-littraux)
    - [Créer un objet nombre](#crer-un-objet-nombre)
    - [Opérateurs](#oprateurs)
    - [Opérateurs arithmétiques](#oprateurs-arithmtiques)
    - [Opérateurs combinés](#oprateurs-combins)
    - [Opérateurs de comparaison](#oprateurs-de-comparaison)
    - [Convertir une chaîne en nombre](#convertir-une-chane-en-nombre)
- [Instructions if](#instructions-if)
- [Boucles](#boucles)
- [Instruction for](#instruction-for)
- [Définir un constructeur](#dfinir-un-constructeur)
- [Héritage](#héritage)
- [Module pickle](#module-pickle)
- [Module random](#module-random)
- [Fichiers](#fichiers)
- [Ouvrir un fichier](#ouvrir-un-fichier)
- [Fermer un fichier](#fermer-un-fichier)
- [Se positionner dans un fichier](#se-positionner-dans-un-fichier)
- [Lire dans un fichier](#lire-dans-un-fichier)
- [Ecrire dans un fichier](#ecrire-dans-un-fichier)
- [Fichiers en mode binaire](#fichiers-en-mode-binaire)
- [Module tkinter](#module-tkinter)
- [Importer le module](#importer-le-module)
- [Structure de base](#structure-de-base)
- [Concepts généraux](#concepts-gnraux)
- [Sites pour pratiquer Python](#sites-pour-pratiquer-python)

## Présentation de Python

Python est un langage de programmation réputé pour sa simplicité et sa puissance. Il a beaucoup évolué au fil du temps et certaines de ses fonctionnalités avancées sont devenues relativement complexes. Néanmoins, il reste un langage facile à apprendre et à lire, tout en étant très puissant. Il est utilisé dans de nombreux domaines et sa connaissance peut vous valoriser professionnellement.

Python se décline en deux versions :

- Python `2.7` est la version finale du langage sous son ancienne forme (série `2.X`). Il est encore utilisé dans bien des domaines et certains exemples que vous trouverez sur le web seront écrits pour cette version.
- Python `3.X` est la nouvelle version du langage. Il n’est pas complètement compatible avec la version 2. Néanmoins, il est préférable que vous appreniez cette version qui finira par devenir prédominante.

Python est un langage interprété mais il existe plusieurs implémentations différentes :

- *CPython* est l’interpréteur standard (celui que vous utiliserez dans ce cours). Il est le plus à jour et sa performance est relativement bonne.
- *Pypy* est un interpréteur *JIT* (Just In Time) qui compile des sections du code source pour optimiser son exécution. Il n’est pas aussi à jour avec le Standard que CPython mais est très performant. Si vous souhaitez améliorer les performances de vos applications, tournez vous vers lui.
- *Jython* est un interpréteur qui converti le code source en langage *Java* et permet d’utiliser les bibliothèques de ce langage.
- *IronPython* est un interpréteur qui converti le code source en *assembly .NET* et permet d’utiliser les bibliothèques de ce framework.

## Pourquoi utiliser Python ?

Python n’est certainement pas le langage le plus performant qui soit mais si vous débutez, il est préférable de vous simplifier la vie autant que possible.
L’interpréteur Python est libre, gratuit et s’installe facilement. Installer et utiliser des bibliothèques supplémentaires (modules) est très simple.
Apprendre les bases de la programmation avec Python est plus facile qu’avec d’autres langages et vous oblige à prendre de bonnes habitudes.  Enfin, apprendre Python pourra vous servir dans de nombreux domaines et vos connaissances seront applicables dans n’importe quel autre domaine de programmation.

## Installation

### Interpréteur Python

Pour installer l’interpréteur CPython, allez à l’adresse suivante :

[https://www.python.org/](https://www.python.org/)

Et cliquez sur la section `Downloads` pour télécharger la version correspondant à votre système. Ensuite installez Python. La version 2 est l'ancienne version qui ne sera plus mise à jour en 2020. Préférez la version 3.

**Remarque :** Sur Windows, pensez à cocher la case `Add Python 3.x to PATH` pour ajouter Python au chemin lors de l'installation. Sur *Mac OS X*, Python est déjà installé mais c'est la version 2. Vous pouvez installer la version 3 sans risque en utilisant la commande suivante :

```python
sudo apt-get install python3
```

Pour les autres implémentations, consultez leurs sites respectifs mais sachez que certaines bibliothèques pourront ne pas fonctionner. Vous devrez donc expérimenter par vous-même.

### IDE

Vous n’avez que l’embarras du choix. Voici quelques éditeurs :

#### PyCharm

*PyCharm* existe en version gratuite et est assez réputé :

[https://www.jetbrains.com/pycharm/](https://www.jetbrains.com/pycharm/)

**Remarque :** La version *Community* est gratuite.

#### Geany

*Geany* est un éditeur très léger, sans fioritures et disponible sur de nombreuses plateformes (y compris le *Raspberry Pi*) :

[https://www.geany.org/](https://www.geany.org/)

#### Visual Studio Code

*Visual Studio Code* est un éditeur très populaire créé par *Microsoft* mais dont le code source est libre :

[https://code.visualstudio.com/](https://code.visualstudio.com/)

#### Thonny

*Thonny* est un éditeur de code Python très simple mais proposant des outils pédagogiques très utiles aux débutants.

[https://thonny.org/](https://thonny.org/)

### Vérifier la version de Python installée

Pour voir quelle version de Python est installée sur votre machine, saisissez la commande suivante dans un terminal :

```
python --version
```

Sur Mac OS X, utilisez la commande `python3` :

```
python3 --version
```

### Lancer le mode interactif

Pour débuter le mode interactif, où vous pouvez saisir des instructions Python ligne par ligne, utilisez la commande `python` :

```
python
```

Les signes suivants vont alors apparaître pour vous indiquer que vous êtes passé en mode interactif :

```
>>>
```

### Quitter le mode interactif

Saisissez simplement la commande `exit()` (n'oubliez pas les parenthèses) :

```
exit()
```

### Utiliser pip

`pip` vous permet de gérer de nombreuses choses dans vos projets. Voici quelques exemples :

- `pip help` : vous montre les commandes de `pip`.
- `pip help commande` : vous montre les options de la commande.
- `pip search package` : vous montre une description du package.
- `pip install package` : installe le package.
- `pip install -U package` : met à jour le package déjà installé.
- `pip uninstall package` : désinstalle le package.
- `pip list` : affiche tous les packages installés.
- `pip list -o` ou `pip list --outdated` : affiche les packages installés qui ne sont pas à jour.
- `pip freeze` : affiche une liste des packages nécessaire à un projet. **A_VERIFIER**

### Environnements virtuels

Les *environnements virtuels* vous permettent d'avoir plusieurs configurations de Python séparées pour différents projets. Vous pouvez par exemple utiliser différentes versions d'un package pour deux projets différents. Commencez par installer le package des environnements virtuels :

```python
pip install virtualenv`

Placez-vous dans un dossier où vous allez créer vos environnements virtuels. Saisissez la commande suivante pour créer un environnement virtuel :

```
virtualenv nom_de_l'environnement_virtuel
```

Pour utiliser ce nouvel environnement virtuel, saisissez la commande suivante :

```
source nom_de_l'environnement_virtuel/bin/activate
```

La commande `which python` affiche le chemin du projet courant et l'environnement virtuel en cours d'utilisation.
Par défaut, les packages installés globalement ne sont pas accessibles depuis l'environnement virtuel mais vous pouvez utiliser `pip` pour installer les packages de votre choix.
Pour quitter l'environnement virtuel en cours d'utilisation, utilisez la commande `deactivate` :

```
deactivate
```

### Afficher une donnée

La fonction `print` affiche dans le terminal le ou les paramètres passés en arguments séparés par un espace puis effectue un retour à la ligne. Vous pouvez également passer des littéraux de type chaînes de caractères en argument :

```python
print(donnée)
print(donnée_1, ..., donnée_n)
```

### Créer un fichier source

Créez un simple fichier texte sans mise en forme. Par convention, sauvegardez vos fichiers sources avec l'extension `.py`.

### Exécuter un fichier source

Pour exécuter un fichier source Python (par défaut, l'extension est `.py`), double cliquez sur le fichier ou dans un terminal appelez `python` (ou `python3` si vous avez plusieurs versions de Python installées sur votre machine) suivi du nom du fichier à exécuter :

```python
python nom_du_fichier
```

Pour exécuter une partie d'un fichier pouvant également servir de *module*, utilisez la syntaxe suivante :

```python
if __name__ == "__main__":
    code_à_exécuter
```

### Commentaire

Un commentaire commence par le signe dièse `#` et se termine à la fin de la ligne :

```python
# Un commentaire sur une seule ligne`

Vous pouvez également utiliser une chaîne de caractères encadrée par trois guillemets simples pour rédiger un commentaire sur plusieurs lignes :

```python
'''
Un commentaire
sur plusieurs
lignes.
'''
```

### Déclarer une variable

En Python, on ne déclare pas une variable en lui associant un type de donnée. On lie un identificateur à une donnée lorsque celle-ci est créée.

```python
nom_de_variable = valeur`

### Supprimer une variable

La fonction `del` vous permet de supprimer une variable passée en argument.

```python
del(nom_de_variable)
```

### Obtenir le type d'une donnée

La fonction `type` permet de connaître le type d'une donnée passée en argument :

```python
type(donnée)
```

### Booléens

Le type `bool` (*booléen*) correspond à des valeurs logiques qui peuvent prendre soit la valeur `True` (vrai), soit la valeur `False` (faux).

**Remarque :** Notez la capitalisation des deux mots (la première lettre est en majuscule).

Les valeurs `None`, `0`,  `''`, `[]`, `()`, `{}` sont évaluées à `False`.

#### Créer un objet booléen 

Si vous souhaitez créer un objet booléen sans vous soucier de sa valeur, créer un objet booléen faux, en appelant le constructeur `bool` sans arguments.

```python
false_value = bool() # équivalent à false_value = False
```

#### Opérateurs logiques

Ces opérateurs s'appliquent à des valeurs booléennes et renvoient une valeur booléenne.

- `and` : *et* logique
- `or` : *ou* logique
- `not` : *non* logique

### Chaînes de caractères

En Python, il n'existe pas de type caractère. Utilisez à la place les *chaînes de caractères* du type `str`. Ce sont des *séquences*.

#### Littéraux

Guillemets simples ou doubles :

```python
'Hello world'
"Hello world"
```

`\'` et `\"` permettent de placer des guillemets dans des littéraux.

**Remarque :** Préférez les guillemets simples si possible.

#### Littéraux multi-lignes

```python
'''Hello
world'''
```

ou

```python
"""Hello
world"""
```

#### Créer une chaîne vide

Appelez le constructeur `str` sans arguments ou ne placez rien dans des guillemets.

```python
empty_str= str() # équivalent à empty_str = ""`

#### Accéder à un caractère

Utilisez les crochets avec l'index du caractère à accéder :

```python
some_string[index]
```

**Attention !** Le type `str` est *immutable*. Vous ne pouvez pas modifier un caractère individuellement. Vous devez affecter une nouvelle chaîne à la variable.

#### Méthodes

Voir les méthodes disponibles pour un objet particulier :

```python
print(dir(chaîne))
```

Voir ce que font les méthodes :

```python
print(help(str))
print(help(str.lower))
```

**Remarque :** `str` correspond au type chaîne de caractères en Python.

La méthode `lower` renvoie la chaîne en caractères minuscules :

```python
chaine.lower()
```

La méthode `upper` renvoie la chaîne en caractères majuscules :

```python
chaine.upper()
```

La méthode `count` compte le nombre d'occurrence d'une sous-chaîne :

```python
chaine.count(sous_chaine)`

La méthode `find` renvoie l'index d'une sous-chaîne :

```python
chaine.find(sous_chaine)
```

**Remarque :** Renvoie `-1` si la sous-chaîne n'existe pas dans la chaîne.

La méthode `replace` renvoie une chaîne avec une sous-chaîne remplacée par une autre :

```python
chaine.replace(sous_chaine_à_remplacer, sous_chaine_de_remplacement)
```

La méthode `center` renvoie une copie de la chaîne avec des espaces supplémentaires si nécessaires pour centrer la chaîne d'origine sur un nombre de caractères spécifié en argument :

```python
chaine.center(nombre)
```

#### Concaténation

L'opérateur `+` permet de concaténer deux chaînes.

```python
chaine_1 + chaine_2
```

#### Répétition d'une chaîne

L'opérateur `*` duplique la chaîne un certain nombre (entier) de fois :

```python
chaine * nombre_entier
```

#### Longueur d'une chaîne

Pour déterminer la longueur (le nombre de caractères) d'une chaîne, utilisez la fonction générale `len` :

```python
len(chaine)
```

**Remarque :** La fonction `len` prend une séquence en argument, c'est pourquoi ce n'est pas une méthode du type `str`.

#### Slicing

Renvoie le caractère à la position `index` :

```python
chaine[index]
```

**Remarque :** Les index commence à partir de `0`. Le dernier caractère est donc situé à l'index `len(chaine) - 1`.

Renvoie une sous-chaîne du caractère situé à l'index `départ` jusqu'au caractère situé à l'index `arrivée - 1` :

```python
chaine[départ:arrivée]
```

Renvoie une sous-chaîne depuis le premier caractère jusqu'au caractère situé à l'index `arrivée - 1` :

```python
chaine[:arrivée]
```

Renvoie une sous-chaîne depuis le caractère situé à l'index `départ` jusqu'au dernier caractère :

```python
chaine[départ:]
chaine[départ:arrivée:pas]
```

**Remarque :** Il est possible de passer un index négatif pour partir du dernier caractère.

#### Chaîne formatée

La méthode `format` permet de construire une chaîne composée d'un *littéral* avec des accolades indiquant l'endroit où insérer des éléments passés en argument :

```python
'{} littéral {}'.format(valeur_1, valeur_2)
```

vous pouvez également insérer un index entre les accolades pour indiquer quel argument utiliser :

```python
'{1} littéral {0}'.format(valeur_1, valeur_2)
```

Enfin, vous pouvez passer aux arguments des couples de clés / valeurs. Vous pouvez placer les clés entre les accolades :

```python
'{a} littéral {b}'.format(a=valeur_1, b=valeur_2)
```

#### Chaînes formattées de type fstrings

Depuis la version `3.6` de Python, vous pouvez placer directement des valeurs entre les accolades si vous faites précéder le littéral par un caractère `f` :

```python
f'{variable_1} littéral {variable_2}'
```

#### Assembler plusieurs chaînes

La méthode `join` permet de rassembler une séquence contenant des chaînes de caractères en les séparant par une chaîne :

```python
nouvelle_chaîne = 'séparateur'.join(séquence)
```

#### Convertir une chaîne en une liste

La méthode `split` découpe une chaîne en utilisant un séparateur passé en argument et place le tout dans une *liste* :

```python
liste = chaîne.split(séparateur)
```

#### Lire une chaîne saisie par l'utilisateur

La fonction `input` affiche un texte à l'écran et renvoie la chaîne de caractères saisie par l'utilisateur :

```python
user_answer = input('Texte à afficher :')
```

**Attention !** La fonction renvoie une chaine de caractères. Si vous souhaitez récupérer un nombre qu'a saisi l'utilisateur, pensez à convertir le résultat avec les fonctions `int` ou `float`.

```python
user_int = int(input('Saisissez un nombre entier :'))
user_float = float(input('Saisissez un nombre à virgule :'))
```

### Nombres

Il existe deux types de base pour représenter des nombres en Python. Les *entiers relatifs* appelés `int` et les *nombres à virgule flottante* appelés `float`.

#### Nombres Littéraux

**A EDITER** Entier décimal, int
Nombre avec un point ou un exposant -> float.

#### Créer un objet nombre

Si vous souhaitez créer un nombre sans vous soucier de sa valeur, créer un objet nombre nul, en appelant le constructeur `int` ou `float` sans arguments.

```python
null_int = int() # équivalent à null_int = 0
null_float = float() # équivalent à null_float = 0.0
```

#### Opérateurs

##### Opérateurs arithmétiques

- `+` : addition.
- `-` : soustraction.
- `*` : multiplication.
- `/` : division entière en Python 2, pas en Python 3.
- `//` : division entière en Python 3.
- `**` : puissance.
- `%` : reste de division entière (*modulo*).

**A EDITER** Précédence des opérateurs…
En cas de doute ou d'opération complexe, utiliser des parenthèses.

##### Opérateurs combinés

Pour effectuer une affectation en même temps qu'une opération, Python fournit les opérateurs combinés suivants :

- `+=` : `variable += valeur` équivalent à `variable = variable + valeur`.
- `-=` : `variable -= valeur` équivalent à `variable = variable - valeur`.
- `*=` : `variable *= valeur` équivalent à `variable = variable * valeur`.
- `/=` : `variable /= valeur` équivalent à `variable = variable / valeur`.

La fonction `abs` renvoie la *valeur absolue* d'un nombre :

```python
abs(nombre)
```

La fonction `round` arrondit un nombre à l'entier le plus proche :

```python
round(nombre)
```

Avec un second argument, vous pouvez arrondir à un nombre à virgule :

```python
round(nombre, précision)
```

##### Opérateurs de comparaison

Ces opérateurs s'appliquent sur des nombres et renvoient une valeur booléenne :

- `<` inférieur à.
- `<=` inférieur ou égal à.
- `>` supérieur à.
- `>=` supérieur ou égal à.

Ces opérateurs s'appliquent à tout type de données :

- `==` strictement égal à.
- `!=` différent de.
- `is` identité d'objet.

**Remarque :** L'opérateur `==` compare le contenu d'un objet avec le contenu d'un autre. Si les deux objets ont des données de même valeur, l'expression est évaluée à `True`. L'opérateur `is` compare l'adresse d'un objet en mémoire avec l'adresse de l'autre. Si les deux objets font référence au même espace mémoire, l'expression est évaluée à `True`.

La fonction `id` renvoie l'identité d'un objet :

```python
id(objet)
```

Si deux objets ont la même identité, l'opérateur `is` renvoie `True`. C'est équivalent à l'expression suivante :

```python
id(objet_1) == id(objet_2) # équivalent à objet_1 is objet_2
```

#### Convertir une chaîne en nombre

```python
int(chaîne)
float(chaîne)
```

**Remarque :** Dans une fstring, vous pouvez demander à afficher un certain nombre de chiffres après la virgule en faisant suivre l'expression des caractères `:.2f` (pour deux chiffres après la virgule).

```python
print(f"Affiche deux chiffres après la virgule : {1234.56789:.2f}")
```

## Instructions if

```python
if condition_1:
    instructions_1
elif condition_2:
    instructions_2
elif condition_3:
    instructions_3
...
else:
    instructions_par_défaut
```

**Remarque :** Les instructions doivent être indentées ou l'instruction `if` est terminée. Par convention, l'indentation en Python est constituée de quatre caractères "espace".

## Boucles

### Instruction for

```python
for élément in iterable:
    instructions
```

- Le mot clé `break` sort de la boucle.
- Le mot clé `continue` passe à l'itération suivante sans exécuter les instructions qui suivent dans la boucle.
- Le mot clé `pass` permet d'insérer un vide là où une ou des instructions sont attendues (dans les blocs).

Si vous ne comptez pas utiliser la variable `élément` dans les instructions de la boucle, utilisez l'identificateur `_` :

```python
for _ in itérable :
    instructions
```

Pour créer une répétition "classique" (un nombre de fois précis), utilisez la fonction `range` qui vous permet de créer un intervalle à parcourir :

```python
for i in range(départ, arrivée):
    instructions
```

**Remarque :** Les valeurs `départ` et `arrivée` correspondent à des nombres entiers. `arrivée` ne fait pas partie de l'intervalle : `[départ, arrivée[`

Si vous ne passer qu'un argument, l'intervalle commence à `0` :

```python
for i in range(arrivée):
    instructions
```

La fonction `range` est un *générateur*. Elle ne renvoie donc pas de donnée en elle-même. Pour obtenir une séquence de valeurs, convertissez-la en *liste* :

```python
list(range(arrivée))
```

Vous pouvez *dépaqueter* un *tuple* dans une instruction `for` et ainsi accéder à chaque sous-élément du tuple indépendamment des autres :

```python
for sous-élément_1, sous-élément_2, ... in un_tuple:
    instructions
```

Combinée à la fonction `enumerate`, cela vous permet de manipuler à la fois un élément d'un objet *itérable* et un compteur :

```python
for index, item in enumerate(iterable):
    instructions
```

### Instruction while

```python
initialisation
while condition:
    instructions_1
else
    instructions_2
```

**Remarque :** Prévoyez toujours de modifier la condition dans les instructions de la boucle pour éviter une répétition infinie.

## Mot clé pass

Utilisez le mot clé `pass` à l'endroit où un bloc d'instructions est attendu pour ignorer ce bloc. Par exemple, après une instruction `if`, `while`, `for` ou dans le corps d'une *fonction*.

## Assertions

```python
assert conditions_à_évaluer
```

Si la condition à évaluer est fausse, une *exception* de type `AssertionError` est levée.

## Lever une exception

Pour déclencher (lever) une *exception* vous-même, utilisez le mot clé `raise` suivi d'un appel au *constructeur* du type de l'exception à lever. Les constructeurs des exceptions prennent souvent en argument une chaîne de caractères décrivant l'erreur.

```python
raise type_de_l'exception("chaîne_de_caractères")
```

## Itérables

### Séquences

Utilisez le mot clé `in` pour déterminer si un élément se trouve dans une séquence :

```python
élément in séquence # vrai si élément se trouve dans séquence
```

### Listes

Pour créer une liste, utilisez des crochets avec une liste d'éléments.

```python
nom_de_liste = [élément_1, élément_2, ...]
```

**Attention !** Une variable contenant une liste contient en réalité une *référence* à cette liste. Si vous souhaitez passer une *copie* de la liste à une fonction construisez une nouvelle liste avec la fonction `list` :

```python
list(liste_d_origine)
```

Utilisez les crochets vides ou la fonction `list` pour créer une liste vide :

```python
liste_vide = []
liste_vide = list()
```

Les listes sont *mutables*. Vous pouvez modifier chaque élément.

```python
liste[index] = nouvelle_valeur
```

La fonction `len` renvoie le nombre d'éléments.

```python
len(liste)
```

Concaténez deux listes en une nouvelle avec l'opérateur `+` :

```python
nouvelle_liste = liste_1 + liste_2
```

Accédez aux éléments en utilisant les crochets et un index commençant à `0` :

```python
liste[index]
```

Vous pouvez utiliser un index négatif pour partir de la fin.
L'index `-1` est équivalent à l'index `len(liste) - 1`.
Le *slicing* s'applique également à ce type (voir les chaînes de caractères).

La méthode `append` permet d'ajouter un élément à la fin de la liste.

```python
liste.append(élément)
```

La méthode `insert` permet d'ajouter un élément à une position particulière.

```python
liste.insert(index, élément)
```

L'élément situé à l'index précisé et les suivants sont décalés d'une position vers la droite et leur index respectifs sont incrémentés d'un.

La méthode `extend` permet d'ajouter à la fin d'une liste les éléments d'une autre liste :

```python
liste_1.extend(liste_2) # similaire à liste_1 += liste_2`

La méthode `remove` retire un élément (le premier trouvé) d'une liste :

```python
liste.remove(élément)
```

Même si ce n'est pas très élégant, vous pouvez également utiliser la fonction générale `del` pour supprimer un élément :

```python
del(liste[index])
```

La méthode `pop` retire d'une liste son dernier élément et le renvoie :

```python
liste.pop()
```

Si vous passez un index, c'est l'élément situé à cette position qui sera supprimé de la liste et renvoyé et tous les éléments suivants seront décalés d'une position vers la gauche e leur index respectifs sont décrémentés d'un :

```python
liste.pop(index)
```

La méthode `reverse` inverse l'ordre des éléments de la liste :

```python
liste.reverse()
```

La méthode `sort` trie les éléments de la liste :

```python
liste.sort()
```

Passez l'argument `reverse=True` si vous voulez triez la liste dans le sens inverse :

```python
liste.sort(reverse=True)
```

**Attention !** Cette méthode modifie la liste d'origine et ne renvoie pas de valeur.

La fonction générale `sorted` prend une liste en argument et retourne une copie triée :

```python
sorted(liste)
```

La fonction `min` renvoie l'élément le plus "petit" d'une liste :

```python
min(liste)
```

La fonction `max` renvoie l'élément le plus "grand" d'une liste :

```python
max(liste)`

La fonction `sum` renvoie la somme de tous les éléments d'une liste :

```python
sum(liste)
```

La méthode `index` prend un élément en argument et retourne un index :

```python
liste.index(élément)
```

Le mot clé Python `in` renvoie un booléen pour indiquer si un élément est dans la liste :

```python
élément in liste
```

La boucle `for` permet de parcourir les éléments d'une liste :

```python
for identificateur in liste:
    instructions
```

Utilisez la fonction `enumerate` dans une boucle `for` pour obtenir à la fois les éléments et les index associés :

```python
for index, item in enumerate(liste):
    instructions
```

La fonction `enumerate` peut prendre un second argument pour indiquer à partir de quel index commencer le parcours :

```python
for index, élément in enumerate(liste, index_de_départ):
    instructions
```

Utilisez la fonction `zip` pour associer plusieurs objets *itérables* en une liste de tuples :

```python
zip(iterable_1, iterable,2, ...)
```

Cette fonction est un générateur. Elle ne renvoie pas de valeurs en elle-même.

#### Lists comprehension

```python
a_list = [expression for item in iterable]
```

```python
a_list = [expression for item in iterable if condition]
```

```python
a_list = [expression_1 if condition else expression_2 for item in iterable]
```

L'expression peut utiliser la variable `item`.

### Tuples

Pour créer un *tuple*, utilisez les parenthèses.

```python
nouveau_tuple = (élément_1, élément_2, ...)
```

**Attention !** Si vous créez un tuple contenant un seul élément, faites suivre ce dernier d'une virgule :

```python
tuple_à_un_seul_élément = (élément, )
```

**Attention !** Une variable contenant un tuple contient en réalité une *référence* à ce tuple. Si vous souhaitez passer une *copie* du tuple à une fonction construisez un nouveau tuple avec la fonction tuple :

```python
tuple(tuple_d'origine)
```

Utilisez les parenthèses vides ou la fonction tuple pour créer un tuple vide :

```python
tuple_vide = ()
tuple_vide = tuple()
```

**Attention !** Les tuples sont *immutables*. Cela signifie qu'ils ne peuvent être modifiés une fois créés. Considérez-les comme des listes constantes.

La méthode `count` renvoie le nombre d'objets identiques présent dans le tuple :

```python
nouveau_tuple.count(élément)
```

La méthode `index` renvoie l'index de la première occurrence de l'élément passé en argument :

```python
nouveau_tuple.index(élément)
```

### Sets

Les sets sont des *conteneurs* mais ne sont pas des *séquences*. Les éléments n'ont pas d'ordre dans les sets. De plus, chaque élément est unique. Il ne peut y avoir deux éléments identiques dans les sets.

Pour créer un set, utilisez les accolades et insérez les éléments séparés par une virgule :

```python
nouveau_set = {élément_1, élément_2, ...}
```

**Attention !** Une variable contenant un set contient en réalité une *référence* à ce set. Si vous souhaitez passer une *copie* du set à une fonction construisez un nouveau set avec la fonction set :

```python
set(set_d'origine)
```

Utilisez la fonction `set` pour créer un set vide :

```python
set_vide = set() # ne pas utiliser set_vide = ()
```

**Attention !** Les accolades vides créent un dictionnaire vide et non un set vide.

Pour convertir une collection en set, utilisez la fonction `set` :

```python
nouveau_set = set(collection)
```

La méthode `intersection` renvoie la liste des éléments en commun dans deux sets :

```python
set_1.intersection(set_2)
```

La méthode `difference` renvoie la liste des éléments qui ne sont pas en commun dans deux sets :

```python
set_1.difference(set_2)
```

La méthode `union` renvoie la liste des éléments dans deux sets :

```python
set_1.union(set_2)
```

Le mot clé Python `in` renvoie un booléen pour indiquer si un élément est dans un set :

```python
élément in un_set
```

Les sets sont plus efficaces que les listes ou les tuples pour cette opération.

La méthode `add` ajoute un nouvel élément unique dans le set :

```python
set.add(élément)
```

**Attention !** Si vous appelez cette méthode en passant en argument un élément déjà présent dans la liste, rien ne se passe.

### Dictionnaires

Un dictionnaire associe une *valeur* à une *clé* :

```python
dictionnaire = {clé_1: valeur_1, clé_2: valeur_2, ...}
```

Une clé peut être de n'importe quel type *immutable* (nombres, chaînes, etc...).**A_VERIFIER**

**Attention !** Une variable contenant un dictionnaire contient en réalité une *référence* à ce dictionnaire. Si vous souhaitez passer une *copie* d'un dictionnaire à une fonction construisez un nouveau dictionnaire avec la fonction `dict` :

```python
dict(dictionnaire_d'origine)
```

Pour accéder à un élément du dictionnaire, utilisez la clé entre crochets :

```python
dictionnaire[clé]
```

Utiliser une clé qui n'existe pas pour accéder à un élément entraîne une erreur. Pour éviter d'avoir une erreur, utilisez la méthode `get` qui retourne `None` si la clé n'existe pas :

```python
dictionnaire.get(clé)
```

Passez un second paramètre en argument à la méthode `get` pour qu'elle retourne ce paramètre plutôt que `None` :

```python
dictionnaire.get(clé, "cette clé est invalide")
```

Pour ajouter un couple *clé / valeur*, affectez une valeur à une nouvelle clé :

```python
dictionnaire[nouvelle_clé] = nouvelle_valeur
```

Si la clé existe déjà, l'ancienne valeur est remplacée par la nouvelle.

Pour modifier plusieurs éléments en une seule fois, utilisez la méthode `update` :

```python
dictionnaire.update({clé_a: valeur_a, clé_b: valeur_b, ...})
```

Si une clé n'existe pas, le couple *clé / valeur* est ajouté au dictionnaire.

Le mot clé Python `del` supprime un élément du dictionnaire :

```python
del dictionnaire[clé]
```

La méthode `pop` supprime et renvoie un élément du dictionnaire :

```python
dictionnaire.pop(clé)
```

La fonction générale `len` renvoie le nombre d'éléments du dictionnaire :

```python
len(dictionnaire)
```

La méthode `keys` renvoie une liste de toutes les clés du dictionnaire :

```python
dictionnaire.keys()
```

La méthode `values` renvoie une liste de toutes les valeurs du dictionnaire :

```python
dictionnaire.values()
```

La méthode `items` renvoie une liste de tuples contenant tous les couples *clé / valeur* du dictionnaire :

```python
dictionnaire.items()
```

Cette méthode est également utile pour parcourir le dictionnaire en dépaquetant les tuples :

```python
for key, value in dictionnaire.items():
    instructions
```

Les variables `key` et `value` prennent respectivement la *clé* et la *valeur* de l'élément courant.

Grâce à cette méthode, vous pouvez également créer des dictionnaires en compréhension.

```python
nouveau_dictionnaire = {nouvelle_cle: valeur for (cle, valeur) in dictionnaire.items() if condition}
```

## Fonctions

Les *fonctions* sont des instructions regroupées sous un *nom* et qui peuvent être *paramétrées* lors de l'appel à ce nom. Voyez-les comme des boîtes noires qui peuvent prendre des paramètres, qui exécutent une série d'instructions et qui peuvent renvoyer une valeur.

```python
def nom_de_fonction():
    """description"""
    instructions
```

**Remarque :** Par convention, toutes les fonctions en Python ont une chaîne de caractères (une *docstring*) pour décrire ce que fait la fonction, ses paramètres et, le cas échéant, son type de retour.

Une fonction sans instruction doit prendre l'instruction *pass* :

```python
def fonction_vide():
    pass
```

Utilisez le nom de la fonction suivie de parenthèses pour l'appeler :

```python
nom_de_fonction()
```

Pour renvoyer une valeur, utilisez le mot clé Python `return` :

```python
def nom_de_fonction():
    instructions
    return valeur
```

### Paramètres

Pour passez une liste de valeurs à une fonction, celle-ci doit avoir prévu ces paramètres lors de sa déclaration :

```python
def nom_de_fonction(paramètre_1, paramètre_2, ..., paramètre_n):
    instructions
```

Appelez la fonction avec le nombre de paramètres prévus :

```python
nom_de_fonction(valeur_1, valeur_2, ..., valeur_n)
```

Affectez des valeurs aux paramètres pour leur donner une valeur par défaut. Dans ce cas, vous pouvez appeler la fonctions avec moins d'arguments :

```python
def nom_de_fonction(paramètre_1, paramètre_2=valeur):
    instructions
```

```python
nom_de_fonction(valeur_1)
```

Précisez quel paramètre doit prendre quelle valeur comme ceci :

```python
nom_de_fonction(valeur_1, valeur_2, paramètre_n=valeur_n)
```

**Remarque :** Les *arguments nommés* doivent apparaître après les *arguments positionnels*.

Si vous voulez définir une fonction prenant un nombre variable de *paramètres positionnels*, utilisez la syntaxe suivante :

```python
def nom_de_fonction(*args):
    instructions
```

De même, pour des *paramètres nommés* :

```python
def nom_de_fonction(**kwargs):
    instructions
```

Combinez les deux possibilités en respectant l'ordre suivant : *paramètres positionnels* puis *paramètres nommés* :

```python
def nom_de_fonction(*args, **kwargs):
    instructions
```

**Remarque :** Bien que vous puissiez utiliser n'importe quel nom pour ces paramètres, par convention, on utilise les identificateurs `args` et `kwargs`.

Lors de l'appel à la fonction, les paramètres `args` et `kwargs` sont convertis en *tuples* contenant les différents arguments.

Pour imposer un certains nombre de paramètres, placez ces derniers avant les paramètres variables :

```python
def nom_de_fonction(paramètre_requis_1, paramètre_requis_2, *args):
    instructions
```

Faites de même pour les *paramètres nommés*. Ces derniers doivent cependant être placés après les *paramètres positionnels* (variables ou non) :

```python
def nom_de_fonction(paramètre_requis, *args, paramètre_nommé_1=valeur, **kwargs):
    instructions
```

Lors de l'appel à la fonction, si vous souhaitez utiliser une *liste* à la place d'une suite d'*arguments positionnels*, faites précéder le nom de la *liste* du caractère `*` pour la convertir en *arguments positionnels*. De même, pour utiliser un *dictionnaire*, faites précéder le nom du *dictionnaire* de deux caractères `**` pour le convertir en une suite d'arguments nommés :

```python
nom_de_fonction(*nom_liste, **nom_dictionnaire)
```

## Modules

Pour importer le code d'un *module* dans un autre, utilisez le mot clé Python `import` :

```python
import nom_de_module
```

**Remarque :** Vous n'avez pas besoin de préciser l'extension `.py` pour importer un fichier.

Importez les fichiers dès les premières lignes de votre code source qui en a besoin. Les fichiers sont recherchés dans une liste de chemin accessible avec l'objet `path` du module `sys` (vous devez donc l'importer avant de pouvoir utiliser cet objet) :

```python
import sys

print(sys.path)
```

Python cherche les fichiers à importer dans le dossier du fichier courant. Puis dans le chemin de *variable d'environnement* de Python. Ensuite, Python regarde dans le dossier de la *bibliothèque standard*.  Enfin, il regarde dans les packages de site pour les bibliothèques supplémentaires.
Il est déconseillé d'ajouter à `sys.path` un chemin spécifique mais vous pouvez le faire avec la méthode `append` :

```python
sys.path.append(nouveau_chemin)
```

Il est possible de paramétrer votre variable d'environnement de Python sur votre système. Si vous le souhaitez, documentez-vous sur cette possibilité.
Lorsque vous importez un fichier dans un autre, le code du fichier importé est exécuté.
Pour utiliser des objets ou des fonctions provenant d'un fichier externe, faites précéder le nom de la fonction par le nom du fichier :

```python
nom_de_fichier.nom_de_fonction()
```

Pour importer directement le nom de l'objet ou de la fonction d'un module sans le faire précéder du nom du module, utilisez la forme `from import` :

```python
from nom_de_fichier import nom_de_fonction
```

**Remarque :** Pour importer plusieurs objets ou fonctions, séparez-les par des virgules.

Pour attribuer un *alias* à un nom de module, utilisez le mot clé Python `as` :

```python
import nom_de_fichier as alias
```

Pour attribuer un alias à un nom d'objet ou de fonction d'un module, utilisez le mot clé Python `as` avec la syntaxe suivante :

```python
from nom_de_fichier import nom_de_fonction as alias
```

Importer tous les objets et fonctions d'un fichier est une mauvaise pratique mais vous pouvez le faire avec le signe `*` :

```python
from nom_de_fichier import *
```

## Exceptions

```python
try:
    instructions_pouvant_provoquer_une_exception
except:
    instructions_à_exécuter_en_cas_d'exception
```

**Remarque :** Cette forme capture tous les types d'erreurs possibles. Utilisez plutôt la forme suivante.

Pour gérer différentes erreurs, utilisez la forme plus complète suivante :

```python
try:
    instructions_pouvant_provoquer_une_erreur
except nom_d_exception1:
    instructions_à_exécuter_en_cas_d_exception1
except nom_d_exception2:
    instructions_à_exécuter_en_cas_d_exception2
...
else:
    instructions_à_exécuter_si_aucune_exception
finally:
    instructions_à_exécuter_dans_tous_les_cas
```

Pour utiliser l'erreur dans le bloc d'exception, utilisez la syntaxe suivante :

```python
try:
    instructions_pouvant_provoquer_une_erreur
except nom_d_erreur as alias:
    instructions_à_exécuter_en_cas_d_erreur
```

## Programmation orientée objet

Tôt ou tard, vous devrez construire vos propres objets constitués de différents assemblages de sous éléments. La programmation permet de coupler ces nouveaux types avec des fonctions qui leur sont fortement associées. Avant de pouvoir utiliser un nouveau type vous devez le définir. Pour cela, vous allez créer une classe.

### Définir une nouvelle classe

Définir une classe vous permet de concevoir un nouveau type d'objet que vous pourrez utiliser par la suite. Utilisez le mot clé "class" suivi du nom de votre nouvelle classe pour la définir.

```python
class NomDeClasse:
    pass
```

Le mot clé `pass` vous permet de définir une classe vide sans provoquer d'erreur à l'éxécution.
Vous pouvez également définir la classe en faisant suivre son nom de parenthèses vide pour indiquer qu'elle n'a pas de classe parent mais cela vous fait écrire deux caractères de plus :

```python
class NomDeClasse():
    pass
```

**Remarque :** Par convention, les noms de classes utilisent la notation PascalCase : Chaque mot constituant le nom de la classe possède une initiale en majuscule.

Pour créer une instance de votre nouvelle classe, il vous suffit d'appeler une fonction portant le nom de la classe qu'on appelle un constructeur :

```python
instance_de_classe = NomDeClasse()
```

**Attention !** Si vous définissez une méthode `__init__` avec des paramètres, vous devez passer des arguments qui y correspondent lors de l'appel.

Pour que votre classe ait une quelconque utilité elle doit posséder des données et / ou des méthodes.

### Attributs de classe

Pour définir des attributs à votre classe, créez des variables à l'intérieur de celle-ci en dehors de toute méthode.

```python
class NomDeClasse:

    attribut = valeur
```

Vous pouvez également y accéder n'importe où (dans une méthode de la classe ou en dehors) en faisant précéder l'attribut du nom de la classe.

```python
NomDeClasse.attribut
```

Si vous modifiez l'attribut en utilisant une instance, vous masquez l'attribut de classe et donnez à l'instance un nouvel attribut.

```python
instance = NomDeClasse()
instance.attribut = valeur # masque l'attribut de classe
```

### Définir une méthode d'instance

Les méthodes d'instances sont des fonctions placées à l'intérieur d'une classe. Leur premier paramètre doit être `self` qui correspond à l'instance de la classe.

```python
classe NomDeClasse:

    def une_méthode(self, paramètres...):
        instructions
```

Une fois votre classe instanciée, vous pouvez appeler les méthodes sur une instance spécifique en faisant suivre le nom de l'instance par un point `.` puis du nom de la méthode.

```python
instance = NomDeClasse()
instance.une_méthode(paramètres)
```

Vous pouvez également utiliser ne nom de classe et passer l'instance en tant que premier argument.

```python
instance = NomDeClasse()
NomDeClasse.une_méthode(instance, paramètres)
```

### Définir une méthode de classe

Les méthodes de classes sont des fonctions placées à l'intérieur d'une classe et possédant le décorateur `@classmethod`. Leur premier paramètre doit être `cls` qui correspond à  la classe.

```python
classe NomDeClasse:

    @classmethod
    def une_méthode(cls, paramètres...):
        instructions
```

### Définir un constructeur

Un constructeur est une méthode spéciale qui crée une instance d'une classe. Cette méthode doit être nommée __init__ :

```python
class NomDeClasse:

    def __init__(self, paramètres...):
        instructions
```

### Héritage

Pour dériver une nouvelle classe d'une ou de plusieurs autres classes, passez leur nom entre parenthèses :

```python
class SousClasse(SuperClasse1, SuperClasse2, ...):
    pass
```

La sous-classe possède alors tous les attributs des super-classes.

Vous pouvez également appeler le constructeur de la classe parent.

```python
classe SousClasse(SuperClasse):

    def __init__(self):
        super().__init__()
```

## Module pickle

```python
import pickle

score = {
    "joueur 1":    5,
    "joueur 2": 35,
    "joueur 3": 20,
    "joueur 4":    2,
}

with open('chemin/nom_de_fichier', 'wb') as fichier:
    mon_pickler = pickle.Pickler(fichier)
    mon_pickler.dump(score)

with open('chemin/nom_de_fichier', 'rb') as fichier:
    mon_depickler = pickle.Unpickler(fichier)
    score_recupere = mon_depickler.load()
```

## Module random

Importez le module random pour l'utiliser.

```python
import random
```

La fonction `randrange` renvoie un nombre entier compris entre une valeur minimale et une valeur maximale (non incluse) passées en argument :

```python
number = random.randrange(minimum, maximum)
```

La fonction `randint` renvoie un nombre entier compris entre une valeur minimale et une valeur maximale (inclus) passées en argument :

```python
number = random.randint(minimum, maximum)
```

La fonction `choice` renvoie un élément d'un objet itérable :

```python
element = random.choice(iterable)
```

La fonction `shuffle` mélange l'ordre des éléments d'une séquence :

```python
random.shuffle(sequence)
```

**Attention !** Cette fonction ne retourne pas de valeur mais modifie la séquence d'origine.

## Fichiers

### Ouvrir un fichier

La fonction `open` ouvre un fichier texte et renvoie une référence à ce fichier :

```python
fichier = open('chemin/nom_de_fichier.txt')
```

**Attention !** Pensez bien à toujours fermer le fichier après utilisation.

Par défaut, cela ouvre le fichier en lecture uniquement. Vous ne pouvez donc pas enregistrer de modifications. Passez en argument la valeur `'r'` à l'attribut `mode` pour demander explicitement l'ouverture en lecture du fichier.

```python
fichier_en_lecture = open('chemin/nom_de_fichier.txt', mode='r')
```

Passez en argument la valeur `'w'` à l'attribut `mode` pour demander l'ouverture en écriture du fichier. Cela efface le contenu précédent du fichier ou crée un nouveau fichier s'il n'existe pas déjà.

```python
fichier_en_écriture = open('chemin/nom_de_fichier.txt', mode='w')
```

Passez en argument la valeur `'a'` à l'attribut mode pour demander l'ouverture en écriture du fichier à la suite de son contenu.

```python
fichier_en_écriture = open('chemin/nom_de_fichier.txt', mode='a')
```

**Attention !** Si le fichier n'existe pas, seul le paramètre `mode='w'` crée un un nouveau fichier. Les autres modes provoquent une erreur.

### Fermer un fichier

La méthode `close` ferme le fichier pour prévenir toute erreur :

```python
fichier.close()
```

La méthode `closed` renvoie si le fichier est bien fermé :

```python
fichier.closed()
```

Pour éviter l'oubli de cette méthode, utilisez la syntaxe suivante qui refermera automatiquement le fichier à la fin du bloc :

```python
with open('nom_de_fichier.txt') as fichier:
    instructions
```

### Se positionner dans un fichier

La méthode `seek` permet de positionner le point de lecture à l'index passé en argument :

```python
fichier.seek(index)
```

### Lire dans un fichier

Un fichier ouvert avec les paramètres par défaut ou avec l'attribut `mode='r'` permet d'accéder en lecture à son contenu.

La méthode `read` renvoie une chaîne contenant le texte depuis le point de lecture courant (par défaut le premier caractère du fichier) jusqu'au dernier caractère du fichier et positionne le point de lecture à la fin :

```python
texte = fichier.read()
```

La méthode `readlines` renvoie une liste contenant chaque ligne du texte :

```python
fichier.readlines()
```

**Attention !** Les retours à la ligne sont conservés dans la liste.

### Ecrire dans un fichier

Un fichier ouvert avec l'attribut `mode='w'` permet d'accéder en écriture au fichier et d'effacer son contenu précédent. L'attribut `mode='a'` permet d'accéder en écriture au fichier et d'ajouter du texte à la fin de son contenu.

La méthode `write` insère le texte passé en argument :

```python
fichier.write('texte')
```

**Attention !** Pensez bien à fermer le fichier après vos manipulations.

### Fichiers en mode binaire

Faites suivre la valeur de l'attribut `mode` de la valeur `b` pour demander l'ouverture en mode binaire du fichier :

```python
fichier_en_lecture = open('chemin/nom_de_fichier.txt', mode='rb')
fichier_en_écriture = open('chemin/nom_de_fichier.txt', mode='wb')
fichier_en_écriture = open('chemin/nom_de_fichier.txt', mode='ab')
```

## Exceptions

### Gérer les exceptions

```python
try:
    # code pouvant provoquer une exception
except TypeErreur:
    # si une exception de type TypeErreur se produit
else
    # s'il n'y a pas eu d'exception
finally:
    # code à exécuter quoi qu'il arrive
```

ou

```python
try:
    # code pouvant provoquer une exception
except TypeErreur as erreur:
    # si une exception de type TypeErreur se produit
else
    # s'il n'y a pas eu d'exception
finally:
    # code à exécuter quoi qu'il arrive
```

**Remarque :** Il peut y avoir plusieurs clauses `except` avec un type d'erreur différent.

### Lever une exception

A tout moment, vous pouvez lever une exception avec le mot clé `raise`.

```python
raise TypeErreur
```

ou

```python
raise TypeErreur('Message d\'erreur.')
```

## Module json

Ecrire dans un fichier json.

```python
json.dump()
```

Lire dans un fichier json.

```python
json.load()
```

Mettre à jour un fichier json.

```python
json.update()
```

## Module csv

Par défaut, le package `csv` est inclut avec Python. Vous pouvez directement importer le module :

```python
import csv
```

### Ouvrir un fichier CSV

Ouvrez un fichier CSV en lecture et créez un objet `reader`.

```python
with open('nom_fichier.csv') as fichier_csv:
    csv_reader = csv.reader(fichier_csv)
```

**Attention !** Vous ne pouvez manipuler cet objet que tant que le fichier est ouvert. Pensez à garder votre codé indenté dans la clause `with`.

Itérer sur l'objet reader vous permet d'obtenir une liste de chaque élément (de type string) pour chaque ligne du fichier CSV.

```python
csv_list = []
for line in csv_reader:
    csv_list.append(line)
```

Pour éviter de récupérer la première ligne contenant les noms de chaque colonne, utilisez la fonction `next` avant d'itérer sur l'objet.

```python
noms_colonne = next(csv_reader)
for line in csv_reader:
    print(line)
```

Si vous utiliser un objet `DictReader` au lieu d'un objet `reader`, les éléments générés sont de type `OrderedDict` avec les clés prises sur la première ligne du fichier CSV.

```python
with open('nom_fichier.csv') as fichier_csv:
    csv_dict_reader = csv.DictReader(fichier_csv)
    for line in csv_dict_reader:
        print(line)
```

### Créer un fichier CSV

Ouvrez un fichier en écriture et créez un objet `writer`.

```python
with open('nom_fichier.csv', r='w') as fichier_csv:
    csv_writer = csv.writer(fichier_csv, delimiter=',')

    for line in csv_list:
        csv_writer.writerow(line)
```

Vous pouvez également utiliser un objet `DictWriter`. Dans ce cas, vous devez fournir les noms de colonnes dans une liste.

```python
nom_colonnes = ['nom_colonne1', 'nom_colonne2']
with open('nom_fichier.csv', r='w') as fichier_csv:
    csv_writer = csv.DictWriter(fichier_csv, fieldnames=nom_colonnes, delimiter=',')
    csv.writer.writeheader()

    for line in csv_list:
        csv_writer.writerow(line)
```

## Module pandas

### Importer le module

Commencez par installer le package.

Ensuite, importez le module :

```python
import pandas
```

Le module pandas utilise deux types de données :

- `DataFrame` est une structure représentant un tableau à deux dimensions.
- `Series` est une structure représentant un tableau à une dimension. Par exemple, une colonne ou une ligne de DataFrame.

```python
liste = [1, 2, 3, 4]
data_frame = pandas.DataFrame(liste)
```

```python
liste = data_frame['nom_colonne'].to_list()
```

```python
dictionnaire = {
    'eleve': ['Patrick', 'Michael', 'David'],
    'note': [15, 17, 18],
}
data_frame = pandas.DataDrame(dictionnaire)
```

```python
doctionnaire = data_frame.to_dict()
```

### pandas et fichiers CSV

Convertir un fichier CSV en DataFrame.

```python
data_frame = pandas.read_csv('nom_fichier.csv')
```

Créer un fichier CSV depuis un DataFrame.

```python
data_frame.to_csv('nom_fichier.csv')
```

### Itération

```python
for (key, value) in data_frame.items():
    print(key)
    print(value)
```

```python
for (index, row) in data_frame.iterrows():
    print(index)
    print(row)
    print(row['eleve'])
```

## Tests unitaires

Créez un fichier avec le préfixe `test_` puis importez le module préinstallé `unittest`.

```python
import unittest
```

Importez le module à tester.

```python
import calc
```

Créez une classe qui hérite de la classe `TestCase` du module `unittest`.

```python
class TestCalc(unittest.TestCase):
    pass
```

Les méthodes de cette classe doivent avoir le préfixe `test_`.

```python
class TestCalc(unittest.TestCase):
    def test_add(self):
        self.assert_equal(calc.add(10, 5), 15)
```

Ces méthodes peuvent utiliser les [méthodes de la classe `TestCase`](https://docs.python.org/3/library/unittest.html#unittest.TestCase.debug).

Pour tester les méthodes, passez le nom du ficher au module `unittest` dans la console.

```
python -m unittest test_calc.py
```

Vous pouvez également ajouter les lignes suivantes pour exécuter les tests directement avec le fichier source (par exemple depuis votre IDE).

```python
if __name__ == '__main__':
    unittest.main()
```

## Sites pour pratiquer Python

- [http://codingbat.com/python](Exercices basiques).
- [https://projecteuler.net/archives](Exercices plus difficiles autour des mathématiques).
- [http://www.codeabbey.com/index/task_list](Liste de problèmes pour s'exercer).
- [https://www.reddit.com/r/dailyprogrammer](reddit.com/dailyprogrammer). Un subreddit dédié à des problèmes d'entrainement quotidien.
- [http://www.pythonchallenge.com/](Python Challenge). Un site très difficile avec peu d'aide. Non recommandé aux débutants mais peut être intéressant.
- Codewars: [https://www.codewars.com/](Codewars). Un site avec de nombreux exercices et la possibilité de regarder les propositions des autres membres.
