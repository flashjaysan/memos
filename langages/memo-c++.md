# Mémo C++

*par flashjaysan*

## Installation de MinGW64

Pour compiler et tester vos programmes écrits en C++ vous avez besoin d'un compilateur. Je vous conseille d'utiliser MinGW64. La procédure est détaillée dans mon autre [mémo consacré au langage C](memo-c.md).

## Compilation dans Visual Studio Code

Si vous le souhaitez, installez l'extension `C/C++` de Microsoft.

Créez un dossier et ouvrez-le avec Visual Studio Code.

Créez un fichier `main.cpp` et saisissez le code suivant :

```cpp
#include <iostream>

int main()
{
    std::cout << "Hello, World!";
    return 0;
}
```

Pour ouvrir le terminal de Visual Studio Code, cliquez sur le menu `View -> Terminal`. Le terminal s'affiche en bas de la fenêtre.

Pour compiler le fichier source, saisissez la commande suivante :

```
g++ main.cpp
```

Aucun message n'apparait dans le terminal quand la compilation se passe bien. Cependant, un nouveau fichier exécutable a bien été généré. Dans le terminal, saisissez la commande `ls` pour afficher la liste des fichiers du dossier. Un fichier nommé `a.exe` doit être présent.

```
ls
```

![commande `ls` dans le terminal de Visual Studio Code](images/c_commande_ls_vscode.png)

Par défaut, le compilateur `g++` génère un fichier exécutable appelé `a.exe` à partir de votre fichier source. Pour l'exécuter depuis le terminal, saisissez la commande suivante :

```
.\a.exe
```

![exécution du programme test dans le terminal](images/c_premiere_execution_vscode.png)

## Point d'entrée d'un programme

La fonction `main` est généralement le point d'entrée d'un programme C++. Elle renvoie un entier à l'environnement d'exécution. Elle peut s'écrire sous deux formes.

La première forme ne prend pas de paramètre (contrairement au C, en C++, il ne faut pas préciser le mot clé `void` dans les parenthèses quand une fonction ne prend pas de paramètre).

```cpp
int main() {}
```

La seconde forme prend deux paramètres.

- Un entier (généralement nommé `argc`) qui contient soit `0` soit le nombre de chaînes contenues dans le second paramètre.
- Un tableau de pointeurs de caractères (généralement nommé `argv`) qui contient les chaînes de caractères passées au programme lors de son lancement par l'environnement d'exécution. Le premier élément correspond au nom du programme.

```cpp
int main(int argc, char* argv[]) {}
```

Cette seconde forme est utilisée lorsque le programme doit recevoir des paramètres de l'environnement d'exécution.

Par convention, un programme s'exécutant correctement se termine en renvoyant la valeur `0` à l'environnement d'exécution. Vous pouvez le préciser explicitement à la fin de la fonction `main` en utilisant l'instruction `return 0;`.

```cpp
int main()
{
    return 0;
}
```

Cette instruction n'est pas obligatoire. Si vous ne la placez pas dans votre programme, le compilateur considère par défaut que le programme renvoie la valeur `0`.

Pour plus de clarté, vous pouvez également renvoyer la constante `EXIT_SUCCESS` définie dans le fichier en-tête `cstdlib`.

```cpp
#include <cstdlib>

int main()
{
    return EXIT_SUCCESS;
}
```

**Remarque :** En cas de besoin, vous pouvez également utiliser la constante `EXIT_FAILURE` définie dans le fichier en-tête `cstdlib` pour indiquer que le programme ne s'est pas terminé correctement.

## Compiler un fichier source et exécuter le programme

Compiler avec `g++` :

```
g++ nom_du_fichier.cpp
```

Exécuter le programme :

```
./a.exe
```

Combiner les deux :

```
g++ nom_du_fichier.cpp && ./a.exe
```

## Littéraux

Un littéral entier peut être écrit sous forme décimale :

```cpp
int nombre = 12345;
```

Un littéral caractère s'écrit entre apostrophes :

```cpp
char caractere = 'a';
```

Un littéral chaîne de caractères s'écrit entre guillemets :

```cpp
char* chaine = "bonjour";
```

**Attention !** Un littéral chaîne de caractères est de type `char*` et non de type `string`. Cependant, vous pouvez affecter automatiquement un littéral chaîne de caractères à un objet de type `string`.

Une chaîne de caractères possède un caractères de fin de chaîne `\0` en plus des caractères classiques.

Un littéral chaîne de caractères vide s'écrit avec deux guillemets :

```cpp
char* chaine_vide = "";
```

## Afficher une chaine de caractères

```cpp
#include <cstdio>
#include <cstdlib>

int main()
{
    printf("Bonjour.");
    return EXIT_SUCCESS;
}
```

```cpp
#include <cstdio>
#include <cstdlib>

int main()
{
    char* chaine = "Bonjour.";
    printf(chaine);
    return EXIT_SUCCESS;
}
```

```cpp
#include <cstdio>
#include <cstdlib>

int main()
{
    char* chaine = "Bonjour.";
    printf("%s", chaine);
    return EXIT_SUCCESS;
}
```

## Afficher un nombre entier

```cpp
#include <cstdio>
#include <cstdlib>

int main()
{
    printf("%d", 1234);
    return EXIT_SUCCESS;
}
```

```cpp
#include <cstdio>
#include <cstdlib>

int main()
{
    int entier = 1234;
    printf("%d", entier);
    return EXIT_SUCCESS;
}
```

## Commentaires

```cpp
// commentaires sur une seule ligne

/* commentaire
sur plusieurs
lignes */
```

## La fonction printf

Le premier paramètre de la fonction `printf` est **toujours** de type chaine de caractères.

- `%d` affiche le paramètre suivant de type entier sous forme décimale.
- 
