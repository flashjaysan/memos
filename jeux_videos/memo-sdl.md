# Mémo SDL

*par flashjaysan*

## Installation Windows

### Visual Studio Code

Téléchargez et installez [Visual Studio Code](https://code.visualstudio.com/download) puis installez l'extension `C/C++` de Microsoft.

### MinGW

#### Installer MinGW

La procédure est détaillée dans mon autre [mémo consacré au langage C](../langages/memo-c.md).

### SDL

Rendez vous sur le site de la [SDL](https://www.libsdl.org/download-2.0.php).

Téléchargez les Development Libraries pour MinGW ainsi que les Runtime Binaries en version 64 bits.

![fichiers de la SDL à télécharger](images/c_binaries_et_libraries.png)

Dézippez ces deux archives à l'emplacement de votre choix.

**Remarque :** Pour faciliter la configuration, choisissez un emplacement simple (par exemple `C:\SDL`).

## Configurer un projet

Créez un dossier vide et ouvrez-le dans Visual Studio Code.

Créez les sous-dossiers `src` (pour vos fichiers source), `build` (pour les exécutables) et `.vscode` (pour la configuration).

Dans le sous-dossier `build`, placez le fichier `SDL2.dll` pour pouvoir exécuter votre programme.

Dans le sous-dossier `.vscode`, créez un fichier `tasks.json`. Saisissez le code suivant dans ce ficher :

```json
{
	"version": "2.0.0",
	"tasks": [
		{
			"type": "shell",
			"label": "SDL2",
			"command": "C:\\mingw\\mingw32\\bin\\g++.exe",
			"args": [
				"-g",
				"src\\*.cpp",
				"-o",
				"build\\game.exe",
				"-IC:/SDL/x86_64-w64-mingw32/include",
				"-LC:/SDL/x86_64-w64-mingw32/lib",
				"-lmingw32",
				"-lSDL2main",
				"-lSDL2",
				"-mwindows"
			],
			"options": {
				"cwd": "${workspaceFolder}"
			},
			"problemMatcher": [
				"$gcc"
			],
			"group": {
				"kind": "build",
				"isDefault": true
			}
		}
	]
}
```

- La propriété `"label"` correspond au nom de la tâche.
- La propriété `"command"` correspond au chemin vers le compilateur C++ nommé `g++.exe` et situé dans le sous-dossier `mingw64/bin` du dossier d'installation de MinGW.
- La propriété `"args"` contient des informations supplémentaires à préciser :
  - le nom de l'exécutable créé (ici `"build\\game.exe"`).
  - le chemin vers les dossiers `include` et `lib` de la SDL en version 64 bits (dossier mentionnant `x86_64`) (ici `"-IC:\\SDL\\x86_64-w64-mingw32\\include"` et `"-LC:\\SDL\\x86_64-w64-mingw32\\lib"`).

**Remarques :**

- L'option `-I` du compilateur `g++` sert à préciser l'emplacement des fichiers headers (les fichiers `.h`) d'une bibliothèque comme la SDL. Ces fichiers sont généralement situés dans un dossier nommé `include`.
- L'option `-L` du compilateur `g++` sert à préciser l'emplacement des fichiers objets précompilés (les fichiers `.a`) d'une bibliothèque comme la SDL. Ces fichiers sont généralement situés dans un dossier nommé `lib`.

Dans le sous-dossier `.vscode`, créez un fichier `launch.json`. Saisissez le code suivant dans ce ficher :

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "(gdb)",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceFolder}\\build\\game.exe",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "miDebuggerPath": "C:\\mingw\\mingw32\\bin\\gdb.exe",
            "setupCommands": [
                {
                    "description": "Enably pretty printing",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ],
            "preLaunchTask": "SDL2"
        }
    ]
}
```

- La propriété `"program"` correspond au chemin vers l'exécutable créé lors de la compilation.
- La propriété `"miDebuggerPath"` correspond au chemin vers le déboggeur `gdb.exe` situé dans le sous-dossier `mingw64/bin` du dossier d'installation de MinGW.
- La propriété `"preLaunchTask"` indique quelle tache doit être effectuée avant de lancer l'exécution du programme. En l'occurrence, ici, on demande à compiler le projet via la tache `"SDL2"`.

### Configurer Intellisense

Dans Visual Studio Code, appuyez sur `CTRL + SHIFT + P`, saisissez `C/C++` et choisissez l'option `C/C++ Edit configurations (UI)` pour ouvrir le fichier de configuration lié à la compilation de projets C et C++.

Dans la section `Chemin du compilateur`, saisissez le chemin vers le compilateur `g++.exe` situé dans le sous-dossier `mingw64/bin` du dossier d'installation de MinGW (par exemple `C:\mingw\mingw32\bin\g++.exe`).

Dans la section `Mode IntelliSense`, choisissez l'option `gcc_x64`.

Dans la section `Inclure le chemin`, saisissez le chemin vers le dossier `include` de la SDL en version 64 bits (dossier mentionnant `x86_64`) (exemple : `C:\SDL\x86_64-w64-mingw32\include\**`).

**Remarque :** N'encadrer pas les chemins de guillemets et ne doublez pas les antislash dans ce fichier de configuration.

Sauvegardez ce fichier.

### Vérifier si la configuration est correcte

Dans le sous-dossier `src`, créez un fichier `main.cpp` et saisissez le code suivant :

```cpp
#include <SDL2/SDL.h>
#include <iostream>

int main(int argv, char** args)
{
	SDL_Init(SDL_INIT_EVERYTHING);

	SDL_Window *window = SDL_CreateWindow("Hello SDL", SDL_WINDOWPOS_CENTERED, SDL_WINDOWPOS_CENTERED, 800, 600, 0);
	SDL_Renderer *renderer = SDL_CreateRenderer(window, -1, 0);

	bool isRunning = true;
	SDL_Event event;

	while (isRunning)
	{
		while (SDL_PollEvent(&event))
		{
			switch (event.type)
			{
			case SDL_QUIT:
				isRunning = false;
				break;

			case SDL_KEYDOWN:
				if (event.key.keysym.sym == SDLK_ESCAPE)
				{
					isRunning = false;
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

Appuyez sur `F5`. Si une fenêtre rouge apparait, tout fonctionne correctement. Vous pouvez utiliser la SDL.




