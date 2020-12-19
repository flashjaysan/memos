# Mémo Java

par *flashjaysan*

## Documentation

La documentation [Java SE](http://docs.oracle.com/javase)

La documentation [Java EE](http://docs.oracle.com/javaee)

## Installation

Si vous souhaitez **exécuter** des applications Java, vous devez installer le [Java Runtime Environment](https://www.java.com/fr/download) (*JRE*). En revanche, si vous souhaitez **développer** des applications Java, vous devez installer le *Java Development Kit* (*JDK*) qui inclut également le *JRE*. Il existe plusieurs versions du *JDK* :

- *Oracle* fournit la [version officielle de Java](https://www.oracle.com/technetwork/java/javase/downloads/index.html) mais depuis la version 11, *Java* est sous une license qui nécessite un abonnement payant si vous développez des applications commerciales.
- [OpenJDK](https://jdk.java.net) est une version libre (license GNU GPL v2) et *open source* du *JRE*.
- [Amazon Corretto](https://aws.amazon.com/fr/corretto) est basé sur *OpenGDK* mais avec un support à long terme (*LTS*).

## Jshell

Comme pour le langage *Python*, *Java* fournit désormais un environnement de test en ligne de commande. Exécutez *Jshell* depuis votre terminal.

```
jshell -v
```

Vous pouvez alors saisir des commandes *Java* pour tester rapidement leur effet.

## IDEs

- *Eclipse Foundation* [Eclipse](https://www.eclipse.org/downloads).
- *JetBrains* [IntelliJ IDEA](https://www.jetbrains.com/idea/download).
- *Microsoft* [Visual Studio Code](https://code.visualstudio.com) (*VS Code*).

## Point d'entrée

Vous devez créer une classe (de préférence publique) comportant une méthode `Main` avec la signature suivante :

```java
public class Program
{
    public static void main(String[] args)
    {

    }
}
```

**Remarque :** Le point d'entrée en Java ne renvoie aucune valeur de retour. Par défaut, lorsque l'application se termine, elle renvoie la valeur `0` à l'environnement d'exécution. Utilisez la méthode `System.exit` pour renvoyer une valeur entière spécifique.

## Commentaires

```java
// commentaire sur une ligne
```

```java
/*
commentaire
multi-lignes
*/
```

```java
/**
commentaire javadoc
*/
```

**Attention !** Les commentaires multi-lignes ne s'imbriquent pas. Le commentaire s'arrête à la première occurrence `*/`. Soyez vigilant lorsque vous souhaitez commenter temporairement un bloc de code par ce moyen. Pour éviter cela, utilisez la fonctionnalité de votre IDE pour commenter un bloc de code par des commentaires sur une ligne ou commentez votre code uniquement avec des commentaires sur une ligne.

## Types de base

```java
byte byteValue; // entier signé sur un octet
short shortValue; // entier signé sur deux octets
int intValue; // entier signé sur quatre octets
long longValue; // entier signé sur huit octets (utilisez le suffixe L sur les littéraux)
float floatValue = 0.1f; // nombre à virgule flottante sur quatre octets (utilisez le suffixe F sur les littéraux)
double doubleValue = 0.1d; // nombre à virgule flottante sur huit octets (utilisez le suffixe D sur les littéraux)
boolean booleanValue = true; // valeur booléenne (true ou false)
char charValue = 'a'; // caractère unicode entre guillemets simples
```

Les données de types de base ne sont pas des références. Pour cela, vous devez utiliser les classes *wrapper* associées.

```java
Integer integerOne = new Integer(1);
Integer integerTwo = 2;
Integer integerThree = Integer.valueOf(3);
int intOne = integerOne;
int intTwo = integerTwo.intValue();
```

Vous pouvez convertir un type numérique vers un autre avec l'opérateur de cast.

```java
int intValue = 10;
short shortValue = (short) intValue;
```

La méthode `valueOf` de la classe `String` et des classes *wrapper* pour les types de base (`Byte`, `Short`, `Integer`, `Long`, `Float`, `Double`) permet de convertir une donnée en un autre type. Chacune de ces classes *wrapper* possède une méthode `*primitiveType*Value` qui retourne la valeur du type de base contenue dans l'objet.

```java
Integer integer = Integer.valueOf(5);
int intValue = integer.intValue();
byte byteValue = 5;
String stringByte;
stringByte.valueOf(byteValue);
byte byteValue = Integer.valueOf(stringByte).intValue();
```

## Pseudo constantes

Une variable déclarée avec le mot clé `final` ne peut plus être modifiée après sa première initialisation.

```java
final int TEN = 10;
TEN = 10; // erreur
```

**Remarque :** Il est possible de retarder l'initialisation. En effet, le mot clé `final` indique seulement à Java que la variable ne peut être initialisée qu'une seule fois. Vous pouvez donc l'initialiser avec une valeur saisie par l'utilisateur lors de l'exécution.

```java
final int TWENTY;
// instructions
TWENTY = 10;
```

## Opérateurs

```java
// opérateurs algébriques
int a = 5;
int b = 3;
int somme = a + b;
int difference = a - b;
int product = a * b;
int division = a / b;
int remainder = a % b;
a += 7; // a = a + 7;
a -= 7; // a = a - 7;
a *= 7; // a = a * 7;
a /= 7; // a = a / 7;
a %= 7; // a = a % 7;
a++; // renvoie l'ancienne valeur de a puis l'augmente de 1
++a; // augmente la valeur de a de 1 et renvoie sa nouvelle valeur
// opérateurs de comparaison
boolean less = a < b;
boolean lessOrEqual = a <= b;
boolean greater = a > b;
boolean greaterOrEqual = a >= b;
boolean equals = a == b;
boolean different = a != b;
// opérateurs logiques
boolean isTrue = true;
boolean isFalse = false;
boolean and = isTrue && isFalse; // ET logique
boolean or = isTrue || isFalse; // OU logique
boolean not = !isTrue; // NON logique
```

**Attention !** Les opérateurs ont des priorités différentes. En cas de doute, utilisez des parenthèses pour être plus explicite.

**Remarque :** Java fournit également des opérateurs de manipulation de bits. Consultez la documentation pour plus d'informations. En pratique, il est rarement utile de s'en servir en Java.

## Type String

```java
String stringValue = "Some text."; // caractères unicode entre guillemets doubles
String anotherStringValue = new String("Another text."); // appel du constructeur
```

La méthode `charAt` renvoie le caractère situé à l'indice spécifié.

```java
char charValue = stringValue.chatAt(0); // renvoie le premier caractère de la chaîne
```

La méthode `length` renvoie le nombre de caractères contenus dans la chaîne.

```java
stringValue.length(); // renvoie le nombre de caractères
```

La méthode `toLowerCase` renvoie une chaîne constituée uniquement de minuscules.

```java
String stringValue = "Mickey et Dingo";
System.out.println(stringValue.toLowerCase()); // affiche "mickey et dingo"
```

La méthode `toUpperCase` renvoie une chaîne constituée uniquement de minuscules.

```java
String stringValue = "Mickey et Dingo";
System.out.println(stringValue.toUpperCase()); // affiche "MICKEY ET DINGO"
```

La méthode `equals` indique si deux chaînes sont identiques. N'utilisez pas l'opérateur `==` pour les chaînes.

```java
String stringValue1 = "Mickey et Dingo";
String stringValue2 = "Mickey et Dingo";
stringValue.equals(stringValue2)); // renvoie true
```

La méthode `substring` renvoie une sous-chaîne d'une chaîne.

```java
String stringValue = "Mickey et Dingo";
stringValue.substring(10, 15); // renvoie "Dingo"
```

La méthode `indexOf` renvoie l'indice de la première occurrence d'une sous-chaîne située dans la chaîne en partant du début.

```java
String stringValue = "Mickey et Dingo et Donald";
stringValue.indexOf("et"); // renvoie 7
```

La méthode `lastIndexOf` renvoie l'indice de la premième occurrence d'une sous-chaîne située dans la chaîne en partant de la fin.

```java
String stringValue = "Mickey et Dingo et Donald";
stringValue.lastIndexOf("et"); // renvoie 16
```

## Fonctions mathématiques

La classe `Math` située dans le paquetage `java.lang` (automatiquement importé), fournit de nombreuses méthodes de classe pour les calculs mathématiques.

[`java.lang.Math`](https://docs.oracle.com/en/java/javase/13/docs/api/java.base/java/lang/Math.html)

```java
double angle = Math.PI; // renvoie la valeur de PI en radians
Math.cos(angle); // calcule le cosinus d'un angle en radians
Math.sin(angle); // calcule le sinus d'un angle en radians
Math.random(); // renvoie un nombre compris en 0 et 1
```

## Afficher du texte

```java
System.out.print("Some text."); // affiche le texte
System.out.println("Another text."); // affiche le texte et revient à la ligne
```

## Afficher les types de base ou les objets

Pour les types de base, utilisez simplement `System.out.print` ou `System.out.println`.

```java
int intValue = 10;
double doubleValue = 10.01d;
System.out.print(intValue); // affiche 10
System.out.println(doubleValue); // affiche 10.01 et revient à la ligne
```

Pour les objets, vous pouvez utiliser ces mêmes méthodes si vous avez redéfini la méthode `toString` héritée de la classe `Object`.

```java
public class SomeClass
{
    public int intValue;

    public SomeClass()
    {
        intValue = 99;
    }

    public String toString()
    {
        return Integer.toString(intValue);
    }
}
```

```java
SomeClass someClass = new SomeClass();
System.out.println(someClass); // affiche 99
```

## Récupérer les saisies utilisateur

Commencez par importer la classe [`java.util.Scanner`](https://docs.oracle.com/en/java/javase/13/docs/api/java.base/java/util/Scanner.html).

```java
import java.util.Scanner;
```

Créez une instance de la classe `Scanner` en lui passant l'entrée standard `System.in`.

```java
Scanner scanner = new Scanner(System.in);
```

Vous pouvez à présent appeler les méthodes de cet objet.

La méthode `nextLine` renvoie une chaîne saisie depuis la console.

```java
String userInput = scanner.nextLine();
```

Les méthodes `nextInt`, `nextDouble`, etc... à l'exception du type `char` renvoient une donnée saisie depuis la console.

```java
boolean booleanValue = scanner.nextBoolean();
byte byteValue = scanner.nextByte();
short shortValue = scanner.nextShort();
int intValue = scanner.nextInt();
long longValue = scanner.nextLong();
float floatValue = scanner.nextFloat();
double doubleValue = scanner.nextDouble();
```

**Remarque :** Ces méthodes peuvent provoquer une exception si l'utilisateur saisie une chaîne impossible à convertir dans le type attendu. Utilisez la série de méthode `hasNext...` pour vérifier si une saisie utilisateur peut-être convertie dans un type spécifique.

```java
if (scanner.hasNextInt())
{
    int intValue = scanner.nextInt();
}
else
{
    System.out.println("Saisie incorrecte.");
    scanner.nextLine(); // vidage du tampon pour effacer la saisie précédente
}
```

**Attention !** Si vous souhaitez récupérer une saisie numérique après une saisie chaîne ou une saisie erronnée, videz le tampon. Pour cela appelez simplement la méthode `nextLine` à vide.

Une fois la saisie utilisateur terminée, vous pouvez fermer l'objet `Scanner` avec la méthode `close`. Vous ne pouvez plus appeler de méthodes `next...` sur l'objet `Scanner` après avoir appelé cette méthode.

```java
scanner.close();
```

## conventions

Il est conseillé de définir les noms de classes et interfaces en `PascalCase`, les noms de variables locales, de membres de classes et de méthodes en `camelCase`, les variables et les membres contants en `ALL_CAPS` et les noms de paquetages en `minuscules`. Les acronymes respectent cette convention (seul le premier caractère peut être écrit en majuscule).

## Structures de contrôle

### Branchement conditionnel

```java
if (condition)
{
    // instructions 
}
```

```java
if (condition)
{
    // instructions 
}
else
{
    // instructions par défaut
}
```

```java
if (condition1)
{
    // instructions 1
}
else if (condition2)
{
    // instructions 2
}
else
{
    // instructions par défaut
}
```

```java
switch (expression)
{
    case valeur1:
        // instructions 1
        break;
    case valeur2:
        // instructions 2
        break;
    default:
        // instructions par défaut
}
```

### Boucle

```java
while (condition)
{
    // instructions
}
```

```java
do
{
    // instructions
}
while (condition);
```

```java
for (int i = 0; i < 10; ++i)
{
    // instructions
}
```

Java fournit également une construction `for` spéciale pour itérer sur un tableau ou des collections implémentant l'interface `Iterable`.

```java
for (typeElement item : collection)
{
    // instructions
}
```

## Tableaux

Un tableau ne peut contenir que des éléments de même type. Utilisez les crochets à la suite d'un type primitif ou une classe pour déclarer un tableau d'éléments de ce type.

```java
int[] intArray;
double[] doubleArray;
String[] stringArray;
```

Vous pouvez également placer les crochets après le nom de la variable mais la lecture du type en est plus difficile. C'est une pratique déconseillée.

```java
int intArray[];
```

Pour créer une instance d'un tableau, utilisez le mot-clé `new` suivi du type et de crochets avec un nombre d'éléments. Ce nombre ne peut plus être modifié par la suite.

```java
int[] intArray = new int[5];
double[] doubleArray = new double[10];
String[] stringArray = new String[15];
```

Lors de la déclaration, vous pouvez également utiliser une suite de valeur séparées par des virgules et entre accolades.

```java
int[] intArray = {0, 1, 2, 3, 4};
double[] doubleArray = {.1, .2, .3, .4, .5};
String[] stringArray = {"Marc", "David", "Laurie", "Marie"};
```

**Attention !** La forme avec les accolades ne peut pas être utilisée après la déclaration du tableau mais vous pouvez toujours créer un nouveau tableau avec le mot clé `new`.

```java
int[] intArray;
intArray = {1, 2, 3, 4, 5}; // erreur
intArray = new int[] {1, 2, 3, 4, 5}; // OK
```

La propriété `length` (attention, ce n'est pas une méthode) indique le nombre d'éléments d'un tableau.

```java
for (int i = 0; i < intArray.length; ++i)
{
    // instructions
}
```

Pour accéder à un élément, utilisez un indice entre crochets.

```java
int[] intArray = {0, 1, 2, 3, 4};
System.out.println(intArray[2]); // affiche 2
intArray[2] = 5;
System.out.println(intArray[2]); // affiche 5
```

**Attention !** L'indice du premier élément d'un tableau est `0`. L'indice du dernier élément d'un tableau est donc `tableau.length - 1`. Accéder à un élément au delà des limites provoque une erreur.

```java
int[] intArray = {0, 1, 2, 3, 4};
System.out.println(intArray[0]); // affiche 0
System.out.println(intArray[intArray.length - 1]); // affiche 4
System.out.println(intArray[intArray.length]); // erreur
```

Pour parcourir un tableau, une boucle `for` est idéale.

```java
for (int i = 0; i < intArray.length; ++i)
{
    System.out.println(intArray[i]);
}
```

Pour un parcours complet d'un tableau, l'instruction `for` autorise également la construction suivante, plus concise et moins sujette à erreur.

```java
for (int intValue: intArray)
{
    System.out.println(intValue);
}
```

### Trier un tableau

La méthode `sort` de la classe `.Arrays` du package `java.util` permet de trier un tableau passé en argument.

```java
java.util.Arrays(intArray);
```

**Remarque :** Vous pouvez utiliser cette méthode avec un tableau de n'importe quel type à partir du moment où ce dernier implémente l'interface `Comparable`.

### Trouver la valeur minimale, maximale et la moyenne des éléments d'un tableau

La classe `Arrays` du package `java.util` vous permet de convertir l'ensemble des éléments d'un tableau en flux via sa méthode statique `stream`. Vous pouvez ensuite appeler les méthodes `min`, `max` et `average` pour obtenir une option contenant la valeur. Utilisez alors la méthode `getAsNomDuType` pour obtenir la valeur effective.

```java
int min = Arrays.stream(intArray).min().getAsInt();
int max = Arrays.stream(intArray).max().getAsInt();
double avg = Arrays.stream(doubleArray).average().getAsDouble();
```

### Afficher un tableau

La méthode statique `Arrays.toString` du package `java.util` affiche le contenu d'un tableau.

```java
int[] array = {1, 2, 3, 4, 5};
System.out.println(Arrays.toString(array));
```

### Copier un tableau

Les méthodes statiques `copyOf` de la classe `Arrays` du package `java.util` renvoie une copie d'un tableau.

```java
int[] array = {5, 10, 15, 20};
int[] newArray = Arrays.copyOf(array, array.length);
```

**Attention !** Cette méthode effectue une copie en surface. Pour les types primitifs, cela ne pose pas de problème mais pour des tableaux d'objets, cela implique une copie des références à ces objets.

Vous pouvez également utiliser cette méthode pour créer un tableau plus grand. Les éléments supplémentaires sont initialisés à la valeur par défaut de leur type.

```java
int[] array = {5, 10, 15, 20};
int[] newArray = Arrays.copyOf(array, array.length + 2);
```

## ArrayList

La classe [`ArrayList`](https://docs.oracle.com/en/java/javase/13/docs/api/java.base/java/util/ArrayList.html), située dans le package `java.util`, permet de créer et de gérer une structure de donnée similaire à un tableau mais dont le nombre d'éléments peut varier.

Pour créer un objet de type `ArrayList`, utilisez le constructeur en précisant le type.

```java
import java.util.ArrayList;
ArrayList<String> stringArrayList = new ArrayList<String>();
```

**Attention !** Vous ne pouvez pas utiliser un type de base. Pour ça, utilisez les classes *wrapper*.

```java
import java.util.ArrayList;
ArrayList<Integer> intArrayList = new ArrayList<Integer>();
```

Utilisez la méthode `add` pour ajouter un élément.

```java
stringArrayList.add("Bonjour.");
intArrayList.add(Integer.valueOf(10));
```

Pour accéder à un élément, utiliser la méthode `get` avec l'indice de l'élément.

```java
String stringValue = stringArrayList.get(0);
int intValue = intArrayList.get(0).intValue();
```

## LinkedList

```java
import java.util.LinkedList;
import java.util.Iterator;
LinkedList<String> stringLinkedList = new LinkedList<String>();
stringLinkedList.add("Bonjour.");
stringLinkedList.add("Hello.");
stringLinkedList.add(1, "Guten tag.");
Iterator<String> i = stringLinkedList.iterator();
while (i.hasNext())
{
    System.out.println(i.next());
}
```

## Quand utiliser un `ListIterator` à la place d'un `Iterator` ?

Si vous avez besoin de revenir à un élément précédent, ou d'obtenir l'index d'un élément, utilisez un `ListIterator`.

```java
import java.util.LinkedList;
import java.util.LisrIterator;
LinkedList<String> stringLinkedList = new LinkedList<String>();
stringLinkedList.add("Bonjour.");
stringLinkedList.add("Hello.");
stringLinkedList.add(1, "Guten tag.");
ListIterator<String> i = stringLinkedList.iterator();
i.next();
i.previous();
i.get();
```

## Parcourir une collection avec une boucle `for`

```java
for (String string : stringLinkedList) {
    System.out.println(string);
}
```

## Classes

```java
public class SomeClass
{
    // déclaraction d'une variable d'instance
    private type nomDeVariable;

    // déclaration d'une variable de classe
    private static type nomDeVariable;

    // déclaration d'une méthode d'instance
    public type nomDeMéthode()
    {
        // instructions
    }

    // déclaration d'une méthode de classe
    public static type nomDeMéthode()
    {
        // instructions
    }

}
```

### Constructeurs

Un constructeur est une méthode qui n'a aucun type de retour et qui porte le même nom que la classe. Lorsque le comiplateur rencontre une classe sans constructeur, il génère automatiquement un constructeur par défaut sans paramètre. Vous pouvez ainsi appeler le constructeur d'une classe n'en possédant pas pour créer un objet de cette classe. En revanche, à partir du moment où vous définissez au moins un constructeur, le compilateur ne génère plus ce constructeur par défaut.

```java
public class SomeClass
{
    public SomeClass() // constructeur par défaut
    {

    }

    public SomeClass(NomDeType nomDeParametre, ...) // constructeur avec paramètres
    {

    }
}
```

Vous pouvez ensuite créer des instances de la classe grâce au mot clé `new`.

```java
SomeClass someClass1 = new SomeClass(); // appel au constructeur par défaut
SomeClass someClass2 = new SomeClass(argument); // appel au constructeur avec paramètres
```

### le mot clé this

Le mot clé `this` permet de faire référence à l'objet courant. Il peut être utilisé pour appeler un membre de l'objet ou une de ses méthodes depuis une autre méthode de cet objet (y compris le constructeur).

```java
public class SomeClass
{
    private int intValue;
    private int otherIntValue;

    public SomeClass(int intValue)
    {
        this.intValue = intValue;
        this.setOtherIntValue();
    }

    private void setOtherIntValue()
    {
        this.otherIntValue = this.intValue;
    }
}
```

Vous pouvez également appeler un autre constructeur depuis un constructeur avec l'appel `this()`. Cependant, cet appel doit être la première instruction du constructeur.

```java
public class SomeClass
{
    private int intValue;

    public SomeClass(int intValue)
    {
        this.intValue = intValue;
    }

    public SomeClass()
    {
        this(0); // appel du premier constructeur avec une valeur par défaut
        // autres instructions
    }
}
```

### Héritage

Une sous-classe peut étendre une classe parent pour lui ajouter des fonctionnalités. Vous pouvez ajouter de nouveaux membres et de nouvelles méthodes. Utilisez le mot clé `extends` pour définir une sous-classe d'une autre classe.

Une sous-classe peut également redéfinir une méthode de sa classe parent (même nom et même paramètres) à condition que la méthode soit déclarée `public` ou `protected` dans la classe parent. Pour un code plus sûr, vous pouvez ajouter une annotation `@Override` pour signaler explicitement au compilateur que vous redéfinissez une méthode dans une sous-classe.

Vous pouvez appeler une méthode de la classe parent avec l'appel `super()` depuis la méthode de la classe enfant. Cependant, cet appel doit être la première instruction de la méthode.

Lors de l'instanciation d'un objet de la sous-classe, si vous n'appelez pas explicitement le constructeur de la classe parent dans le constructeur de la sous-classe, le compilateur ajoute automatiquement un appel au constructeur sans argument de la classe parent. Si la classe parent ne définit que des constructeurs avec au moins un paramètre, une erreur se produit à la compilation.

```java
public class Parent
{
    public Parent()
    {

    }

    protected void someMethod()
    {

    }
}


public class Child extends Parent
{
    public Child()
    {
        super();
        // instructions
    }

    @Override
    public void someMethod()
    {
        super.someMethod();
        // instructions
    }
}
```

### Méthodes finales

Une méthode définie avec le mot clé `final` ne peut être étendue dans une sous-classe.

```java
public class Parent
{
    public final void someFinalMethod()
    {

    }
}


public class Child extends Parent
{
    public void someFinalMethod() // erreur
    {

    }
}
```

### Classes finales

Les classes finales n'ont que des méthodes finales. Elles ne peuvent pas posséder de sous-classe.

### Classe abstraite

Une classe abstraite est une classe possédant une ou plusieurs méthodes qui ne sont pas implémentées (qui ne possèdent qu'une signature / n'ont pas de corps). Ce type de classe ne peut pas être instanciée directement. Vous devez étendre cette classe dans une sous-classe et implémenter ses méthodes abstraites. Une telle sous-classe peut-être instanciée.

```java
public abstract class AbstractClass
{
    abstract public type someMethod();
}
```

### Interfaces

Une interface est l'équivalent d'une classe abstraite dont toutes les méthodes sont abstraites. De plus, une sous classe peut étendre (on dit *implémenter*) plusieurs interfaces tout en étendant une seule classe parent. Utilisez le mot-clé `implements` pour implémenter une interface dans une classe.

```java
public interface SomeInterface
{
    public type someMethod();
}


class ImplementsSomeInterface implements SomeInterface
{
    public type someMethod()
    {
        // instructions
    }
}
```

### Surcharge de méthode

Une classe peut surcharger une méthode définie dans sa propre classe ou une classe parent en réutilisant son nom mais en définissant une autre signature (avec différents arguments (en nombre ou en type)).

### Surdéfinition de méthode

Une classe enfant peut redéfinir une méthode d'instance (**pas statique**) d'une classe parent si elle possède les mêmes arguments (en nombre et en type). Avant de redéfinir la méthode, placez l'annotation `@Override`. Le type de retour doit être le même que la classe parent ou d'un de ses sous-types. Elle ne peut pas réduire l'éccessibilité de la méthode d'origine.

```java
public class Parent
{
    protected void someMethod()
    {

    }
}


public class Child extends Parent
{
    @Override
    public void someMethod()
    {
        super.someMethod();
        // instructions
    }
}
```



