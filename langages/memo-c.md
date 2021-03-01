# Mémo C

*par flashjaysan*

## Installation de MinGW

Téléchargez et installez [MinGW-W64 Online Installer](https://sourceforge.net/projects/mingw-w64/files/).

**Remarque :** Pour faciliter la configuration, définissez un emplacement simple comme ci-dessous :

![dossier d'installation de MinGW](images/c_dossier_installation_mingw.png)

Notez l'emplacement du dossier d'installation.


#### Configurer le path

 Vous devez ajouter le chemin vers le sous-dossier  `mingw32\bin` (il contient plein de fichiers `.exe`) au path Windows.

 **Exemple :** `C:\mingw\mingw32\bin`

Dans la barre de recherche de Windows, saisissez `variables d'environnement` et choisissez l'option `Modifier les variables d'environnement système`.

Cliquez sur le bouton `Variables d'environnement...`.

![bouton Variables d'environnement...](images/c_bouton_variables_environnement.png)

Dans la section `Variables système`, faites un double clic sur la ligne `Path`.

![ligne Path dans la boite de dialogue](images/c_ligne_path.png)

Cliquez sur le bouton `Nouveau` et ajoutez le chemin vers le sous dossier `mingw32\bin`.

![ajout de MinGW au Path](images/c_ajouter_path.png)

Une fois terminé, cliquez sur `OK` pour fermer toutes les fenêtres.

Le path est bien configuré si la commande `gcc` est reconnue quand vous la saisissez dans un terminal.

![test de la commande gcc](images/c_commande_gcc_test.png)

## Compiler avec Visual Studio Code

Créez un dossier et ouvrez-le avec Visual Studio Code.

Créez un fichier `main.c` et saisissez le code suivant :

```c
#include <std.io>

int main(void)
{
    printf("Hello, World!");
    return 0;
}
```

Cliquez sur le menu `Terminal -> New Terminal`. Un terminal s'affiche en bas de la fenêtre.

Pour compiler le fichier source, saisissez la commande suivante :

```
gcc main.c
```

Aucun message n'apparait dans le terminal quand la compilation se passe bien. Cependant, un nouveau fichier exécutable a bien été généré. Dans le terminal, saisissez la commande `ls` pour afficher la liste des fichiers du dossier. Un fichier nommé `a.exe` doit être présent.

```
ls
```

![commande `ls` dans le terminal de Visual Studio Code](images/c_commande_ls_vscode.png)

Par défaut, le compilateur `gcc` génère un fichier exécutable appelé `a.exe` à partir de votre fichier source. Pour l'exécuter depuis le terminal, saisissez la commande suivante :

```
.\a.exe
```

![exécution du programme test dans le terminal](images/c_premiere_execution_vscode.png)

## Point d'entrée d'un programme

La fonction `main` est généralement le point d'entrée d'un programme C. Elle renvoie un entier à l'environnement d'exécution. Elle peut s'écrire sous deux formes.

La première forme ne prend pas de paramètre (en C, on le précise avec le mot clé `void`).

```c
int main(void) {}
```

La seconde forme prend deux paramètres.

- Un entier (généralement nommé `argc`) qui contient soit `0` soit le nombre de chaînes contenues dans le second paramètre.
- Un tableau de pointeurs de caractères (généralement nommé `argv`) qui contient des chaînes de caractères passées au programme lors de son lancement par l'environnement d'exécution. Le premier élément correspond au nom du programme.

```c
int main(int argc, char* argv[]) {}
```

Cette seconde forme est utilisée lorsque le programme doit recevoir des paramètres de l'environnement d'exécution.

Par convention, un programme s'exécutant correctement se termine en renvoyant la valeur `0` à l'environnement d'exécution. Vous pouvez le préciser explicitement à la fin de la fonction `main` en utilisant l'instruction `return 0;`.

```c
int main(void)
{
    return 0;
}
```

Depuis la norme C99, cette instruction n'est pas obligatoire. Si vous ne la placez pas dans votre programme, le compilateur considère par défaut que le programme renvoie la valeur `0`.

Pour plus de clarté, vous pouvez également renvoyer la constante `EXIT_SUCCESS` définie dans le fichier en-tête `stdlib.h`.

```c
#include <stdlib.h>

int main(void)
{
    return EXIT_SUCCESS;
}
```

**Remarque :** En cas de besoin, vous pouvez également utiliser la constante `EXIT_FAILURE` définie dans le fichier en-tête `stdlib.h` pour indiquer que le programme ne s'est pas terminé correctement.

## Compiler un fichier source et exécuter le programme

Compiler avec `gcc` :

```
gcc nom_du_fichier.c
```

Exécuter le programme :

```
./a.exe
```

Combiner les deux :

```
gcc nom_du_fichier.c && ./a.exe
```

## Littéraux

Un littéral entier peut être écrit sous forme décimale :

```c
int nombre = 12345;
```

Un littéral caractère s'écrit entre apostrophes :

```c
char caractere = 'a';
```

Un littéral chaîne de caractères s'écrit entre guillemets :

```c
char* chaine = "bonjour";
```

Une chaîne de caractères possède un caractères de fin de chaîne `\0` en plus des caractères classiques.

Un littéral chaîne de caractères vide s'écrit avec deux guillemets :

```c
char* chaine_vide = "";
```



## Afficher une chaine de caractères

```c
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char* argv[])
{
    printf("Bonjour.");
    return EXIT_SUCCESS;
}
```

```c
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char* argv[])
{
    char* chaine = "Bonjour.";
    printf(chaine);
    return EXIT_SUCCESS;
}
```

```c
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char* argv[])
{
    char* chaine = "Bonjour.";
    printf("%s", chaine);
    return EXIT_SUCCESS;
}
```

## Afficher un nombre entier

```c
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char* argv[])
{
    printf("%d", 1234);
    return EXIT_SUCCESS;
}
```

```c
#include <stdio.h>
#include <stdlib.h>

int main(int argc, char* argv[])
{
    int entier = 1234;
    printf("%d", entier);
    return EXIT_SUCCESS;
}
```

## Commentaires

```c
// commentaires sur une seule ligne

/* commentaire
sur plusieurs
lignes */
```

## La fonction printf

Le premier paramètre de la fonction `printf` est **toujours** de type chaine de caractères.

- `%d` affiche le paramètre suivant de type entier sous forme décimale.
- 
