# Mémo C

*par flashjaysan*

## Point d'entrée d'un programme

```c
int main(void)
{
    return 0;
}
```


```c
#include <stdlib.h>

int main(void)
{
    return EXIT_SUCCESS;
}
```

```c
#include <stdlib.h>

int main(int argc, char* argv[])
{
    return EXIT_SUCCESS;
}
```

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
