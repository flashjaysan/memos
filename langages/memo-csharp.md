# Mémo C#

*par flashjaysan*

## Introduction



## Installation

**Nouveau !**

### Visual Studio Code

Téléchargez et installez la [dernière version de .NET SDK](https://dotnet.microsoft.com/en-us/download). Vérifiez que l'installation s'est bien déroulée en saisissant `dotnet --version` dans un terminal.

Téléchargez et installez [Visual Studio Code](https://code.visualstudio.com/). Installez l'extension `C#` de Microsoft.

### Installation de Visual Studio

Installez la dernière version de `Microsoft Visual Studio`. Pensez à cocher la charge de travail `Développement .NET Desktop`.

**Remarque :** Si vous avez déjà installé Visual Studio sans cette charge de travail, démarrez `Visual Studio Installer`. Sous la version de Visual Studio déjà installée, cliquez sur le bouton `Modifier` puis installez la charge de travail `Développement .NET Desktop`.

## Créer un nouveau projet

**Nouveau !**

### Visual Studio Code

- Créez un dossier pour votre projet.
- Ouvrez un terminal à l'emplacement du dossier.
- Saisissez la commande `dotnet new console`.
- Ouvrez le dossier dans VS Code (se placer dans le dossier, et saisir la commande `code .`).
- Cliquez sur l'option `Yes` dans la boite de dialogue `"Required assets to build and debug are missing. Add them?"`.
- Ouvrez un terminal dans VS Code et saisissez `dotnet run`.


### Visual Studio

Dans Visual Studio, cliquez sur le menu `Fichier -> Nouveau -> Projet...` (`Ctrl+Maj+N`) ou cliquez sur le texte `Créer un projet...` dans l'écran de démarrage de Visual Studio.

- Sélectionnez l'option `Application console (.NET framework)`.
- Saisissez le nom de votre projet dans le champ `Nom`.
- Sélectionnez un emplacement dans le champ `Emplacement`.
- Saisissez le nom de la solution dans le champ `Nom de solution`.

**Remarque :** Une solution peut contenir plusieurs projets.

## Ajouter un nouveau projet à une solution

Dans le panneau `Explorateur de solutions`, faites un clic droit sur la solution et choisissez l'option `Ajouter -> Nouveau projet...`.

## Conventions de styles

- Les noms de classes et de méthodes sont écrits en `PascalCase`.
- Les noms de variables locales (définies dans une méthode) sont écrits en `camelCase`.
- Les noms de classes sont contitués de noms.
- Les noms de méthodes sont constitués de verbes.

## Point d'entrée

La méthode statique `Main` définit le point d'entrée d'un programme. On la place généralement dans une classe `Program`. Elle peut ne rien renvoyer ou renvoyer un entier. Elle peut ne prendre aucun paramètre ou un tableau de chaine de caractères.

```csharp
public class Program
{
    public static void Main()
    {

    }
}
```

ou

```csharp
public class Program
{
    public static void Main(string[] args)
    {

    }
}
```

ou

```csharp
public class Program
{
    public static int Main()
    {

    }
}
```

ou

```csharp
public class Program
{
    public static int Main(string[] args)
    {

    }
}
```

## Afficher du texte dans la console

Utilisez la méthode `WriteLine` de la classe `System.Console` pour afficher une chaine de caractères puis retourner à la ligne.

```csharp
System.Console.WriteLine("Texte à afficher.");
```

**Remarque :** Vous pouvez utiliser le raccourci `cw`, `Tab`, `Tab` pour appeler cette méthode automatiquement dans Visual Studio.

Utilisez la méthode `Write` si vous ne souhaitez pas un retour à la ligne après l'affichage de la chaine de caractères.

```csharp
System.Console.Write("Texte à afficher.");
```

## Lire une saisie de l'utilisateur dans la console

Utilisez la méthode `ReadLine` de la classe `System.Console` pour lire une chaine de caractères saisie par l'utilisateur. Cette méthode renvoie une chaine que vous devez donc utiliser (par exemple, la stocker dans une variable).

```csharp
string userMessage = System.Console.ReadLine();
```

**Attention !** Les méthodes `Write...` et `Read...` ne sont pas symétriques. La méthode `Read` renvoie l'entier associé à un seul caratère saisi. La méthode `ReadKey` renvoie le caractère associé à l'appui d'une touche du clavier.

## Utiliser un espace de nommage

Utilisez le mot clé `using` pour utiliser un espace de nommage . (directive ?)

```csharp
using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Texte à afficher.");
    }
}
```

## Définir un espace de nommage

Utilisez le mot clé `namespace` pour définir un espace de nommage.

```csharp
namespace NomEspaceNommage
{

}
```

## Commentaires

Il y a quatre types de commentaires.

```csharp
// commentaire de ligne

/*
commentaire
multi-lignes
*/

/// commentaire de documentation de ligne

/**
commentaire de documentation multi-ligne
**/
```

## Déclarer une variable

Une variable se déclare en faisant précéder son nom (ou identificateur) par son type. La variable peut être initialisée lors de sa déclaration.

```
type identificateurVariable;
type identificateurVariable = valeurInitiale;
```

Exemple :

```csharp
class Program
{
    // déclaration de variable d'instance
    int VariableInstance;

    // déclaration de variable de classe
    static int VariableDeClasse;

    static void Main()
    {
        // déclaration de variables locales à une méthode
        int variableLocaleNonInitialisee;
        int variableLocaleInitialisee = 10;
        int variableLocale1, variableLocale2 = 20;
    }
}
```

## Types primitifs

### Type booléen

`bool`

### Type charactère

`char`

### Types numériques entiers

C# fournit les types primitifs suivants :

- `sbyte` (équivalent à `System.SByte`) est un type entier signé codé sur 8 bits.
  - `sbyte.MaxValue` contient la plus grande valeur possible dans ce type (`127`).
  - `sbyte.MinValue` contient la plus petite valeur possible dans ce type (`-128`).
- `byte` (équivalent à `System.Byte`) est un type entier non signé codé sur 8 bits.
  - `byte.MaxValue` contient la plus grande valeur possible dans ce type (`255`).
  - `byte.MinValue` contient la plus petite valeur possible dans ce type (`0`).
- `short` (équivalent à `System.Int16`) est un type entier signé codé sur 16 bits.
  - `short.MaxValue` contient la plus grande valeur possible dans ce type (`32_767`).
  - `short.MinValue` contient la plus petite valeur possible dans ce type (`-32_768`).
- `ushort` (équivalent à `System.UInt16`) est un type entier non signé codé sur 16 bits.
  - `ushort.MaxValue` contient la plus grande valeur possible dans ce type (`0`).
  - `ushort.MinValue` contient la plus petite valeur possible dans ce type (`65_535`).
- `int` (équivalent à `System.Int32`) est un type entier signé codé sur 32 bits.
  - `int.MaxValue` contient la plus grande valeur possible dans ce type (`2_147_483_647`).
  - `int.MinValue` contient la plus petite valeur possible dans ce type (`-2_147_483_648`).
- `uint` (équivalent à `System.UInt32`) est un type entier non signé codé sur 32 bits.
  - `uint.MaxValue` contient la plus grande valeur possible dans ce type (`4_294_967_295`).
  - `uint.MinValue` contient la plus petite valeur possible dans ce type (`0`).
- `long` (équivalent à `System.Int64`) est un type entier signé codé sur 64 bits.
  - `long.MaxValue` contient la plus grande valeur possible dans ce type (`-9_223_372_036_854_775_807`).
  - `long.MinValue` contient la plus petite valeur possible dans ce type (`-9_223_372_036_854_775_808`).
- `ulong` (équivalent à `System.UInt64`) est un type entier non signé codé sur 64 bits.
  - `ulong.MaxValue` contient la plus grande valeur possible dans ce type (`18_446_744_073_709_551_615`).
  - `ulong.MinValue` contient la plus petite valeur possible dans ce type (`0`).

**Remarque :** Le terme `non signé` indique simplement un type qui ne peut prendre que des valeurs positives.

### Types numériques à virgule flottante

`float` `double` `decimal` `BigDecimal`

### Type chaine de caractères

Le type `string` définit un objet représentant une chaine de caractères. Une fois initialisée, une chaine est immutable.

Le type `string` est une référence. Vous pouvez initialiser une variable de ce type avec `null`.

La concaténation (la fusion) de deux chaines s'effectue avec l'opérateur `+`.

```csharp
string message = "Hello, " + "World!"; // message contient "Hello, World!"

string hello = "Hello, ";
string world = "World!";
message = hello + world;
```


## Déclarer une variable

Pour déclarer une variable, vous devez utilisez la forme suivante :

```csharp
type nomDeVariable;
```

Par exemple :

```csharp
sbyte variableSbyte;
byte variableByte;
short variableShort;
ushort variableUshort;
int variableInt;
uint variableUint;
long variableLong;
ulong variableUlong;
```

## Littéraux

Un littéral est une valeur constante codée en dur dans un fichier source.

### Littéraux entiers

Vous pouvez écrire les littéraux entiers sous diverses formes :

- décimal : une séquence de chiffres compris entre `0` et `9` sans préfixe. Exemple : `123_456_789`
- binaire : (depuis C# 7.0) une séquence de chiffres `0` ou `1` préfixée par `0b` (ou `0B`). Exemple : `0b0101_1010`
- hexadécimal : une séquence de chiffres compris entre `0` et `9` ou de lettres comprises entre `A` (ou `a`) et `F` (ou `f`) et préfixée par `Ox` (ou `OX`). Exemple : `0xCAFE_0123`

**Remarque :** Comme dans les exemples précédents, depuis C# 7.0, vous pouvez séparer les chiffres par un signe `_` pour en faciliter la lecture.

Par défaut, un littéral entier est du premier type pouvant représenter sa valeur parmi `int`, `uint`, `long`, `ulong`.

En outre, vous pouvez ajouter un suffixe au littéral pour préciser son type.

- Si le littéral est suffixé par `U` ou `u`, il est du premier type pouvant représenter sa valeur parmi `uint`, `ulong`.
- Si le littéral est suffixé par `L` ou `l`, il est du premier type pouvant représenter sa valeur parmi `long`, `ulong`.
- Si le littéral est suffixé par `UL`, `Ul`, `uL`, `ul`, `LU`, `Lu`, `lU` ou `lu`, il est du type `ulong`.

**Remarque :** Utilisez plutôt les versions majuscules des suffixes pour éviter toute confusion entre la lettre `l` et le chiffre `1`.

### Littéraux flottants

Il existe plusieurs formats de littéraux flottants :

```csharp
double variableDouble = 1.234;
float variableFloat = 1.234F;
decimal variableDecimal = 1.234M;
```

### Littéraux booléens

`true` `false`

### Littéraux caractères

`'a'` `'@'` `'\''`

### Littéraux chaînes de caractères

`"Chaîne de caractères."` `"\""` `"\n"`












## Affecter une valeur à une variable

Utilisez l'opérateur `=` pour affecter une valeur à une variable. Vous pouvez le faire lors de la déclaration ou plus tard mais vous ne pouvez pas utiliser la valeur d'une variable non initialisée.

```csharp
int variableInt = 10;
int autreVariableInt = variableInt;
autreVariableInt = autreVariableInt + 1;
```




























```csharp

```

































































































































