# Mémo SDL

*par flashjaysan*

## Installation

Pour utiliser la SDL, vous aurez besoin d'un compilateur C ou C++. La procédure est détaillée dans mon autre [mémo consacré au langage C](../langages/memo-c.md).

### SDL

Rendez-vous sur le site de la [SDL](https://www.libsdl.org/download-2.0.php).

Téléchargez les Development Libraries pour MinGW.

![fichier de la SDL à télécharger](images/sdl_development_libraries.png)

Dézippez cette archive à l'emplacement de votre choix.

**Remarque :** Pour faciliter la configuration, choisissez un emplacement simple (par exemple `C:\SDL`).

## Préparation d'un projet

Créez un dossier vide et ouvrez-le dans Visual Studio Code.

Créez le sous-dossier `src` pour vos fichiers source.

Copiez les dossiers `include`, `lib` et `bin` de la SDL dans le dossier du projet.

**Attention !** La SDL est fournie en version 32 et 64 bits. Vous devez utiliser la version correspondante à l'architecture de votre compilateur. Les machines modernes utilisant presque toutes une base 64 bits, je vous conseille donc d'utiliser la version 64 bits de la SDL avec un compilateur 64 bits. La version 64 bits de la SDL est située dans le sous-dossier `x86_64...` tandis que la version 32 bits est située dans le sous-dossier `i686...`.

Vous devriez avoir l'arborescence de projet suivante :

- racine du projet
  - dossier `include`
    - dossier `SDL2`
	  - fichiers en-tête (`.h`) de la SDL
  - dossier `lib`
    - fichiers objets (`.a`) de la SDL
  - dossier `src`
  - dossier `bin`
    - fichier `SDL.dll`

Dans le sous-dossier `src`, créez un fichier main.c et saisissez le code suivant :

```c
#include <stdio.h>
#include <SDL2/SDL.h>

int main(int argv, char** args)
{
    if (SDL_Init(SDL_INIT_EVERYTHING) == 0)
    {
        printf("SDL initialisee.");
    }
    else
    {
        printf("Probleme avec la SDL.");
    }
    SDL_Quit();
    return 0;
}
```

**Remarque :** La SDL impose cette version de la fonction `main`. Cela ne fonctionnera pas avec la version ne prenant pas de paramètres.

Pour compiler le fichier, ouvrez le terminal dans Visual Studio Code et saisissez la commande suivante :

```
gcc src/main.c -Iinclude -Llib -lmingw32 -lSDL2main -lSDL2 -o bin/main.exe
```

**Remarques :**

- Le premier paramètre passé au compilateur correspond au nom du fichier source à compiler. Notez que la compilation s'effectue à la racine du projet. Vous devez donc indiquer le chemin relatif du fichier source à compiler.
- L'option `-I` du compilateur `gcc` sert à préciser l'emplacement des fichiers headers (les fichiers `.h`) d'une bibliothèque comme la SDL. Ces fichiers sont généralement situés dans un dossier nommé `include`.
- L'option `-L` du compilateur `gcc` sert à préciser l'emplacement des fichiers objets précompilés (les fichiers `.a`) d'une bibliothèque comme la SDL. Ces fichiers sont généralement situés dans un dossier nommé `lib`.
- L'option `-l` indique les fichiers objets à ajouter au programme par l'éditeur de liens. Les trois fichiers objets `mingw32`, `SDL2main` et `SDL2` doivent être listés dans cet ordre précis.
- L'option `-o` permet de préciser le nom et l'emplacement où générer le fichier exécutable. Notez que la compilation s'effectue à la racine du projet. Vous devez donc indiquer le chemin relatif du fichier exécutable à générer.

Si tout s'est bien passé, un fichier `main.exe` doit avoir été généré dans le dossier `bin`.

Pour exécuter le programme, dans le terminal de visual Studio Code, saisissez la commande suivante :

```
bin/main.exe
```

![compilation et execution d'un premier projet avec SDL](images/sdl_premiere_compilation.png)

modifier le fichier `main.c` avec le code suivant :

```c
#include <stdio.h>
#include <SDL2/SDL.h>

int main(int argv, char** args)
{
	SDL_Init(SDL_INIT_EVERYTHING);

	SDL_Window *window = SDL_CreateWindow("Hello SDL", SDL_WINDOWPOS_CENTERED, SDL_WINDOWPOS_CENTERED, 800, 600, 0);
	SDL_Renderer *renderer = SDL_CreateRenderer(window, -1, 0);

	int isRunning = 1;
	SDL_Event event;

	while (isRunning)
	{
		while (SDL_PollEvent(&event))
		{
			switch (event.type)
			{
			case SDL_QUIT:
				isRunning = 0;
				break;

			case SDL_KEYDOWN:
				if (event.key.keysym.sym == SDLK_ESCAPE)
				{
					isRunning = 0;
				}
			}
		}

		SDL_RenderClear(renderer);
		SDL_SetRenderDrawColor(renderer, 255, 0, 0, 255);

		SDL_RenderPresent(renderer);
	}

	SDL_DestroyRenderer(renderer);
	SDL_DestroyWindow(window);
	SDL_Quit();

	return 0;
}
```

Compilez à nouveau et exécutez le programme. Si une fenêtre rouge s'affiche, vous êtes prêt à utiliser la SDL.

![première fenêtre avec SDL](images/sdl_premiere_fenetre.png)

Appuyez sur `ECHAP` pour fermer le programme.
