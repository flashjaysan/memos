# Mémo raylib

par *flashjaysan*

## Introduction

[raylib](http://www.raylib.com) est une bibliothèque facile à utiliser, légère et conçue pour apprendre à programmer des jeux vidéos. Elle est gratuite, libre (licence zlib / libpng) et développée en langage C (C99) par Ramon Santamaria (plus connu sous le pseudonyme raysan5).

raylib permet de développer pour les plateformes Windows, Linux, Mac OS X, Android, Raspberry Pi, HTML5...

En fait, techniquement, raylib est compatible avec toute plateforme supportant le langage C et le standard OpenGL.

Fonctionnalités de raylib : 

- pas de dépendances externes. Toutes les bibliothèques requises sont incluses avec raylib.
- nombreuses plateformes supportées : Windows, Linux, Mac OS X, Android, et bien d'autres…
- écrit en langage C (C99) en notation PascalCase / camelCase.
- accélération matérielle avec OpenGL (1.1, 2.1, 3.3 ou ES 2.0).
- couche d'abstraction OpenGL unique (utilisable en tant que module indépendant) :

[https://github.com/raysan5/raylib/blob/master/src/rlgl.h](https://github.com/raysan5/raylib/blob/master/src/rlgl.h)

- module puissant de police de caractères avec la gestion des SpriteFonts (polices XNA, AngelCode et TTF).
- prise en charge de nombreux formats de textures y compris des formats compressés (DXT, ETC, ASTC).
- support 3D complet de formes géométriques, de modèles, de billboards, de heightmaps et plus.
- système de matériaux souple supportant des maps classiques et PBR.
- support des shaders y compris shaders de modèles et des shaders de post-traitement.
- module puissant de math sur les vecteurs, les matrices et les quaternions :

[https://github.com/raysan5/raylib/blob/master/src/raymath.h](https://github.com/raysan5/raylib/blob/master/src/raymath.h)

- chargement automatique et lecture audio avec support du streaming (WAV, OGG, MP3, FLAC, XM, MOD).
- support de rendu VR en stéréo avec des paramètres d'appareils HMD configurables.
- Support des langages Lua, Go et d'autres.
 
## Installation

### Windows

Installer raylib sur Windows est très simple. Téléchargez et installez le fichier depuis le site suivant :

[https://raysan5.itch.io/raylib](https://raysan5.itch.io/raylib)

**Remarque :** Vous n'êtes pas obligé de payer. Il suffit de cliquer sur le texte "No thanks, just take me to the downloads" lorsqu'on vous le demande.

Par défaut, raylib s'installe à la racine de votre disque système. A l'intérieur du dossier raylib, vous trouvez :

- le dossier `mingw` contenant les outils de compilation pour convertir les fichiers sources en fichiers exécutables.
- le dossier `npp` contenant l'éditeur de code Notepad++ préconfiguré pour compiler les projets utilisants raylib.
- le dossier `raylib` contenant les fichiers sources de raylib ainsi que les fichiers exemples.

****Conseil :**** Pour plus de simplicité, utilisez Notepad++.exe située dans le dossier `npp`.

Pour plus de détails, consultez la page suivante :

[https://github.com/raysan5/raylib/wiki/Working-on-Windows](https://github.com/raysan5/raylib/wiki/Working-on-Windows)

#### Compilation avec Notepad++

La version de Notepad++ fournie avec raylib sur Windows inclut un script pour compiler facilement vos programmes sources.

Pour compiler et tester votre programme actuellement ouvert dans Notepad++, allez dans le menu `Plugins > NppExec` et choisissez l'option `Execute…` (vous pouvez également appuyer sur la touche `F6`). Dans le menu déroulant en bas de la fenêtre qui vient de s'ouvrir, choisissez l'option `raylib_compile_execute` puis cliquez sur le bouton `OK`. Si votre programme ne comporte pas d'erreur, Notepad++ va le compiler et l'exécuter automatiquement.

### Raspberry Pi

Toutes les versions du Raspberry Pi sont supportées par raylib. Par défaut, le système Raspbian inclut le compilateur `gcc`. Vous n'avez donc normalement pas besoin d'autre chose que les fichiers sources de raylib.

#### Mise à jour de Raspbian

Commencez par mettre votre système à jour le système. Ouvrez le terminal et saisissez les commandes suivantes :

```
sudo apt-get update
sudo apt-get dist-update
sudo apt-get clean
```

Vérifiez que vous utilisez bien la dernière version de Raspbian ("stretch" et non "jessie" à l'heure de la rédaction de ce document). Pour le savoir, saisissez la commande suivante dans le terminal :

```
cat /etc/os-release
```

Pour plus d'informations, consultez la page suivante :

[https://www.raspberrypi.org/documentation/raspbian/updating.md](https://www.raspberrypi.org/documentation/raspbian/updating.md)

#### Compilation de raylib

Commencez par télécharger les fichiers sources de raylib à l'adresse suivante :

[https://github.com/raysan5/raylib](https://github.com/raysan5/raylib)

Pour la compilation, utilisez de préférence le mode natif car il fonctionne sur tous les types de Raspberry Pi et ne nécessite pas de configuration supplémentaire. Dans le terminal, placez-vous dans le dossier `src\` de raylib et saisissez la commande suivante :

```
make PLATFORM=PLATFORM_RPI
```

Pour plus de détails, consultez la page suivante :

[https://github.com/raysan5/raylib/wiki/Working-on-Raspberry-Pi](https://github.com/raysan5/raylib/wiki/Working-on-Raspberry-Pi)

#### Compilation des fichiers exemples

Dans le terminal, placez-vous dans le dossier `examples\` de raylib et saisissez la commande suivante :

```
make PLATFORM=PLATFORM_RPI
```

#### Compiler un programme utilisant la bibliothèque raylib

Lorsque vous voulez compiler un programme source utilisant la bibliothèque raylib, ouvrez une fenêtre `LXTerminal`, placez-vous dans le dossier contenant votre programme source et invoquez le compilateur `gcc` avec la commande suivante (une seule ligne de commande) :

```
arm-linux-gnueabihf-gcc -o nom_du_programme_exécutable nom_du_fichier_source.c -O1 -s -Wall -std=gnu99 -D_DEFAULT_SOURCE -Wno-missing-braces -I. -I/opt/vc/include -I/opt/vc/include/interface/vmcs_host/linux -I/opt/vc/include/interface/vcos/pthreads -L. -L/opt/vc/lib -lraylib -lbrcmGLESv2 -lbrcmEGL -lpthread -lrt -lm -lbcm_host -ldl -DPLATFORM_RPI
```

Remplacez simplement le `nom_du_programme_exécutable` par celui de votre choix et le `nom_du_fichier_source` par celui correspondant à votre fichier source réel.

**Remarque :** Vous pouvez copier cette ligne de commande (quelque peu compliquée). Vous devrez toutefois l'éditer pour passer les bons fichiers sources et exécutables.

#### Exécuter un programme compilé

Ouvrez une fenêtre `LXTerminal`, placez-vous dans le dossier contenant votre programme exécutable puis saisissez la commande suivante :

```
./nom_du_programme_exécutable
```

Remplacez simplement le `nom_du_programme_exécutable` par celui que vous avez choisi lors de la compilation.

**Remarque :** Si cela ne fonctionne pas, saisissez le mot clé `sudo` devant la commande.

### Autres systèmes

Pour les autres plateformes, raylib peut être compilé à partir des sources disponibles sur Github :

[https://github.com/raysan5/raylib](https://github.com/raysan5/raylib)

Une section wiki détaille également comment bien démarrer sur différentes plateformes.

## Sources de documentation

La documentation de raylib est quasiment inexistante. Heureusement, le code source est très bien commenté.
Sur le site officiel, vous trouverez la liste des fonctions et structures de données fournies par raylib :

[https://www.raylib.com/cheatsheet/cheatsheet.html](https://www.raylib.com/cheatsheet/cheatsheet.html)

Vous pourrez également trouver quelques informations sur l'installation et la compilation de raylib sur diverses plateformes sur le wiki dédié de github :

[https://github.com/raysan5/raylib/wiki](https://github.com/raysan5/raylib/wiki)

Vous trouverez aussi du contenu intéressant dans la partie challenges du github de raysan :

[https://github.com/raysan5/challenges](https://github.com/raysan5/challenges)

Mais la source principale d'information pour utiliser raylib se trouve dans les fichiers exemples :

[https://www.raylib.com/examples.html](https://www.raylib.com/examples.html)

Ces exemples sont truffés de pratiques ingénieuses (que vous pourrez utiliser avec n'importe quel framework de jeu) et démontrent les possibilités offertes par raylib.

## Structure de base

### Cycle de vie d'un jeu vidéo

Le cycle de vie standard d'un jeu vidéo consiste en quatre parties :

- Initialisation des ressources
- Mise à jour de l'état du jeu
- Affichage
- Libération des ressources

Les étapes 2 et 3 se répètent indéfiniment dans une boucle tant que le jeu s'exécute.

Le diagramme suivant montre ce cycle, les processus liés à chaque étape ainsi que les fonctions de raylib impliquées dans ces processus :

![]()

### Fichier en-tête de raylib

Pour utiliser raylib, pensez à toujours inclure dans vos programmes le fichier en-tête `raylib.h` :

```c
#include "raylib.h"
```

### Exemple de code de base

Le fichier exemple `core_basic_window` présente le squelette de base d'un projet vide utilisant raylib :

[https://www.raylib.com/examples/web/core/loader.html?name=core_basic_window](https://www.raylib.com/examples/web/core/loader.html?name=core_basic_window)

Examinons d'un peu plus près ce code source...

On demande d'abord au compilateur d'inclure le fichier nécessaire à l'utilisation de raylib :

```c
#include "raylib.h"
```

On définit ensuite la fonction principale `main` qui correspond au point d'entrée du programme :

```c
int main()
{
```

On définit deux variables `screenWidth` et `screenHeight` de type entier correspondant aux dimensions de la fenêtre de jeu :

```c
int screenWidth = 800;
int screenHeight = 450;
```

On initialise la fenêtre de jeu avec la fonction `InitWindow` en lui passant les dimensions de la fenêtre ainsi que son titre :

```c
InitWindow(screenWidth, screenHeight, "raylib [core] example - basic window");
```
    
On paramètre la fréquence de rafraîchissement du jeu (en nombre d'images affichées par seconde) :

```c
SetTargetFPS(60);
```
    
On démarre une boucle qui ne s'arrêtera que lorsque l'utilisateur fermera la fenêtre (ou appuiera sur la touche `ESC`) :

```c
while (!WindowShouldClose())
{
```

On met à jour les données du jeu. Pour l'instant, la section est vide bien entendu :

```c
// Update
```

On gère les fonctions d'affichage :

```c
// Draw
```

Cette ligne doit être insérée avant toute fonction d'affichage :

```c
BeginDrawing();
```

Cette fonction remplit l'écran de la couleur prédéfinie `RAYWHITE` :

```c
ClearBackground(RAYWHITE);
```

Cette fonction affiche le texte `"Congrats! You created your first window!"` à l'écran :

```c
DrawText("Congrats! You created your first window!", 190, 200, 20, LIGHTGRAY);
```

Cette ligne doit être insérée après avoir terminé d'appeler des fonctions d'affichage :

```c
EndDrawing();
```

On ferme la boucle :

```c
}
```

La boucle de jeu est terminée. On ferme la fenêtre et le contexte OpenGL :

```c
CloseWindow();
```

La fonction `main` doit renvoyer un entier au système avant d'être fermée. On renvoie la valeur `0` pour indiquer que tout s'est bien déroulé :

```c
    return 0;
}
```

### Structure de départ

Si on résume le programme précédent à ses composantes essentielles, on se retrouve avec le squelette de code suivant :

```c
#include "raylib.h"

int main()
{
    int screenWidth = 800;
    int screenHeight = 450;
    const int FPS = 60;
    InitWindow(screenWidth, screenHeight, "title");
    SetTargetFPS(FPS);
    while (!WindowShouldClose())
    {
        // Mise à jour
        // Affichage
        BeginDrawing();
        // Fonctions d'affichage
        EndDrawing();
    }
    CloseWindow();
    return 0;
}
```

## Structures de données essentielles

raylib fournit certaines structures de données usuelles :

### Color

La structure `Color` représente une couleur RVBA codée sur 32 bits :

```c
typedef struct Color {
    unsigned char r;
    unsigned char g;
    unsigned char b;
    unsigned char a;
} Color;
```

- Le champ `r` correspond à la composante rouge de la couleur. Il a une valeur comprise entre `0` et `255`.
- Le champ `g` correspond à la composante verte de la couleur. Il a une valeur comprise entre `0` et `255`.
- Le champ `b` correspond à la composante bleue de la couleur. Il a une valeur comprise entre `0` et `255`.
- Le champ `a` correspond à la composante de transparence (*alpha*) de la couleur. Il a une valeur comprise entre `0` et `255`.

#### Créer une couleur

Pour créer une couleur, déclarez une variable de type `Color` et initialisez-la avec la syntaxe suivante :

```c
Color color = (Color) {rouge, vert, bleu, alpha};
```

Les composantes `rouge`, `vert`, `bleu` et `alpha` sont des entiers non signés de 8 bits (une valeur comprise entre `0` et `255`).

**Remarque :** Pensez bien à donner la valeur `255` à la composante `alpha` pour qu'une couleur soit visible. Si vous ne donnez que trois valeurs à la couleur, la composante alpha prend par défaut la valeur 0. La couleur sera donc totalement transparente.

Les fonctions `ColorToInt` et `GetColor` convertissent une couleur en une valeur entière (type non signé) et inversement :

```c
int ColorToInt(Color color);
```

- Le paramètre `color` correspond à la couleur à convertir.

```c
Color GetColor(int hexValue);
```

- Le paramètre `hexValue` correspond à la valeur entière (non signée) à convertir. N'hésitez pas à utiliser la notation hexadécimale.

**Astuce :** Utilisez un outil de conversion pour définir une couleur précise. Par exemple :
[https://www.w3schools.com/colors/colors_picker.asp](https://www.w3schools.com/colors/colors_picker.asp)

#### Constantes associées aux couleurs

raylib définit un certain nombres de constantes symboliques représentant des couleurs dont voici la définition :

```c
#define LIGHTGRAY  (Color){ 200, 200, 200, 255 } // Light Gray
#define GRAY       (Color){ 130, 130, 130, 255 } // Gray
#define DARKGRAY   (Color){ 80, 80, 80, 255 }    // Dark Gray
#define YELLOW     (Color){ 253, 249, 0, 255 }   // Yellow
#define GOLD       (Color){ 255, 203, 0, 255 }   // Gold
#define ORANGE     (Color){ 255, 161, 0, 255 }   // Orange
#define PINK       (Color){ 255, 109, 194, 255 } // Pink
#define RED        (Color){ 230, 41, 55, 255 }   // Red
#define MAROON     (Color){ 190, 33, 55, 255 }   // Maroon
#define GREEN      (Color){ 0, 228, 48, 255 }    // Green
#define LIME       (Color){ 0, 158, 47, 255 }    // Lime
#define DARKGREEN  (Color){ 0, 117, 44, 255 }    // Dark Green
#define SKYBLUE    (Color){ 102, 191, 255, 255 } // Sky Blue
#define BLUE       (Color){ 0, 121, 241, 255 }   // Blue
#define DARKBLUE   (Color){ 0, 82, 172, 255 }    // Dark Blue
#define PURPLE     (Color){ 200, 122, 255, 255 } // Purple
#define VIOLET     (Color){ 135, 60, 190, 255 }  // Violet
#define DARKPURPLE (Color){ 112, 31, 126, 255 }  // Dark Purple
#define BEIGE      (Color){ 211, 176, 131, 255 } // Beige
#define BROWN      (Color){ 127, 106, 79, 255 }  // Brown
#define DARKBROWN  (Color){ 76, 63, 47, 255 }    // Dark Brown
#define WHITE      (Color){ 255, 255, 255, 255 } // White
#define BLACK      (Color){ 0, 0, 0, 255 }       // Black
#define BLANK      (Color){ 0, 0, 0, 0 }         // Transparent
#define MAGENTA    (Color){ 255, 0, 255, 255 }   // Magenta
#define RAYWHITE   (Color){ 245, 245, 245, 255 } // Ray White
```

**Astuce :** Si vous remplissez une structure `RenderTexture` avec la couleur `BLANK`, elle devient entièrement transparente. Vous pouvez ainsi créer un calque transparent sur lequel travailler.

#### Fonctions liées aux couleurs

La fonction `ColorToInt` renvoie un entier non signé représentant la couleur passée en argument :

```c
int ColorToInt(Color color);
```

- Le paramètre `color` correspond à la couleur à convertir.

La fonction `ColorNormalize` renvoie un vecteur à quatre dimensions contenant les quatre composantes normalisées (une valeur comprise entre `0` et `1`) de la couleur passée en argument :

```c
Vector4 ColorNormalize(Color color);
```

- Le paramètre `color` correspond à la couleur à convertir.

La fonction `ColorToHSV` renvoie un vecteur à trois dimensions contenant les composantes teinte, saturation et luminosité de la couleur passée en argument :

```c
Vector3 ColorToHSV(Color color);
```

- Le paramètre `color` correspond à la couleur à convertir.

La fonction `ColorFromHSV` renvoie une structure `Color`, conversion d'un vecteur à trois dimensions représentant la couleur passée en argument :

```c
Color ColorFromHSV(Vector3 hsv);
```

- Le paramètre `hsv` correspond au vecteur à trois dimensions à convertir. Les champs de ce vecteur contiennent une valeur des composantes teinte, saturation et luminosité.

La fonction `GetColor` renvoie une structure `Color`, conversion d'un entier non signé représentant la couleur passée en argument :

```c
Color GetColor(int hexValue);
```

- Le paramètre `hexValue` correspond à la couleur sous forme d'un entier non signé à convertir. Utilisez la notation hexadécimale si vous le souhaitez.

La fonction `Fade` renvoie une structure `Color`, conversion d'une structure `Color` initiale et d'un nombre à virgule flottante (compris entre `0.0f` et `1.0f`) correspondant à la valeur de la composante de transparence (`alpha`) à modifier :

```c
Color Fade(Color color, float alpha);
```

- Le paramètre `color` correspond à la couleur à modifier.
- Le paramètre `alpha` correspond à la valeur de transparence à attribuer à la couleur.

### Rectangle

La structure `Rectangle` définit un rectangle dans un plan :

```c
typedef struct Rectangle {
    float x;
    float y;
    float width;
    float height;
} Rectangle;
```

- Le champ `x` correspond à l'abscisse du coin supérieur gauche du rectangle.
- Le champ `y` correspond à l'ordonnée du coin supérieur gauche du rectangle.
- Le champ `width` correspond à la largeur du rectangle.
- Le champ `height` correspond à la  hauteur du rectangle.

### Vector2

La structure `Vector2` définit un vecteur à deux dimensions :

```c
typedef struct Vector2 {
    float x;
    float y;
} Vector2;
```

- Le champ `x` correspond à la composante horizontale du vecteur.
- Le champ `y` correspond à la composante verticale du vecteur.

### Vector3

La structure `Vector3` définit un vecteur à trois dimensions :

```c
typedef struct Vector3 {
    float x;
    float y;
    float z;
} Vector3;
```

- Le champ `x` correspond à la composante horizontale du vecteur.
- Le champ `y` correspond à la composante verticale du vecteur.
- Le champ `z` correspond à la composante de profondeur du vecteur.

### Vector4

La structure `Vector4` définit un vecteur à quatre dimensions :

```
typedef struct Vector4 {
    float x;
    float y;
    float z;
    float w;
} Vector4;
```

- Le champ `x` correspond à la première composante du vecteur.
- Le champ `y` correspond à la deuxième composante du vecteur.
- Le champ `z` correspond à la troisième composante du vecteur.
- Le champ `w` correspond à la quatrième composante du vecteur.

### Quaternion

L'alias `Quaternion` définit un quaternion :

```c
typedef Vector4 Quaternion;
```

- Le champ `x` correspond à la première composante du quaternion.
- Le champ `y` correspond à la deuxième composante du quaternion.
- Le champ `z` correspond à la troisième composante du quaternion.
- Le champ `w` correspond à la quatrième composante du quaternion.

### Matrix

La structure `Matrix` définit une matrice 4x4 :

```c
typedef struct Matrix {
    float m0, m4, m8, m12;
    float m1, m5, m9, m13;
    float m2, m6, m10, m14;
    float m3, m7, m11, m15;
} Matrix;
```

- Les seize champs `m0` à `m15` correspondent aux éléments par colonne de la matrice.

### Fonctions mathématiques spécifiques

raylib fournit un module spécifique pour effectuer des opérations mathématiques sur les structures prédéfinies :

[https://github.com/raysan5/raylib/blob/master/src/raymath.h](https://github.com/raysan5/raylib/blob/master/src/raymath.h)

Utilisez ce module en incluant le fichier en-tête `raymath.h` au début de vos codes sources :

```c
#include "raymath.h"
```

#### Fonctions mathématiques sur les vecteurs à deux dimensions

La fonction `Vector2Zero` renvoie une structure `Vector2` dont chaque composante a la valeur `0` (ce qu'on appelle un vecteur nul) :

```c
Vector2 Vector2Zero(void);
```

La fonction `Vector2One` renvoie une structure `Vector2` dont chaque composante a la valeur une :

```c
Vector2 Vector2One(void);
```

La fonction `Vector2Add` renvoie une structure `Vector2` résultat de la somme de deux structures `Vector2` passées en argument :

```c
Vector2 Vector2Add(Vector2 v1, Vector2 v2);
```

- Les paramètres `v1` et `v2` correspondent aux vecteurs dont on veut calculer la somme.

La fonction `Vector2Subtract` renvoie une structure `Vector2` résultat de la différence de deux structures `Vector2` passées en argument :

```c
Vector2 Vector2Subtract(Vector2 v1, Vector2 v2);
```

- Les paramètres `v1` et `v2` correspondent aux vecteurs dont on veut calculer la différence.

La fonction `Vector2Length` renvoie la longueur (magnitude) d'une structure `Vector2` passée en argument :

```c
float Vector2Length(Vector2 v);
```

- Le paramètre `v` correspond au vecteur dont on veut calculer la longueur.

La fonction `Vector2DotProduct` renvoie le résultat du produit scalaire de deux structures `Vector2` passées en argument :

```c
float Vector2DotProduct(Vector2 v1, Vector2 v2);
```

- Les paramètres `v1` et `v2` correspondent aux vecteurs dont on veut calculer le produit scalaire.

La fonction `Vector2Distance` renvoie la distance entre deux points représentés par des structures `Vector2` passées en argument :

```c
float Vector2Distance(Vector2 v1, Vector2 v2);
```

- Les paramètres `v1` et `v2` correspondent aux positions des deux points dont on veut calculer la distance.

La fonction `Vector2Angle` renvoie l'angle que font deux structures `Vector2` passées en argument :

```c
float Vector2Angle(Vector2 v1, Vector2 v2);
```

- Les paramètres `v1` et `v2` correspondent aux vecteurs dont on veut calculer l'angle.

La fonction `Vector2Scale` renvoie une structure `Vector2` résultat de la multiplication d'une structure `Vector2` et d'un nombre passés en argument :

```c
Vector2 Vector2Scale(Vector2 v, float scale);
```

- Le paramètre `v1` correspond au vecteur à multiplier.
- Le paramètre `scale` correspond au nombre par lequel multiplier le vecteur.

La fonction `Vector2MultiplyV` renvoie une structure `Vector2` résultat du produit de deux structures `Vector2` passées en argument :

```c
Vector2 Vector2MultiplyV(Vector2 v1, Vector2 v2);
```

- Les paramètres `v1` et `v2` correspondent aux vecteurs à multiplier.

La fonction `Vector2Negate` renvoie une structure `Vector2` opposée d'une structure `Vector2` passée en argument :

```c
Vector2 Vector2Negate(Vector2 v);
```

- Le paramètre `v` correspond au vecteur à inverser.

La fonction `Vector2Divide` renvoie une structure `Vector2` résultat de la division d'une structure `Vector2` et d'un nombre passés en argument :

```c
Vector2 Vector2Divide(Vector2 v, float div);
```

- Le paramètre `v1` correspond au vecteur à diviser.
- Le paramètre `div` correspond au nombre par lequel diviser le vecteur.

La fonction `Vector2DivideV` renvoie une structure `Vector2` résultat de la division de deux structures `Vector2` passées en argument :

```c
Vector2 Vector2DivideV(Vector2 v1, Vector2 v2);
```

- Les paramètres `v1` et `v2` correspondent aux vecteurs à diviser.

La fonction `Vector2Normalize` renvoie une structure `Vector2` unitaire (de longueur 1) d'une structure `Vector2` passée en argument :

```c
Vector2 Vector2Normalize(Vector2 v);
```

- Le paramètre `v` correspond au vecteur dont on veut calculer le vecteur unitaire.

La fonction `Vector2Lerp` renvoie une structure `Vector2` résultat d'un *lerp* entre deux structures `Vector2` et un nombre passés en arguments :

```c
Vector2 Vector2Lerp(Vector2 v1, Vector2 v2, float amount);
```

- Le paramètre `v1` correspond au vecteur initial.
- Le paramètre `v2` correspond au vecteur final.
- Le paramètre `amount` correspond à la quantité d'interpolation à effectuer.

#### Fonctions mathématiques sur les vecteurs à trois dimensions

La fonction `Vector3Zero` renvoie une structure `Vector3` dont chaque composante a la valeur `0` (un vecteur nul) :

```c
Vector3 Vector3Zero(void);
```

La fonction `Vector3One` renvoie une structure `Vector3` dont chaque composante a la valeur `1` :

```c
Vector3 Vector3One(void);
```

La fonction `Vector3Add` renvoie une structure `Vector3` somme de deux structures `Vector3` passées en argument :

```c
Vector3 Vector3Add(Vector3 v1, Vector3 v2);
```

- Les paramètres `v1` et `v2` correspondent aux vecteurs dont on veut calculer la somme.

La fonction `Vector3Add` renvoie une structure `Vector3` différence de deux structures `Vector3` passées en argument :

```c
Vector3 Vector3Subtract(Vector3 v1, Vector3 v2);
```

- Les paramètres `v1` et `v2` correspondent aux vecteurs dont on veut calculer la différence.

La fonction `Vector3Multiply` renvoie une structure `Vector3` produit d'une structure `Vector3` et d'un nombre passés en argument :

```c
Vector3 Vector3Multiply(Vector3 v, float scalar);
```c

- Le paramètre `v` correspond au vecteur à multiplier.
- Le paramètre `scalar` correspond au nombre par lequel on veut multiplier le vecteur.

La fonction `Vector3MultiplyV` renvoie une structure `Vector3` produit de deux structures `Vector3` passées en argument :

```c
Vector3 Vector3MultiplyV(Vector3 v1, Vector3 v2);
```

- Les paramètres `v1` et `v2` correspondent aux vecteurs dont on veut calculer le produit.

La fonction `Vector3CrossProduct` renvoie une structure `Vector3` produit vectoriel de deux structures `Vector3` passées en argument :

```c
Vector3 Vector3CrossProduct(Vector3 v1, Vector3 v2);
```

- Les paramètres `v1` et `v2` correspondent aux vecteurs dont on veut calculer le produit vectoriel.

La fonction `Vector3Perpendicular` renvoie une structure `Vector3` perpendiculaire à une structure `Vector3` passée en argument :

```c
Vector3 Vector3Perpendicular(Vector3 v);
```

- Le paramètre `v` correspond au vecteur dont on veut trouver un vecteur perpendiculaire.

La fonction `Vector3Length` renvoie la longueur (*magnitude*) d'une structure `Vector3` passée en argument :

```c
float Vector3Length(const Vector3 v);
```

- Le paramètre `v` correspond au vecteur dont on veut trouver la longueur.

La fonction `Vector3DotProduct` renvoie le produit scalaire (un nombre) de deux structures `Vector3` passées en argument :

```c
float Vector3DotProduct(Vector3 v1, Vector3 v2);
```

- Les paramètres `v1` et `v2` correspondent aux vecteurs dont on veut calculer le produit scalaire.

La fonction `Vector3Distance` renvoie la distance entre deux points représentés par des structures `Vector3` passées en argument :

```c
float Vector3Distance(Vector3 v1, Vector3 v2);
```

- Les paramètres `v1` et `v2` correspondent aux points dont on veut calculer la distance.

La fonction `Vector3Scale` renvoie une structure `Vector3` produit d'une structure `Vector3` et d'un nombre passés en argument :

```c
Vector3 Vector3Scale(Vector3 v, float scale);
```

- Le paramètre `v` correspond au vecteur à multiplier.
- Le paramètre `scale` correspond au nombre par lequel on veut multiplier le vecteur.

La fonction `Vector3Negate` renvoie une structure `Vector3` opposé à la structure `Vector3` passée en argument :

```c
Vector3 Vector3Negate(Vector3 v);
```

- Le paramètre `v` correspond au vecteur que l'on veut inverser.

La fonction `Vector3Divide` renvoie une structure `Vector3` division d'une structure `Vector3` par un nombre passés en argument :

```c
Vector3 Vector3Divide(Vector3 v, float div);
```

- Le paramètre `v` correspond au vecteur à diviser.
- Le paramètre `scale` correspond au nombre par lequel on veut diviser le vecteur.

La fonction `Vector3DivideV` renvoie une structure `Vector3` division de deux structures `Vector3` passées en argument :

```c
Vector3 Vector3DivideV(Vector3 v1, Vector3 v2);
```

- Les paramètres `v1` et `v2` correspondent aux vecteurs dont on veut calculer la division.

La fonction `Vector3Normalize` renvoie une structure `Vector3` vecteur unitaire (de longueur 1) d'une structure `Vector3` passée en argument :

```c
Vector3 Vector3Normalize(Vector3 v);
```

- Le paramètre `v` correspond au vecteur dont on veut obtenir le vecteur unitaire.

[Incomplet] La fonction `Vector3OrthoNormalize` orthonormalise deux pointeurs sur une structure `Vector3` passés en argument :

```c
// Orthonormalize provided vectors
// Makes vectors normalized and orthogonal to each other
// Gram-Schmidt function implementation
void Vector3OrthoNormalize(Vector3 *v1, Vector3 *v2);
```

Les paramètres `v1` et `v2` correspondent à ???????.

La fonction `Vector3Transform` renvoie une structure `Vector3` transformation d'une structure `Vector3` par une structure Matrix passées en argument :

Vector3 Vector3Transform(Vector3 v, Matrix mat);

- Le paramètre v correspond au vecteur sur lequel on veut appliquer la transformation.
- Le paramètre mat correspond à la matrice définissant la transformation.

La fonction Vector3RotatedQuaternion renvoie une structure Vector3 rotation d'une structure Vector3 par une structure Quaternion passées en argument :

Vector3 Vector3RotateByQuaternion(Vector3 v, Quaternion q);

- Le paramètre v correspond au vecteur sur lequel on veut appliquer la rotation.
- Le paramètre q correspond au quaternion définissant la rotation.

La fonction Vector3Lerp renvoie une structure Vector3 résultat d'une interpolation linéaire entre deux structures Vector3 et un nombre passés en argument :

Vector3 Vector3Lerp(Vector3 v1, Vector3 v2, float amount);

- Le paramètre v1 correspond au vecteur initial.
- Le paramètre v2 correspond au vecteur final.
- Le paramètre amount correspond à la quantité d'interpolation à effectuer.

[Incomplet] La fonction Vector3Reflect renvoie une structure Vector3 ?????????? de deux structures Vector3 passées en argument :

// Calculate reflected vector to normal
Vector3 Vector3Reflect(Vector3 v, Vector3 normal);

- Le paramètre v correspond au vecteur sur lequel ?????.
- Le paramètre normal correspond au vecteur ?????.

La fonction Vector3Min renvoie une structure Vector3 composée des composantes minimales de deux structures Vector3 passées en argument :

Vector3 Vector3Min(Vector3 v1, Vector3 v2);

Les paramètres v1 et v2 correspondent aux vecteurs dont on veut récupérer les composantes minimales.

La fonction Vector3Max renvoie une structure Vector3 composée des composantes maximales de deux structures Vector3 passées en argument :

Vector3 Vector3Max(Vector3 v1, Vector3 v2);

Les paramètres v1 et v2 correspondent aux vecteurs dont on veut récupérer les composantes maximales.

La fonction Vector3Barycenter renvoie une structure Vector3 correspondant au barycentre d'un point par rapport à un triangle représenté par trois sommets (sous la forme de structures Vector3) passés en argument :

Vector3 Vector3Barycenter(Vector3 p, Vector3 a, Vector3 b, Vector3 c);

**Attention !** Le point p est supposé se trouver sur le même plan que celui du triangle.

- Le paramètre p correspond à la position du point.
- Le paramètre a correspond à la position du premier sommet du triangle.
- Le paramètre b correspond à la position du  deuxième sommet du triangle.
- Le paramètre c correspond à la position du troisième sommet du triangle.

La fonction Vector3ToFloatV renvoie une structure float3 conversion en tableau de nombres à virgule flottante d'une structure Vector3 passée en argument :

float3 Vector3ToFloatV(Vector3 v);

 Le paramètre v correspond à la structure Vector3 à convertir.

#### Fonctions mathématiques sur les quaternions [incomplet]

// Returns identity quaternion
Quaternion QuaternionIdentity(void);

// Computes the length of a quaternion
float QuaternionLength(Quaternion q);

// Normalize provided quaternion
Quaternion QuaternionNormalize(Quaternion q);

// Invert provided quaternion
Quaternion QuaternionInvert(Quaternion q);

// Calculate two quaternion multiplication
Quaternion QuaternionMultiply(Quaternion q1, Quaternion q2);

// Calculate linear interpolation between two quaternions
Quaternion QuaternionLerp(Quaternion q1, Quaternion q2, float amount);

// Calculate slerp-optimized interpolation between two quaternions
Quaternion QuaternionNlerp(Quaternion q1, Quaternion q2, float amount);

// Calculates spherical linear interpolation between two quaternions
Quaternion QuaternionSlerp(Quaternion q1, Quaternion q2, float amount);

// Calculate quaternion based on the rotation from one vector to another
Quaternion QuaternionFromVector3ToVector3(Vector3 from, Vector3 to);

// Returns a quaternion for a given rotation matrix
Quaternion QuaternionFromMatrix(Matrix mat);

// Returns a matrix for a given quaternion
Matrix QuaternionToMatrix(Quaternion q);

// Returns rotation quaternion for an angle and axis
// NOTE: angle must be provided in radians
Quaternion QuaternionFromAxisAngle(Vector3 axis, float angle);

// Returns the rotation angle and axis for a given quaternion
void QuaternionToAxisAngle(Quaternion q, Vector3 *outAxis, float *outAngle);

// Returns he quaternion equivalent to Euler angles
Quaternion QuaternionFromEuler(float roll, float pitch, float yaw);

// Return the Euler angles equivalent to quaternion (roll, pitch, yaw)
// NOTE: Angles are returned in a Vector3 struct in degrees
Vector3 QuaternionToEuler(Quaternion q);

// Transform a quaternion given a transformation matrix
Quaternion QuaternionTransform(Quaternion q, Matrix mat);

#### Fonctions mathématiques sur les matrices [incomplet]

// Compute matrix determinant
float MatrixDeterminant(Matrix mat);

// Returns the trace of the matrix (sum of the values along the diagonal)
float MatrixTrace(Matrix mat);

// Transposes provided matrix
Matrix MatrixTranspose(Matrix mat);

// Invert provided matrix
Matrix MatrixInvert(Matrix mat);

// Normalize provided matrix
Matrix MatrixNormalize(Matrix mat);

// Returns identity matrix
Matrix MatrixIdentity(void);

// Add two matrices
Matrix MatrixAdd(Matrix left, Matrix right);

// Subtract two matrices (left - right)
Matrix MatrixSubtract(Matrix left, Matrix right);

// Returns translation matrix
Matrix MatrixTranslate(float x, float y, float z);

// Create rotation matrix from axis and angle
// NOTE: Angle should be provided in radians
Matrix MatrixRotate(Vector3 axis, float angle);

// Returns x-rotation matrix (angle in radians)
Matrix MatrixRotateX(float angle);

// Returns y-rotation matrix (angle in radians)
Matrix MatrixRotateY(float angle);

// Returns z-rotation matrix (angle in radians)
Matrix MatrixRotateZ(float angle);

// Returns scaling matrix
Matrix MatrixScale(float x, float y, float z);

// Returns two matrix multiplication
// NOTE: When multiplying matrices... the order matters!
Matrix MatrixMultiply(Matrix left, Matrix right);

// Returns perspective projection matrix
Matrix MatrixFrustum(double left, double right, double bottom, double top, double near, double far);

// Returns perspective projection matrix
// NOTE: Angle should be provided in radians
Matrix MatrixPerspective(double fovy, double aspect, double near, double far);

// Returns orthographic projection matrix
Matrix MatrixOrtho(double left, double right, double bottom, double top, double near, double far);

// Returns camera look-at matrix (view matrix)
Matrix MatrixLookAt(Vector3 eye, Vector3 target, Vector3 up);

// Returns float array of matrix data
float16 MatrixToFloatV(Matrix mat);

#### Autres fonctionnalités mathématiques

raylib fournit également quelques fonctionnalités supplémentaires notables dans le fichier en-tête `raymath.h` ou directement dans le fichier en-tête `raylib.h`.

La constante `PI` est définie dans les deux fichiers en-tête comme ceci :

```c
#define PI 3.14159265358979323846
```

La constante symbolique `DEG2RAD` permet d'effectuer la conversion d'une valeur en degrés vers une valeur en radians. La constante symbolique `RAD2DEG` permet d'effectuer la conversion inverse :

```c
#define DEG2RAD (PI/180.0f)
#define RAD2DEG (180.0f/PI)
```

[Incomplet] La macro MatrixToFloat ??????

// Return float vector for Matrix
#define MatrixToFloat(mat) (MatrixToFloatV(mat).v)

// Return float vector for Vector3
#define Vector3ToFloat(vec) (Vector3ToFloatV(vec).v)

// NOTE: Helper types to be used instead of array return types for *ToFloat functions
typedef struct float3 { float v[3]; } float3;

typedef struct float16 { float v[16]; } float16;

La fonction Clamp renvoie un nombre contraint dans un intervalle compris entre une valeur minimale et une valeur maximale passées en argument. Voici son prototype :

float Clamp(float value, float min, float max);

- Le paramètre value correspond à la valeur à tester.
- Le paramètre min correspond à la valeur minimale à ne pas dépasser.
- Le paramètre max correspond à la valeur maximale à ne pas dépasser.

La fonction Lerp renvoie un nombre correspondant à l'interpolation linéaire entre deux valeurs par une quantité définie. Voici son prototype :

float Lerp(float start, float end, float amount);

- Le paramètre start correspond à la valeur de départ.
- Le paramètre end correspond à la valeur d'arrivée.
- Le paramètre amount correspond à la quantité d'interpolation à utiliser dans le calcul.

## Gérer l'affichage

### Paramétrer la résolution du jeu

La fonction InitWindow initialise la fenêtre de jeu et le contexte OpenGL :

void InitWindow(int width, int height, const char *title);

- Le paramètre width correspond à la largeur en pixels de la fenêtre de jeu.
- Le paramètre height correspond à la hauteur en pixels de la fenêtre de jeu.
- Le paramètre title correspond au titre de la fenêtre.

**Attention !** Si vous utilisez cette fonction, pensez à toujours appeler la fonction CloseWindow par la suite.

**Conseil :** Dans les fichiers exemples, deux variables entières screenWidth et screenHeight sont définies dans la fonction principale main pour représenter la résolution du jeu. L'auteur de raylib m'a expliqué qu'il n'utilisait pas de constantes pour ces valeurs dans les fichiers exemples pour en faciliter la compréhension auprès des débutants. Néanmoins, il recommande fortement de définir ces valeurs en tant que constantes.

const int SCREEN_WIDTH = 1280;
const int SCREEN_HEIGHT = 720;

Pour libérer les ressources utilisées pour initialiser la fenêtre de jeu et le contexte OpenGL, utilisez la fonction CloseWindow à la fin de votre programme :

void CloseWindow(void);

La fonction IsWindowReady permet de déterminer si la création de la fenêtre et du contexte OpenGL a bien fonctionné :

bool IsWindowReady(void);

**Remarque :** Cette fonction est utile lorsque vous avez plusieurs threads dans vos jeux.

    if (!IsWindowReady())
        return -1;

### Boucle de jeu

Les deux fonctions précédentes peuvent définir un programme raylib minimum :

#include "raylib.h"

int main()
{
    InitWindow(640, 360, "Titre");
    CloseWindow();
    return 0;
}

Cependant, si vous l'exécutez tel quel, il affiche la fenêtre puis la referme aussitôt et le programme se termine. Vous devez donc créer une boucle pour maintenir le jeu ouvert, gérer la mise à jour de l'état du jeu ainsi que l'affichage.

La fonction WindowShouldClose retourne une valeur booléenne indiquant si la touche associée à la sortie du jeu (par défaut, la touche ESC) vient d'être enfoncée ou si l'utilisateur a cliqué sur le bouton de fermeture de la fenêtre :

bool WindowShouldClose(void);

Vous pouvez donc vous en servir pour créer un boucle qui s'exécutera tant que l'utilisateur veut jouer :

while (!WindowShouldClose())
{

}

La touche de sortie du jeu du clavier correspond par défaut à la touche ESC mais vous pouvez la modifier avec la fonction SetExitKey :

void SetExitKey(int key);

- Le paramètre key correspond à un nombre associé à une touche du clavier. Utilisez une constante définie dans l'énumération KeyboardKey (voir la section "Clavier") pour plus de clarté.

**Astuce :** Si vous ne voulez pas qu'une touche du clavier ferme votre jeu, vous pouvez passer la valeur 0 à la fonction précédente :

// Aucune touche de sortie du jeu n'est définie
SetExitKey(0);

Une fois tout assemblé, vous avez donc la structure de code suivante :

#include "raylib.h"

int main()
{
    const int SCREEN_WIDTH = 640;
    const int SCREEN_HEIGHT = 360;
    InitWindow(SCREEN_WIDTH, SCREEN_HEIGHT, "Titre");
    while (!WindowShouldClose())
    {

    }
    CloseWindow();
    return 0;
}

Mais si vous exécutez ce programme, il restera figé dans une boucle infinie et ne répondra plus. Vous devez au minimum appeler l'une des fonctions BeginX et EndX dans la boucle :

#include "raylib.h"

int main()
{
    const int SCREEN_WIDTH = 640;
    const int SCREEN_HEIGHT = 360;
    InitWindow(SCREEN_WIDTH, SCREEN_HEIGHT, "Titre");
    while (!WindowShouldClose())
    {
        BeginDrawing();
        EndDrawing();
    }
    CloseWindow();
    return 0;
}

Cette fois le programme est fonctionnel. Cependant, la fenêtre affiche un écran clignotant désagréable car vous n'avez pas fixé la couleur de fond du tampon d'affichage de l'écran.

La fonction BeginDrawing prépare le canevas (le tampon d'affichage) pour les fonctions d'affichage à venir :

void BeginDrawing(void);

**Attention !** Si vous utilisez cette fonction, pensez à toujours appeler la fonction EndDrawing par la suite.

La fonction EndDrawing signale la fin des fonctions d'affichage et échange les tampons (double buffering) :

void EndDrawing(void);

La fonction BeginMode2D prépare le canevas (le tampon d'affichage) pour les fonctions d'affichage 2D à venir mais avec une structure Camera2D passée en argument :

void BeginMode2D(Camera2D camera);

- Le paramètre camera correspond à la caméra à utiliser dans les fonctions d'affichage suivantes.

**Attention !** Si vous utilisez cette fonction, pensez à toujours appeler la fonction EndMode2D par la suite.

La fonction EndMode2D signale la fin des fonctions d'affichage 2D avec une caméra 2D personnalisée et échange les tampons (double buffering) :

void EndMode2D(void);

La fonction BeginMode3D prépare le canevas (le tampon d'affichage) pour les fonctions d'affichage 3D à venir mais avec une structure Camera3D passée en argument :

void BeginMode3D(Camera3D camera);

- Le paramètre camera correspond à la caméra à utiliser dans les fonctions d'affichage suivantes.

**Attention !** Si vous utilisez cette fonction, pensez à toujours appeler la fonction EndMode3D par la suite.

La fonction EndMode3D signale la fin des fonctions d'affichage 3D avec une caméra 3D personnalisée et échange les tampons (double buffering). Après cette fonction, le contexte retourne à une vue orthographique 2D par défaut :

void EndMode3D(void);

La fonction BeginTextureMode prépare une texture de rendu (une structure RenderTexture2D passée en argument) pour les fonctions d'affichage à venir. Voici son prototype :

void BeginTextureMode(RenderTexture2D target);

- Le paramètre target correspond à la texture de rendu (un canevas) à utiliser dans les fonctions d'affichage suivantes. Cela permet de dessiner dans une texture au lieu du tampon de l'écran.

**Attention !** Si vous utilisez cette fonction, pensez à toujours appeler la fonction EndTextureMode par la suite.

La fonction EndTextureMode signale la fin des fonctions d'affichage dans la texture de rendu et échange les tampons (double buffering) :

void EndTextureMode(void);

### Remplir l'écran avec une couleur

La fonction ClearBackground définit la couleur de fond du tampon d'affichage de l'écran :

void ClearBackground(Color color);

- Le paramètre color correspond à la couleur à utiliser pour remplir le canevas.

Appelez cette fonction en lui passant une valeur de type Color (voir la section "Structures de données de base"). 

### Définir la fréquence de répétition de la boucle de jeu

La fonction SetTargetFPS définit la fréquence de rafraîchissement de la boucle de jeu :

void SetTargetFPS(int fps);

- Le paramètre fps correspond à la fréquence de rafraîchissement maximale à utiliser dans la boucle de jeu.

Appelez cette fonction après avoir initialisé la fenêtre et le contexte OpenGL (avec la fonction InitWindow) en lui passant la fréquence maximale de rafraîchissement de la boucle de jeu.

La fonction SetTargetFPS fonctionne comme ceci :

if (fps < 1)
    targetTime = 0.0;
else
    targetTime = 1.0/(double)fps;

Elle est contrôlée par ce code :

// Attend quelques millisecondes…
if (frameTime < targetTime)
{
    Wait((float)(targetTime - frameTime)*1000.0f);
    currentTime = GetTime();
    double extraTime = currentTime - previousTime;
    previousTime = currentTime;
    frameTime += extraTime;
}

La fonction SetTargetFPS fixe juste une temps maximum par image. Elle est liée à la fonction EndDrawing. Celle-ci vérifie que ce temps est écoulé ou pause l'exécution si besoin. Notez que la fonction Wait peut aussi bien être une boucle d'attente qu'une horloge d'interruption haute définition.

La fonction getFPS renvoie un entier représentant la fréquence de rafraîchissement réelle en cours :

int GetFPS(void);

La fonction DrawFPS affiche les FPS à l'écran :

void DrawFPS(int posX, int posY);

- Le paramètre posX correspond à la position en abscisse des FPS à afficher.
- Le paramètre posY correspond à la position en ordonnée des FPS à afficher.

### Obtenir le temps écoulé

La fonction GetFrameTime renvoie le temps écoulé en secondes depuis le dernier affichage (habituellement appelé delta time) :

float GetFrameTime(void);

La fonction GetTime renvoie le temps écoulé en secondes depuis l'appel de la fonction InitWindow (autrement dit, depuis le début de l'exécution du jeu) :

double GetTime(void);

### Gérer la fenêtre [Incomplet]

// Window and Graphics Device Functions (Module: core)

### Fonctions liées à la fenêtre

La fonction IsWindowMinimized retourne une valeur booléenne indiquant si la fenêtre de jeu est réduite ou a perdu le focus :

bool IsWindowMinimized(void);

La fonction IsWindowResized retourne une valeur booléenne indiquant si la fenêtre de jeu a été redimensionnée :

bool IsWindowResized(void);

La fonction IsWindowHidden retourne une valeur booléenne indiquant si la fenêtre de jeu est masquée :

bool IsWindowHidden(void);

La fonction ToggleFullscreen bascule la fenêtre de jeu entre le mode plein écran et le mode fenêtré (uniquement dans l'environnement PLATFORM_DESKTOP) :

void ToggleFullscreen(void);

La fonction UnhideWindow affiche la fenêtre de jeu :

void UnhideWindow(void);

La fonction HideWindow masque la fenêtre de jeu :

void HideWindow(void);

La fonction SetWindowIcon permet de définir l'icône de la fenêtre de jeu en passant une image en argument (uniquement dans l'environnement PLATFORM_DESKTOP) :

void SetWindowIcon(Image image);

- Le paramètre image correspond à l'image à définir comme icône.

La fonction SetWindowTitle permet de définir l'intitulé de la fenêtre de jeu en passant une chaîne de caractère en argument (uniquement dans l'environnement PLATFORM_DESKTOP) :

void SetWindowTitle(const char *title);

- Le paramètre title correspond à la chaîne de caractères à définir comme intitulé.

La fonction SetWindowPosition permet de définir la position de la fenêtre de jeu en passant les coordonnées du coin supérieur gauche en argument (uniquement dans l'environnement PLATFORM_DESKTOP) :

void SetWindowPosition(int x, int y);

- Le paramètre x correspond à l'abscisse à définir comme position.
- Le paramètre y correspond à l'ordonnée à définir comme position.

La fonction SetWindowMonitor permet, dans le cas d'un environnement à plusieurs écrans, de choisir l'écran où afficher la fenêtre de jeu en passant un entier correspondant au numéro d'écran en argument (uniquement en mode plein écran) :

void SetWindowMonitor(int monitor);

dfgh

La fonction SetWindowMinSize permet de définir les dimensions minimales de la fenêtre de jeu lorsqu'elle est redimensionnable en passant la largeur et la hauteur (en pixels) en argument (uniquement lorsque le statut FLAG_WINDOW_RESIZABLE est défini) :

void SetWindowMinSize(int width, int height);

dfsgf
sdg

La fonction SetWindowSize permet de définir les dimensions de la fenêtre de jeu en passant la largeur et la hauteur (en pixels) en argument :

void SetWindowSize(int width, int height);

xcvb
xg

La fonction GetWindowHandle  renvoie un pointeur correspondant à la ressource système associée à la fenêtre de jeu :

void *GetWindowHandle(void);

La fonction GetScreenWidth renvoie un entier correspondant à la largeur (en pixels) de la fenêtre de jeu :

int GetScreenWidth(void);

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

int GetScreenHeight(void);

La fonction GetScreenHeight renvoie un entier correspondant au nombre d'écrans disponibles du système :

int GetMonitorCount(void);

La fonction GetMonitorWidth renvoie un entier correspondant à la largeur totale (en pixels) de l'écran associé à l'entier passé en argument :

int GetMonitorWidth(int monitor);

gkkg

La fonction GetMonitorHeight renvoie un entier correspondant à la hauteur totale (en pixels) de l'écran associé à l'entier passé en argument :

int GetMonitorHeight(int monitor);

mkj

La fonction GetMonitorPhysicalWidth renvoie un entier correspondant à la largeur (en millimètres) de l'écran associé à l'entier passé en argument :

int GetMonitorPhysicalWidth(int monitor);

dgh

La fonction GetMonitorPhysicalHeight renvoie un entier correspondant à la hauteur (en millimètres) de l'écran associé à l'entier passé en argument :

int GetMonitorPhysicalHeight(int monitor);

fggh

La fonction GetMonitorName renvoie une chaîne de caractères (encodé au format UTF-8) correspondant au nom de l'écran associé à l'entier passé en argument :

const char *GetMonitorName(int monitor);

dfghfg

La fonction GetClipboardText renvoie une chaîne de caractères correspondant au texte contenu dans le presse papier :

const char *GetClipboardText(void);

La fonction SetClipboardText attribue au presse papier le texte passé en argument :

void SetClipboardText(const char *text);

dfghfg

// Screen-space-related functions
La fonction GetMouseRay renvoie une structure Ray correspondant au rayon partant de la caméra en direction de la position de la souris dans la fenêtre de jeu :

Ray GetMouseRay(Vector2 mousePosition, Camera camera);

La fonction GetWorldToScreen renvoie une structure Vector2 correspondant à la position dans la fenêtre de jeu d'un point par rapport à une caméra :

Vector2 GetWorldToScreen(Vector3 position, Camera camera);  // Returns the screen space position for a 3d world space position

// Misc. functions
La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

void SetConfigFlags(unsigned char flags);   // Setup window configuration flags (view FLAGS)

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

void SetTraceLogLevel(int logType); // Set the current threshold (minimum) log level

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

void SetTraceLogExit(int logType);  // Set the exit threshold (minimum) log level

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

void SetTraceLogCallback(TraceLogCallback callback);        // Set a trace log callback to enable custom logging

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

void TraceLog(int logType, const char *text, ...);  // Show trace log messages (LOG_DEBUG, LOG_INFO, LOG_WARNING, LOG_ERROR)

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

void TakeScreenshot(const char *fileName);  // Takes a screenshot of current screen (saved a .png)

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

int GetRandomValue(int min, int max);       // Returns a random value between min and max (both included)

## Fichiers [incomplet]

// Files management functions

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :
bool FileExists(const char *fileName);      // Check if file exists

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

bool IsFileExtension(const char *fileName, const char *ext);// Check file extension

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

const char *GetExtension(const char *fileName);     // Get pointer to extension for a filename string

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

const char *GetFileName(const char *filePath);      // Get pointer to filename for a path string

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

const char *GetFileNameWithoutExt(const char *filePath);    // Get filename string without extension (memory should be freed)

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

const char *GetDirectoryPath(const char *fileName); // Get full path for a given fileName (uses static string)

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

const char *GetWorkingDirectory(void);      // Get current working directory (uses static string)

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

char **GetDirectoryFiles(const char *dirPath, int *count);  // Get filenames in a directory path (memory should be freed)

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

void ClearDirectoryFiles(void);     // Clear directory files paths buffers (free memory)

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

bool ChangeDirectory(const char *dir);      // Change working directory, returns true if success

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

bool IsFileDropped(void);   // Check if a file has been dropped into window

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

char **GetDroppedFiles(int *count); // Get dropped files names (memory should be freed)

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

void ClearDroppedFiles(void);       // Clear dropped files paths buffer (free memory)

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

long GetFileModTime(const char *fileName);  // Get file modification time (last write time)

// Persistent storage management
La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

void StorageSaveValue(int position, int value);     // Save integer value to storage file (to defined position)

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

int StorageLoadValue(int position); // Load integer value from storage file (from defined position)

La fonction GetScreenHeight renvoie un entier correspondant à la hauteur (en pixels) de la fenêtre de jeu :

void OpenURL(const char *url);      // Open URL with default system browser (if available)

## Contrôles

### Clavier

#### Constantes associées au clavier

L'énumération KeyboardKey représente les constantes entières associées aux touches du clavier :

typedef enum {
    // Alphanumeric keys
    KEY_APOSTROPHE      = 39,
    KEY_COMMA           = 44,
    KEY_MINUS           = 45,
    KEY_PERIOD          = 46,
    KEY_SLASH           = 47,
    KEY_ZERO            = 48,
    KEY_ONE             = 49,
    KEY_TWO             = 50,
    KEY_THREE           = 51,
    KEY_FOUR            = 52,
    KEY_FIVE            = 53,
    KEY_SIX             = 54,
    KEY_SEVEN           = 55,
    KEY_EIGHT           = 56,
    KEY_NINE            = 57,
    KEY_SEMICOLON       = 59,
    KEY_EQUAL           = 61,
    KEY_A               = 65,
    KEY_B               = 66,
    KEY_C               = 67,
    KEY_D               = 68,
    KEY_E               = 69,
    KEY_F               = 70,
    KEY_G               = 71,
    KEY_H               = 72,
    KEY_I               = 73,
    KEY_J               = 74,
    KEY_K               = 75,
    KEY_L               = 76,
    KEY_M               = 77,
    KEY_N               = 78,
    KEY_O               = 79,
    KEY_P               = 80,
    KEY_Q               = 81,
    KEY_R               = 82,
    KEY_S               = 83,
    KEY_T               = 84,
    KEY_U               = 85,
    KEY_V               = 86,
    KEY_W               = 87,
    KEY_X               = 88,
    KEY_Y               = 89,
    KEY_Z               = 90,

    // Function keys
    KEY_SPACE           = 32,
    KEY_ESCAPE          = 256,
    KEY_ENTER           = 257,
    KEY_TAB             = 258,
    KEY_BACKSPACE       = 259,
    KEY_INSERT          = 260,
    KEY_DELETE          = 261,
    KEY_RIGHT           = 262,
    KEY_LEFT            = 263,
    KEY_DOWN            = 264,
    KEY_UP              = 265,
    KEY_PAGE_UP         = 266,
    KEY_PAGE_DOWN       = 267,
    KEY_HOME            = 268,
    KEY_END             = 269,
    KEY_CAPS_LOCK       = 280,
    KEY_SCROLL_LOCK     = 281,
    KEY_NUM_LOCK        = 282,
    KEY_PRINT_SCREEN    = 283,
    KEY_PAUSE           = 284,
    KEY_F1              = 290,
    KEY_F2              = 291,
    KEY_F3              = 292,
    KEY_F4              = 293,
    KEY_F5              = 294,
    KEY_F6              = 295,
    KEY_F7              = 296,
    KEY_F8              = 297,
    KEY_F9              = 298,
    KEY_F10             = 299,
    KEY_F11             = 300,
    KEY_F12             = 301,
    KEY_LEFT_SHIFT      = 340,
    KEY_LEFT_CONTROL    = 341,
    KEY_LEFT_ALT        = 342,
    KEY_LEFT_SUPER      = 343,
    KEY_RIGHT_SHIFT     = 344,
    KEY_RIGHT_CONTROL   = 345,
    KEY_RIGHT_ALT       = 346,
    KEY_RIGHT_SUPER     = 347,
    KEY_KB_MENU         = 348,
    KEY_LEFT_BRACKET    = 91,
    KEY_BACKSLASH       = 92,
    KEY_RIGHT_BRACKET   = 93,
    KEY_GRAVE           = 96,

    // Keypad keys
    KEY_KP_0            = 320,
    KEY_KP_1            = 321,
    KEY_KP_2            = 322,
    KEY_KP_3            = 323,
    KEY_KP_4            = 324,
    KEY_KP_5            = 325,
    KEY_KP_6            = 326,
    KEY_KP_7            = 327,
    KEY_KP_8            = 328,
    KEY_KP_9            = 329,
    KEY_KP_DECIMAL      = 330,
    KEY_KP_DIVIDE       = 331,
    KEY_KP_MULTIPLY     = 332,
    KEY_KP_SUBTRACT     = 333,
    KEY_KP_ADD          = 334,
    KEY_KP_ENTER        = 335,
    KEY_KP_EQUAL        = 336
} KeyboardKey;

#### Fonctions liées au clavier

raylib fournit les fonctions essentielles à la gestion des entrées au clavier.
La fonction IsKeyPressed renvoie si une touche du clavier vient juste d'être enfoncée ou non :

bool IsKeyPressed(int key);

- Le paramètre key correspond à une valeur entière associée à une touche du clavier. Vous pouvez utiliser une des constantes entières définie dans l'énumération KeyboardKey.

La fonction IsKeydown renvoie si une touche du clavier est enfoncée ou non au moment de l'appel à cette fonction :

bool IsKeyDown(int key);

- Le paramètre key correspond à une valeur entière associée à une touche du clavier. Vous pouvez utiliser une des constantes entières définie dans l'énumération KeyboardKey.

La fonction IsKeyReleased renvoie si une touche du clavier vient juste d'être relâchée ou non :

bool IsKeyReleased(int key);

- Le paramètre key correspond à une valeur entière associée à une touche du clavier. Vous pouvez utiliser une des constantes entières définie dans l'énumération KeyboardKey.

La fonction IsKeyUp renvoie si une touche du clavier est relâchée ou non au moment de l'appel à cette fonction :

bool IsKeyUp(int key);

- Le paramètre key correspond à une valeur entière associée à une touche du clavier. Vous pouvez utiliser une des constantes entières définie dans l'énumération KeyboardKey.

La fonction GetKeyPressed renvoie la valeur entière associée à la dernière touche du clavier qui a été enfoncée :

int GetKeyPressed(void);

### Gamepads

#### Constantes associées aux gamepads

raylib définit les énumérations suivantes :

GamepadNumber
typedef enum {
    GAMEPAD_PLAYER1     = 0,
    GAMEPAD_PLAYER2     = 1,
    GAMEPAD_PLAYER3     = 2,
    GAMEPAD_PLAYER4     = 3
} GamepadNumber;
GamepadPS3Button
typedef enum {
    GAMEPAD_PS3_BUTTON_TRIANGLE = 0,
    GAMEPAD_PS3_BUTTON_CIRCLE   = 1,
    GAMEPAD_PS3_BUTTON_CROSS    = 2,
    GAMEPAD_PS3_BUTTON_SQUARE   = 3,
    GAMEPAD_PS3_BUTTON_L1       = 6,
    GAMEPAD_PS3_BUTTON_R1       = 7,
    GAMEPAD_PS3_BUTTON_L2       = 4,
    GAMEPAD_PS3_BUTTON_R2       = 5,
    GAMEPAD_PS3_BUTTON_START    = 8,
    GAMEPAD_PS3_BUTTON_SELECT   = 9,
    GAMEPAD_PS3_BUTTON_PS       = 12,
    GAMEPAD_PS3_BUTTON_UP       = 24,
    GAMEPAD_PS3_BUTTON_RIGHT    = 25,
    GAMEPAD_PS3_BUTTON_DOWN     = 26,
    GAMEPAD_PS3_BUTTON_LEFT     = 27
} GamepadPS3Button;
GamepadPS3Axis
typedef enum {
    GAMEPAD_PS3_AXIS_LEFT_X     = 0,
    GAMEPAD_PS3_AXIS_LEFT_Y     = 1,
    GAMEPAD_PS3_AXIS_RIGHT_X    = 2,
    GAMEPAD_PS3_AXIS_RIGHT_Y    = 5,
    GAMEPAD_PS3_AXIS_L2         = 3,    // [1..-1] (pressure-level)
    GAMEPAD_PS3_AXIS_R2         = 4     // [1..-1] (pressure-level)
} GamepadPS3Axis;
GamepadXbox360Button
typedef enum {
    GAMEPAD_XBOX_BUTTON_A       = 0,
    GAMEPAD_XBOX_BUTTON_B       = 1,
    GAMEPAD_XBOX_BUTTON_X       = 2,
    GAMEPAD_XBOX_BUTTON_Y       = 3,
    GAMEPAD_XBOX_BUTTON_LB      = 4,
    GAMEPAD_XBOX_BUTTON_RB      = 5,
    GAMEPAD_XBOX_BUTTON_SELECT  = 6,
    GAMEPAD_XBOX_BUTTON_START   = 7,
    GAMEPAD_XBOX_BUTTON_HOME    = 8,
    GAMEPAD_XBOX_BUTTON_UP      = 10,
    GAMEPAD_XBOX_BUTTON_RIGHT   = 11,
    GAMEPAD_XBOX_BUTTON_DOWN    = 12,
    GAMEPAD_XBOX_BUTTON_LEFT    = 13
} GamepadXbox360Button;
GamepadXbox360Axis
typedef enum {
    GAMEPAD_XBOX_AXIS_LEFT_X    = 0,    // [-1..1] (left->right)
    GAMEPAD_XBOX_AXIS_LEFT_Y    = 1,    // [1..-1] (up->down)
    GAMEPAD_XBOX_AXIS_RIGHT_X   = 2,    // [-1..1] (left->right)
    GAMEPAD_XBOX_AXIS_RIGHT_Y   = 3,    // [1..-1] (up->down)
    GAMEPAD_XBOX_AXIS_LT        = 4,    // [-1..1] (pressure-level)
    GAMEPAD_XBOX_AXIS_RT        = 5     // [-1..1] (pressure-level)
} GamepadXbox360Axis;
GamepadAndroid
typedef enum {
    GAMEPAD_ANDROID_DPAD_UP     = 19,
    GAMEPAD_ANDROID_DPAD_DOWN   = 20,
    GAMEPAD_ANDROID_DPAD_LEFT   = 21,
    GAMEPAD_ANDROID_DPAD_RIGHT  = 22,
    GAMEPAD_ANDROID_DPAD_CENTER = 23,
    GAMEPAD_ANDROID_BUTTON_A    = 96,
    GAMEPAD_ANDROID_BUTTON_B    = 97,
    GAMEPAD_ANDROID_BUTTON_C    = 98,
    GAMEPAD_ANDROID_BUTTON_X    = 99,
    GAMEPAD_ANDROID_BUTTON_Y    = 100,
    GAMEPAD_ANDROID_BUTTON_Z    = 101,
    GAMEPAD_ANDROID_BUTTON_L1   = 102,
    GAMEPAD_ANDROID_BUTTON_R1   = 103,
    GAMEPAD_ANDROID_BUTTON_L2   = 104,
    GAMEPAD_ANDROID_BUTTON_R2   = 105
} GamepadAndroid;

#### Fonctions liées aux gamepads

raylib définit plusieurs fonctions pour gérer les entrées liées aux gamepads.
La fonction IsGamepadAvailable renvoie si un gamepad est disponible (s'il est bien raccordé par exemple) :

bool IsGamepadAvailable(int gamepad);

La fonction IsGamepadName renvoie si un gamepad correspond bien à un certain modèle (s'il est disponible) :

bool IsGamepadName(int gamepad, const char *name);

La fonction GetGamepadName renvoie une chaîne de caractère correspondant à un gamepad :

const char *GetGamepadName(int gamepad);        // Return gamepad internal name id

La fonction IsGamepadButtonPressed renvoie si un bouton d'un gamepad vient juste d'être enfoncé :

bool IsGamepadButtonPressed(int gamepad, int button);

La fonction IsGamepadButtonDown renvoie si un bouton d'un gamepad est enfoncé (au moment de l'exécution de cette fonction) :

bool IsGamepadButtonDown(int gamepad, int button);

La fonction IsGamepadButtonReleased renvoie si un bouton d'un gamepad vient juste d'être relâché :

bool IsGamepadButtonReleased(int gamepad, int button);

La fonction IsGamepadButtonUp renvoie si un bouton d'un gamepad est relâché (au moment de l'exécution de cette fonction) :

bool IsGamepadButtonUp(int gamepad, int button);

La fonction GetGamepadButtonPressed renvoie une valeur entière correspondant au dernier bouton d'un gamepad qui a été enfoncé :

int GetGamepadButtonPressed(void);

La fonction GetGamepadAxisCount renvoie le nombre d'axes analogiques qu'un gamepad possède :

int GetGamepadAxisCount(int gamepad);

La fonction GetGamepadAxisMovement renvoie un nombre à virgule flottante correspondant à la valeur de mouvement d'un axe analogique d'un gamepad :

float GetGamepadAxisMovement(int gamepad, int axis);

### Souris

raylib définit l'énumération MouseButton ainsi que plusieurs fonctions pour gérer la souris et son pointeur.

#### MouseButton

L'énumération MouseButton définit des constantes entières associées aux boutons de la souris :

typedef enum {
    MOUSE_LEFT_BUTTON   = 0,
    MOUSE_RIGHT_BUTTON  = 1,
    MOUSE_MIDDLE_BUTTON = 2
} MouseButton;

#### Fonctions liées à la souris

##### Contrôles de la souris

La fonction IsMouseButtonPressed renvoie si un bouton vient juste d'être enfoncé :

bool IsMouseButtonPressed(int button);

- Le paramètre button correspond au nombre associé au bouton de la souris. Vous pouvez utiliser l'énumération MouseButton pour plus de clarté.

La fonction IsMouseButtonDown renvoie si un bouton est enfoncé (au moment de l'exécution de cette fonction) :

bool IsMouseButtonDown(int button);

- Le paramètre button correspond au nombre associé au bouton de la souris. Vous pouvez utiliser l'énumération MouseButton pour plus de clarté.

La fonction IsMouseButtonReleased renvoie si un bouton vient juste d'être relâché :

bool IsMouseButtonReleased(int button);

- Le paramètre button correspond au nombre associé au bouton de la souris. Vous pouvez utiliser l'énumération MouseButton pour plus de clarté.

La fonction IsMouseButtonUp renvoie si un bouton est relâché (au moment de l'exécution de cette fonction) :

bool IsMouseButtonUp(int button);

- Le paramètre button correspond au nombre associé au bouton de la souris. Vous pouvez utiliser l'énumération MouseButton pour plus de clarté.

La fonction GetMouseX renvoie une valeur entière correspondant à la position horizontale du pointeur de la souris à l'écran :

int GetMouseX(void);

La fonction GetMouseX renvoie une valeur entière correspondant à la position verticale du pointeur de la souris à l'écran :

int GetMouseY(void);

La fonction GetMousePosition renvoie une structure Vector2 correspondant à la position du pointeur de la souris à l'écran :

Vector2 GetMousePosition(void);

La fonction SetMousePosition place le pointeur de la souris à l'écran aux coordonnées passées en argument :

void SetMousePosition(int x, int y);

- Le paramètre x correspond à la position horizontale à attribuer au pointeur de la souris.
- Le paramètre y correspond à la position verticale à attribuer au pointeur de la souris.

La fonction SetMouseOffset définit le décalage du pointeur de la souris à l'écran :

void SetMouseOffset(int offsetX, int offsetY);

- Le paramètre offsetX correspond au décalage horizontal à attribuer au pointeur de la souris.
- Le paramètre offsetY correspond au décalage vertical à attribuer au pointeur de la souris.

La fonction SetMouseScale définit l'échelle du pointeur de la souris à l'écran :

void SetMouseScale(float scaleX, float scaleY);

- Le paramètre scaleX correspond à l'échelle horizontale à attribuer au pointeur de la souris.
- Le paramètre scaleY correspond à l'échelle verticale à attribuer au pointeur de la souris.

La fonction GetMouseWheelMove renvoie une valeur entière correspondant au mouvement de la molette de la souris :

int GetMouseWheelMove(void);

#### Curseur de la souris

La fonction ShowCursor fait apparaître le pointeur de la souris :

void ShowCursor(void);

La fonction HideCursor masque le pointeur de la souris :

void HideCursor(void);

La fonction IsCursorHidden détermine si le pointeur de la souris est masqué ou non :

bool IsCursorHidden(void);

La fonction EnableCursor active le pointeur de la souris :

void EnableCursor(void);

La fonction DisableCursor désactive le pointeur de la souris :

void DisableCursor(void);

### Contrôles tactiles [incomplet]

// Input-related functions: touch
int GetTouchX(void);    // Returns touch position X for touch point 0 (relative to screen size)

int GetTouchY(void);    // Returns touch position Y for touch point 0 (relative to screen size)

Vector2 GetTouchPosition(int index);    // Returns touch position XY for a touch point index (relative to screen size)

void SetGesturesEnabled(unsigned int gestureFlags);     // Enable a set of gestures using flags

bool IsGestureDetected(int gesture);    // Check if a gesture have been detected

int GetGestureDetected(void);   // Get latest detected gesture

int GetTouchPointsCount(void);  // Get touch points count

float GetGestureHoldDuration(void);     // Get gesture hold time in milliseconds

Vector2 GetGestureDragVector(void);     // Get gesture drag vector

float GetGestureDragAngle(void);        // Get gesture drag angle

Vector2 GetGesturePinchVector(void);    // Get gesture pinch delta

float GetGesturePinchAngle(void);       // Get gesture pinch angle

## Caméras

### Structures de données liées aux caméras

#### Camera3D

La structure Camera3D définit les propriétés d'une caméra (position et orientation) dans un espace en trois dimensions :

typedef struct Camera3D {
    Vector3 position;
    Vector3 target;
    Vector3 up;
    float fovy;
    int type;
} Camera3D;

Le champ position correspond à la position de la caméra dans l'espace.
Le champ target correspond à la position du sujet que caméra cible dans l'espace.
Le champ up correspond à la direction du haut de la caméra dans l'espace (rotation sur son axe).
Le champ fovy correspond à l'ouverture du champ de vision vertical (en degrés) en perspective utilisé en tant que largeur d'un plan proche en vue orthographique.
Le champ type correspond au type de la caméra. Il définit le type de projection (CAMERA_PERSPECTIVE ou CAMERA_ORTHOGRAPHIC).

#### Camera

L'alias Camera est équivalent à la structure Camera3D :

typedef Camera3D Camera;

#### Camera2D

La structure Camera2D définit les propriétés d'une caméra dans un espace en deux dimensions :

typedef struct Camera2D {
    Vector2 offset;
    Vector2 target;
    float rotation;
    float zoom;
} Camera2D;

Le champ offset correspond au décalage par rapport à la cible (target) de la caméra.
Le champ target correspond à la cible de la caméra. Il définit la position du centre de rotation et de zoom.
Le champ rotation correspond à l'angle de rotation (en degrés) de la caméra.
Le champ zoom correspond au facteur d'agrandissement (l'échelle) de la caméra. Par défaut, il vaut 1.0f.

### Fonctions liées aux caméras [incomplet]

void SetCameraMode(Camera camera, int mode);        // Set camera mode (multiple camera modes available)

void UpdateCamera(Camera *camera);  // Update camera position for selected mode

void SetCameraPanControl(int panKey);       // Set camera pan key to combine with mouse movement (free camera)

void SetCameraAltControl(int altKey);       // Set camera alt key to combine with mouse movement (free camera)

void SetCameraSmoothZoomControl(int szKey); // Set camera smooth zoom key to combine with mouse (free camera)

void SetCameraMoveControls(int frontKey, int backKey, int rightKey, int leftKey, int upKey, int downKey); // Set camera move controls (1st person and 3rd person cameras)

La fonction GetCameraMatrix renvoie une structure Matrix correspondant à la matrice de transformation appliquée à la caméra passée en argument :

Matrix GetCameraMatrix(Camera camera);

- Le paramètre camera correspond à la caméra dont on veut obtenir la transformation.

## Formes géométriques 2D [incomplet]

raylib fournit une multitude de fonctions pour afficher des formes géométriques. Consultez la section "Structures de données de base" pour une description de la structure Color.

// Basic shapes drawing functions
void DrawPixel(int posX, int posY, Color color);   // Draw a pixel

void DrawPixelV(Vector2 position, Color color);    // Draw a pixel (Vector version)

void DrawLine(int startPosX, int startPosY, int endPosX, int endPosY, Color color);        // Draw a line

void DrawLineV(Vector2 startPos, Vector2 endPos, Color color);     // Draw a line (Vector version)

void DrawLineEx(Vector2 startPos, Vector2 endPos, float thick, Color color);       // Draw a line defining thickness

void DrawLineBezier(Vector2 startPos, Vector2 endPos, float thick, Color color);   // Draw a line using cubic-bezier curves in-out

void DrawCircle(int centerX, int centerY, float radius, Color color);      // Draw a color-filled circle

void DrawCircleSector(Vector2 center, float radius, int startAngle, int endAngle, int segments, Color color);     // Draw a piece of a circle

void DrawCircleSectorLines(Vector2 center, float radius, int startAngle, int endAngle, int segments, Color color);    // Draw circle sector outline

void DrawCircleGradient(int centerX, int centerY, float radius, Color color1, Color color2);       // Draw a gradient-filled circle

void DrawCircleV(Vector2 center, float radius, Color color);       // Draw a color-filled circle (Vector version)

void DrawCircleLines(int centerX, int centerY, float radius, Color color); // Draw circle outline

void DrawRing(Vector2 center, float innerRadius, float outerRadius, int startAngle, int endAngle, int segments, Color color); // Draw ring

void DrawRingLines(Vector2 center, float innerRadius, float outerRadius, int startAngle, int endAngle, int segments, Color color);    // Draw ring outline

void DrawRectangle(int posX, int posY, int width, int height, Color color);        // Draw a color-filled rectangle

void DrawRectangleV(Vector2 position, Vector2 size, Color color);  // Draw a color-filled rectangle (Vector version)

void DrawRectangleRec(Rectangle rec, Color color); // Draw a color-filled rectangle

void DrawRectanglePro(Rectangle rec, Vector2 origin, float rotation, Color color); // Draw a color-filled rectangle with pro parameters

void DrawRectangleGradientV(int posX, int posY, int width, int height, Color color1, Color color2);// Draw a vertical-gradient-filled rectangle

void DrawRectangleGradientH(int posX, int posY, int width, int height, Color color1, Color color2);// Draw a horizontal-gradient-filled rectangle

void DrawRectangleGradientEx(Rectangle rec, Color col1, Color col2, Color col3, Color col4);       // Draw a gradient-filled rectangle with custom vertex colors

void DrawRectangleLines(int posX, int posY, int width, int height, Color color);   // Draw rectangle outline

void DrawRectangleLinesEx(Rectangle rec, int lineThick, Color color);      // Draw rectangle outline with extended parameters

void DrawRectangleRounded(Rectangle rec, float roundness, int segments, Color color);      // Draw rectangle with rounded edges

void DrawRectangleRoundedLines(Rectangle rec, float roundness, int segments, int lineThick, Color color); // Draw rectangle with rounded edges outline

void DrawTriangle(Vector2 v1, Vector2 v2, Vector2 v3, Color color);        // Draw a color-filled triangle

void DrawTriangleLines(Vector2 v1, Vector2 v2, Vector2 v3, Color color);   // Draw triangle outline

void DrawPoly(Vector2 center, int sides, float radius, float rotation, Color color);       // Draw a regular polygon (Vector version)

void DrawPolyEx(Vector2 *points, int numPoints, Color color);      // Draw a closed polygon defined by points

void DrawPolyExLines(Vector2 *points, int numPoints, Color color); // Draw polygon lines

void SetShapesTexture(Texture2D texture, Rectangle source);        // Define default texture used to draw shapes

## Détection de collisions en 2D [incomplet]

// Basic shapes collision detection functions
bool CheckCollisionRecs(Rectangle rec1, Rectangle rec2);   // Check collision between two rectangles

bool CheckCollisionCircles(Vector2 center1, float radius1, Vector2 center2, float radius2);        // Check collision between two circles

bool CheckCollisionCircleRec(Vector2 center, float radius, Rectangle rec); // Check collision between circle and rectangle

Rectangle GetCollisionRec(Rectangle rec1, Rectangle rec2); // Get collision rectangle for two rectangles collision

bool CheckCollisionPointRec(Vector2 point, Rectangle rec); // Check if point is inside rectangle

bool CheckCollisionPointCircle(Vector2 point, Vector2 center, float radius);       // Check if point is inside circle

bool CheckCollisionPointTriangle(Vector2 point, Vector2 p1, Vector2 p2, Vector2 p3);       // Check if point is inside a triangle

## Images

### Structures liées aux images

#### Image

Le type Image représente une image stockée dans la mémoire de l'ordinateur (RAM) en représentation RVBA 32 bits :

typedef struct Image {
    void *data;
    int width;
    int height;
    int mipmaps;
    int format;
} Image;

Le champ data correspond à la donnée brute de l'image.
Le champ width correspond à la largeur de base de l'image.
Le champ height correspond à la hauteur de base de l'image.
Le champ mipmaps correspond au niveau de mipmap (par défaut 1).
Le champ format correspond au format de donnée (type PixelFormat).

#### Texture2D

Le type Texture2D représente une texture stockée dans la mémoire de la carte graphique (VRAM) :

typedef struct Texture2D {
    unsigned int id;
    int width;
    int height;
    int mipmaps;
    int format;
} Texture2D;

Le champ id correspond à l'identifiant de texture d'OpenGL.
Le champ width correspond à la largeur de base de la texture.
Le champ height correspond à la hauteur de base de la texture.
Le champ mipmaps correspond au niveau de mipmap (par défaut 1).
Le champ format correspond au format de donnée (type PixelFormat).

#### Texture et TextureCubemap

Le type Texture et le type TextureCubemap représentent des textures stockées dans la mémoire de la carte graphique (VRAM) identiques au type Texture2D :

typedef Texture2D Texture;
typedef Texture2D TextureCubemap;

#### RenderTexture2D

Le type RenderTexture représente une texture de rendu :

typedef struct RenderTexture2D {
    unsigned int id;        // OpenGL Framebuffer Object (FBO) id
    Texture2D texture;      // Color buffer attachment texture
    Texture2D depth;        // Depth buffer attachment texture
    bool depthTexture;      // Track if depth attachment is a texture or renderbuffer
} RenderTexture2D;

Le champ id correspond à l'identifiant OpenGL FBO (Framebuffer Object).
Le champ texture correspond à la texture attachée au tampon de couleur.
Le champ depth correspond à la texture attachée au tampon de profondeur.
Le champ depthTexture précise si l'image attachée au tampon de profondeur est une texture ou un tampon de rendu (renderbuffer).

#### RenderTexture

Le type RenderTexture est identique au type RenderTexture2D :

typedef RenderTexture2D RenderTexture;

#### NPatchInfo

La structure NPatchInfo définit un n-patch associé à une texture :

typedef struct NPatchInfo {
    Rectangle sourceRec;
    int left;
    int top;
    int right;
    int bottom;
    int type;
} NPatchInfo;

Le champ sourceRec correspond au rectangle définissant la région dans la texture.
Le champ left correspond au décalage du côté gauche.
Le champ top correspond au décalage du côté droit.
Le champ right correspond au décalage du haut.
Le champ bottom correspond au décalage du bas.
Le champ type correspond au type de disposition du n-patch (voir l'énumération NPatchType ci-dessous).

L'énumération NPatchType, associée au type NPatchInfo, définit des constantes entières représentant le type de n-patch :

typedef enum {
    NPT_9PATCH = 0,         // Npatch defined by 3x3 tiles
    NPT_3PATCH_VERTICAL,    // Npatch defined by 1x3 tiles
    NPT_3PATCH_HORIZONTAL   // Npatch defined by 3x1 tiles
} NPatchType;

### Fonctions liées aux images [incomplet]

raylib fournit de très nombreuses fonctions pour manipuler ou afficher des images ou des textures.
// Image/Texture2D data loading/unloading/saving functions
Image LoadImage(const char *fileName);     // Load image from file into CPU memory (RAM)

Image LoadImageEx(Color *pixels, int width, int height);   // Load image from Color array data (RGBA - 32bit)

Image LoadImagePro(void *data, int width, int height, int format); // Load image from raw data with parameters

Image LoadImageRaw(const char *fileName, int width, int height, int format, int headerSize);       // Load image from RAW file data

void UnloadImage(Image image);     // Unload image from CPU memory (RAM)

void ExportImage(Image image, const char *fileName);       // Export image data to file

void ExportImageAsCode(Image image, const char *fileName); // Export image as code file defining an array of bytes

Texture2D LoadTexture(const char *fileName);       // Load texture from file into GPU memory (VRAM)

Texture2D LoadTextureFromImage(Image image);       // Load texture from image data

void UnloadTexture(Texture2D texture);     // Unload texture from GPU memory (VRAM)

TextureCubemap LoadTextureCubemap(Image image, int layoutType);    // Load cubemap from image, multiple image cubemap layouts supported

RenderTexture2D LoadRenderTexture(int width, int height);  // Load texture for rendering (framebuffer)

void UnloadRenderTexture(RenderTexture2D target);  // Unload render texture from GPU memory (VRAM)

Color *GetImageData(Image image);  // Get pixel data from image as a Color struct array

Vector4 *GetImageDataNormalized(Image image);      // Get pixel data from image as Vector4 array (float normalized)

int GetPixelDataSize(int width, int height, int format);   // Get pixel data size in bytes (image or texture)

Image GetTextureData(Texture2D texture);   // Get pixel data from GPU texture and return an Image

Image GetScreenData(void); // Get pixel data from screen buffer and return an Image (screenshot)

void UpdateTexture(Texture2D texture, const void *pixels); // Update GPU texture with new data

// Image manipulation functions
Image ImageCopy(Image image);      // Create an image duplicate (useful for transformations)

void ImageToPOT(Image *image, Color fillColor);    // Convert image to POT (power-of-two)

void ImageFormat(Image *image, int newFormat);     // Convert image data to desired format

void ImageAlphaMask(Image *image, Image alphaMask);        // Apply alpha mask to image

void ImageAlphaClear(Image *image, Color color, float threshold);  // Clear alpha channel to desired color

void ImageAlphaCrop(Image *image, float threshold);        // Crop image depending on alpha value

void ImageAlphaPremultiply(Image *image);  // Premultiply alpha channel

void ImageCrop(Image *image, Rectangle crop);      // Crop an image to a defined rectangle

void ImageResize(Image *image, int newWidth, int newHeight);       // Resize image (Bicubic scaling algorithm)

void ImageResizeNN(Image *image, int newWidth,int newHeight);      // Resize image (Nearest-Neighbor scaling algorithm)

void ImageResizeCanvas(Image *image, int newWidth, int newHeight, int offsetX, int offsetY, Color color);  // Resize canvas and fill with color

void ImageMipmaps(Image *image);   // Generate all mipmap levels for a provided image

void ImageDither(Image *image, int rBpp, int gBpp, int bBpp, int aBpp);    // Dither image data to 16bpp or lower (Floyd-Steinberg dithering)

Color *ImageExtractPalette(Image image, int maxPaletteSize, int *extractCount);    // Extract color palette from image to maximum size (memory should be freed)

Image ImageText(const char *text, int fontSize, Color color);      // Create an image from text (default font)

Image ImageTextEx(Font font, const char *text, float fontSize, float spacing, Color tint); // Create an image from text (custom sprite font)

void ImageDraw(Image *dst, Image src, Rectangle srcRec, Rectangle dstRec); // Draw a source image within a destination image

void ImageDrawRectangle(Image *dst, Rectangle rec, Color color);   // Draw rectangle within an image

void ImageDrawRectangleLines(Image *dst, Rectangle rec, int thick, Color color);   // Draw rectangle lines within an image

void ImageDrawText(Image *dst, Vector2 position, const char *text, int fontSize, Color color);     // Draw text (default font) within an image (destination)

void ImageDrawTextEx(Image *dst, Vector2 position, Font font, const char *text, float fontSize, float spacing, Color color); // Draw text (custom sprite font) within an image (destination)

void ImageFlipVertical(Image *image);      // Flip image vertically

void ImageFlipHorizontal(Image *image);    // Flip image horizontally

void ImageRotateCW(Image *image);  // Rotate image clockwise 90deg

void ImageRotateCCW(Image *image); // Rotate image counter-clockwise 90deg

void ImageColorTint(Image *image, Color color);    // Modify image color: tint

void ImageColorInvert(Image *image);       // Modify image color: invert

void ImageColorGrayscale(Image *image);    // Modify image color: grayscale

void ImageColorContrast(Image *image, float contrast);     // Modify image color: contrast (-100 to 100)

void ImageColorBrightness(Image *image, int brightness);   // Modify image color: brightness (-255 to 255)

void ImageColorReplace(Image *image, Color color, Color replace);  // Modify image color: replace color

// Image generation functions
Image GenImageColor(int width, int height, Color color);   // Generate image: plain color

Image GenImageGradientV(int width, int height, Color top, Color bottom);   // Generate image: vertical gradient

Image GenImageGradientH(int width, int height, Color left, Color right);   // Generate image: horizontal gradient

Image GenImageGradientRadial(int width, int height, float density, Color inner, Color outer);      // Generate image: radial gradient

Image GenImageChecked(int width, int height, int checksX, int checksY, Color col1, Color col2);    // Generate image: checked

Image GenImageWhiteNoise(int width, int height, float factor);     // Generate image: white noise

Image GenImagePerlinNoise(int width, int height, int offsetX, int offsetY, float scale);   // Generate image: perlin noise

Image GenImageCellular(int width, int height, int tileSize);       // Generate image: cellular algorithm. Bigger tileSize means bigger cells

// Texture2D configuration functions
void GenTextureMipmaps(Texture2D *texture);        // Generate GPU mipmaps for a texture

void SetTextureFilter(Texture2D texture, int filterMode);  // Set texture scaling filter mode
SetTextureFilter(target.texture, FILTER_POINT)

// Texture parameters: filter mode
// NOTE 1: Filtering considers mipmaps if available in the texture
// NOTE 2: Filter is accordingly set for minification and magnification

typedef enum {
   FILTER_POINT = 0,               // No filter, just pixel aproximation
   FILTER_BILINEAR,                // Linear filtering
   FILTER_TRILINEAR,               // Trilinear filtering (linear with mipmaps)
   FILTER_ANISOTROPIC_4X,          // Anisotropic filtering 4x
   FILTER_ANISOTROPIC_8X,          // Anisotropic filtering 8x
   FILTER_ANISOTROPIC_16X,         // Anisotropic filtering 16x
} TextureFilterMode;

void SetTextureWrap(Texture2D texture, int wrapMode);      // Set texture wrapping mode

// Texture2D drawing functions
void DrawTexture(Texture2D texture, int posX, int posY, Color tint);       // Draw a Texture2D

void DrawTextureV(Texture2D texture, Vector2 position, Color tint);        // Draw a Texture2D with position defined as Vector2

void DrawTextureEx(Texture2D texture, Vector2 position, float rotation, float scale, Color tint);  // Draw a Texture2D with extended parameters

void DrawTextureRec(Texture2D texture, Rectangle sourceRec, Vector2 position, Color tint); // Draw a part of a texture defined by a rectangle

void DrawTextureQuad(Texture2D texture, Vector2 tiling, Vector2 offset, Rectangle quad, Color tint);  // Draw texture quad with tiling and offset parameters

void DrawTexturePro(Texture2D texture, Rectangle sourceRec, Rectangle destRec, Vector2 origin, float rotation, Color tint);       // Draw a part of a texture defined by a rectangle with 'pro' parameters

void DrawTextureNPatch(Texture2D texture, NPatchInfo nPatchInfo, Rectangle destRec, Vector2 origin, float rotation, Color tint);  // Draws a texture (or part of it) that stretches or shrinks nicely

## Texte [incomplet]

### Structures de données liées au texte

#### CharInfo

// Font character info
typedef struct CharInfo {
    int value;      // Character value (Unicode)
    Rectangle rec;  // Character rectangle in sprite font
    int offsetX;    // Character offset X when drawing
    int offsetY;    // Character offset Y when drawing
    int advanceX;   // Character advance position X
    unsigned char *data;    // Character pixel data (grayscale)
} CharInfo;

#### Font

// Font type, includes texture and charSet array data
typedef struct Font {
    Texture2D texture;      // Font texture
    int baseSize;   // Base size (default chars height)
    int charsCount; // Number of characters
    CharInfo *chars;        // Characters info data
} Font;

#### SpriteFont

#define SpriteFont Font     // SpriteFont type fallback, defaults to Font
Polices de caractères
// Font loading/unloading functions
Font GetFontDefault(void);    // Get the default Font

Font LoadFont(const char *fileName);  // Load font from file into GPU memory (VRAM)

Font LoadFontEx(const char *fileName, int fontSize, int *fontChars, int charsCount);  // Load font from file with extended parameters

Font LoadFontFromImage(Image image, Color key, int firstChar);        // Load font from Image (XNA style)

CharInfo *LoadFontData(const char *fileName, int fontSize, int *fontChars, int charsCount, int type); // Load font data for further use

Image GenImageFontAtlas(CharInfo *chars, int charsCount, int fontSize, int padding, int packMethod);  // Generate image font atlas using chars info

void UnloadFont(Font font);   // Unload Font from GPU memory (VRAM)

### Fonctions liées au texte

// Text drawing functions
void DrawText(const char *text, int posX, int posY, int fontSize, Color color);       // Draw text (using default font)

void DrawTextEx(Font font, const char *text, Vector2 position, float fontSize, float spacing, Color tint);        // Draw text using font and additional parameters

void DrawTextRec(Font font, const char *text, Rectangle rec, float fontSize, float spacing, bool wordWrap, Color tint);   // Draw text using font inside rectangle limits

void DrawTextRecEx(Font font, const char *text, Rectangle rec, float fontSize, float spacing, bool wordWrap, Color tint,
 int selectStart, int selectLength, Color selectText, Color selectBack);    // Draw text using font inside rectangle limits with support for text selection

// Text misc. functions
int MeasureText(const char *text, int fontSize);      // Measure string width for default font

Vector2 MeasureTextEx(Font font, const char *text, float fontSize, float spacing);    // Measure string size for Font

int GetGlyphIndex(Font font, int character);  // Get index position for a unicode character on font

// Text strings management functions
// NOTE: Some strings allocate memory internally for returned strings, just be careful!
bool TextIsEqual(const char *text1, const char *text2);       // Check if two text string are equal

unsigned int TextLength(const char *text);    // Get text length, checks for '\0' ending

const char *TextFormat(const char *text, ...);        // Text formatting with variables (sprintf style)

const char *TextSubtext(const char *text, int position, int length);  // Get a piece of a text string

const char *TextReplace(char *text, const char *replace, const char *by);     // Replace text string (memory should be freed!)

const char *TextInsert(const char *text, const char *insert, int position);   // Insert text in a position (memory should be freed!)

const char *TextJoin(const char **textList, int count, const char *delimiter);        // Join text strings with delimiter

const char **TextSplit(const char *text, char delimiter, int *count); // Split text into multiple strings

void TextAppend(char *text, const char *append, int *position);       // Append text at specific position and move cursor!

int TextFindIndex(const char *text, const char *find);        // Find first text occurrence within a string

const char *TextToUpper(const char *text);      // Get upper case version of provided string

const char *TextToLower(const char *text);      // Get lower case version of provided string

const char *TextToPascal(const char *text);     // Get Pascal case notation version of provided string

int TextToInteger(const char *text);    // Get integer value from text (negative values not supported)

## Formes géométriques 3D [incomplet]

raylib fournit un ensemble de fonctions pour afficher des formes géométriques en trois dimensions. Consultez la section "Structures de données de base" pour une description de la structure Color.

// Basic geometric 3D shapes drawing functions
void DrawLine3D(Vector3 startPos, Vector3 endPos, Color color);    // Draw a line in 3D world space

void DrawCircle3D(Vector3 center, float radius, Vector3 rotationAxis, float rotationAngle, Color color); // Draw a circle in 3D world space

void DrawCube(Vector3 position, float width, float height, float length, Color color);     // Draw cube

void DrawCubeV(Vector3 position, Vector3 size, Color color);       // Draw cube (Vector version)

void DrawCubeWires(Vector3 position, float width, float height, float length, Color color);        // Draw cube wires

void DrawCubeWiresV(Vector3 position, Vector3 size, Color color);  // Draw cube wires (Vector version)

void DrawCubeTexture(Texture2D texture, Vector3 position, float width, float height, float length, Color color); // Draw cube textured

void DrawSphere(Vector3 centerPos, float radius, Color color);     // Draw sphere

void DrawSphereEx(Vector3 centerPos, float radius, int rings, int slices, Color color);    // Draw sphere with extended parameters

void DrawSphereWires(Vector3 centerPos, float radius, int rings, int slices, Color color); // Draw sphere wires

void DrawCylinder(Vector3 position, float radiusTop, float radiusBottom, float height, int slices, Color color); // Draw a cylinder/cone

void DrawCylinderWires(Vector3 position, float radiusTop, float radiusBottom, float height, int slices, Color color); // Draw a cylinder/cone wires

void DrawPlane(Vector3 centerPos, Vector2 size, Color color);      // Draw a plane XZ

void DrawRay(Ray ray, Color color);        // Draw a ray line

void DrawGrid(int slices, float spacing);  // Draw a grid (centered at (0, 0, 0))

void DrawGizmo(Vector3 position);  // Draw simple gizmo
//DrawTorus(), DrawTeapot() could be useful?

## Modèles 3D [incomplet]

### Structures liées aux modèles 3D

#### Mesh

// Vertex data definning a mesh
// NOTE: Data stored in CPU memory (and GPU)
typedef struct Mesh {
    int vertexCount;        // Number of vertices stored in arrays
    int triangleCount;      // Number of triangles stored (indexed or not)

    // Default vertex data
    float *vertices;        // Vertex position (XYZ - 3 components per vertex) (shader-location = 0)
    float *texcoords;       // Vertex texture coordinates (UV - 2 components per vertex) (shader-location = 1)
    float *texcoords2;      // Vertex second texture coordinates (useful for lightmaps) (shader-location = 5)
    float *normals; // Vertex normals (XYZ - 3 components per vertex) (shader-location = 2)
    float *tangents;        // Vertex tangents (XYZW - 4 components per vertex) (shader-location = 4)
    unsigned char *colors;  // Vertex colors (RGBA - 4 components per vertex) (shader-location = 3)
    unsigned short *indices;// Vertex indices (in case vertex data comes indexed)

    // Animation vertex data
    float *animVertices;    // Animated vertex positions (after bones transformations)
    float *animNormals;     // Animated normals (after bones transformations)
    int *boneIds;   // Vertex bone ids, up to 4 bones influence by vertex (skinning)
    float *boneWeights;     // Vertex bone weight, up to 4 bones influence by vertex (skinning)

    // OpenGL identifiers
    unsigned int vaoId;     // OpenGL Vertex Array Object id
    unsigned int vboId[7];  // OpenGL Vertex Buffer Objects id (default vertex data)
} Mesh;

#### MaterialMap

// Material texture map
typedef struct MaterialMap {
    Texture2D texture;      // Material map texture
    Color color;    // Material map color
    float value;    // Material map value
} MaterialMap;

#### Material

// Material type (generic)
typedef struct Material {
    Shader shader;  // Material shader
    MaterialMap maps[MAX_MATERIAL_MAPS]; // Material maps
    float *params;  // Material generic parameters (if required)
} Material;

**Remarque :** La constante symbolique MAX_MATERIAL_MAP correspond au nombre maximum de cartes de textures stockées dans la structure Shader :

#define MAX_MATERIAL_MAPS 12

#### Transform

// Transformation properties
typedef struct Transform {
    Vector3 translation;    // Translation
    Quaternion rotation;    // Rotation
    Vector3 scale;  // Scale
} Transform;

#### BoneInfo

// Bone information
typedef struct BoneInfo {
    char name[32];  // Bone name
    int parent;     // Bone parent
} BoneInfo;
#### Model

// Model type
typedef struct Model {
    Matrix transform;       // Local transform matrix

    int meshCount;  // Number of meshes
    Mesh *meshes;   // Meshes array

    int materialCount;      // Number of materials
    Material *materials;    // Materials array
    int *meshMaterial;      // Mesh material number

    // Animation data
    int boneCount;  // Number of bones
    BoneInfo *bones;        // Bones information (skeleton)
    Transform *bindPose;    // Bones base transformation (pose)
} Model;

#### ModelAnimation

// Model animation
typedef struct ModelAnimation {
    int boneCount;  // Number of bones
    BoneInfo *bones;        // Bones information (skeleton)

    int frameCount; // Number of animation frames
    Transform **framePoses; // Poses array by frame
} ModelAnimation;

### Fonctions liées aux modèles 3D

//------------------------------------------------------------------------------------
// Model 3d Loading and Drawing Functions (Module: models)
//------------------------------------------------------------------------------------

// Model loading/unloading functions
Model LoadModel(const char *fileName);    // Load model from files (meshes and materials)

Model LoadModelFromMesh(Mesh mesh);       // Load model from generated mesh (default material)

void UnloadModel(Model model);    // Unload model from memory (RAM and/or VRAM)

// Mesh loading/unloading functions
Mesh *LoadMeshes(const char *fileName, int *meshCount);   // Load meshes from model file

void ExportMesh(Mesh mesh, const char *fileName); // Export mesh data to file

void UnloadMesh(Mesh *mesh);      // Unload mesh from memory (RAM and/or VRAM)

// Material loading/unloading functions
Material *LoadMaterials(const char *fileName, int *materialCount);        // Load materials from model file

Material LoadMaterialDefault(void);       // Load default material (Supports: DIFFUSE, SPECULAR, NORMAL maps)

void UnloadMaterial(Material material);   // Unload material from GPU memory (VRAM)

void SetMaterialTexture(Material *material, int mapType, Texture2D texture);      // Set texture for a material map type (MAP_DIFFUSE, MAP_SPECULAR...)

void SetModelMeshMaterial(Model *model, int meshId, int materialId);      // Set material for a mesh

// Model animations loading/unloading functions
ModelAnimation *LoadModelAnimations(const char *fileName, int *animsCount);       // Load model animations from file

void UpdateModelAnimation(Model model, ModelAnimation anim, int frame);   // Update model animation pose

void UnloadModelAnimation(ModelAnimation anim);   // Unload animation data

bool IsModelAnimationValid(Model model, ModelAnimation anim);     // Check model animation skeleton match

// Mesh generation functions
Mesh GenMeshPoly(int sides, float radius);        // Generate polygonal mesh

Mesh GenMeshPlane(float width, float length, int resX, int resZ); // Generate plane mesh (with subdivisions)

Mesh GenMeshCube(float width, float height, float length);        // Generate cuboid mesh

Mesh GenMeshSphere(float radius, int rings, int slices);  // Generate sphere mesh (standard sphere)

Mesh GenMeshHemiSphere(float radius, int rings, int slices);      // Generate half-sphere mesh (no bottom cap)

Mesh GenMeshCylinder(float radius, float height, int slices);     // Generate cylinder mesh

Mesh GenMeshTorus(float radius, float size, int radSeg, int sides);       // Generate torus mesh

Mesh GenMeshKnot(float radius, float size, int radSeg, int sides);        // Generate trefoil knot mesh

Mesh GenMeshHeightmap(Image heightmap, Vector3 size);     // Generate heightmap mesh from image data

Mesh GenMeshCubicmap(Image cubicmap, Vector3 cubeSize);   // Generate cubes-based map mesh from image data

// Mesh manipulation functions
BoundingBox MeshBoundingBox(Mesh mesh);   // Compute mesh bounding box limits

void MeshTangents(Mesh *mesh);    // Compute mesh tangents

void MeshBinormals(Mesh *mesh);   // Compute mesh binormals

// Model drawing functions
void DrawModel(Model model, Vector3 position, float scale, Color tint);   // Draw a model (with texture if set)

void DrawModelEx(Model model, Vector3 position, Vector3 rotationAxis, float rotationAngle, Vector3 scale, Color tint); // Draw a model with extended parameters

void DrawModelWires(Model model, Vector3 position, float scale, Color tint);      // Draw a model wires (with texture if set)

void DrawModelWiresEx(Model model, Vector3 position, Vector3 rotationAxis, float rotationAngle, Vector3 scale, Color tint); // Draw a model wires (with texture if set) with extended parameters
void DrawBoundingBox(BoundingBox box, Color color);       // Draw bounding box (wires)

void DrawBillboard(Camera camera, Texture2D texture, Vector3 center, float size, Color tint);     // Draw a billboard texture

void DrawBillboardRec(Camera camera, Texture2D texture, Rectangle sourceRec, Vector3 center, float size, Color tint); // Draw a billboard texture defined by sourceRec

## Détection de collisions en 3D

raylib fournit quelques structures et des fonctions de détection de collision de volumes 3D.
### Structures liées aux collisions 3D [incomplet]

#### Ray

// Ray type (useful for raycast)
typedef struct Ray {
    Vector3 position;       // Ray position (origin)
    Vector3 direction;      // Ray direction
} Ray;

#### RayHitInfo

// Raycast hit information
typedef struct RayHitInfo {
    bool hit;       // Did the ray hit something?
    float distance; // Distance to nearest hit
    Vector3 position;       // Position of nearest hit
    Vector3 normal; // Surface normal of hit
} RayHitInfo;

#### BoundingBox

// Bounding box type
typedef struct BoundingBox {
    Vector3 min;    // Minimum vertex box-corner
    Vector3 max;    // Maximum vertex box-corner
} BoundingBox;

### Fonctions de détection de collision 3D

La fonction CheckCollisionSpheres renvoie si deux sphères entrent en collision ou non :

bool CheckCollisionSpheres(Vector3 centerA, float radiusA, Vector3 centerB, float radiusB);

- Le paramètre centerA correspond à la position du centre de la première sphère.
- Le paramètre radiusA correspond au rayon de la première sphère.
- Le paramètre centerB correspond à la position du centre de la seconde sphère.
- Le paramètre radiusB correspond au rayon de la seconde sphère.

La fonction CheckCollisionBoxes renvoie si deux boîtes de collision (bounding box) entrent en collision ou non :

bool CheckCollisionBoxes(BoundingBox box1, BoundingBox box2);

- Le paramètre box1 correspond à la première boîte de collision.
- Le paramètre box2 correspond à la seconde boîte de collision.

La fonction CheckCollisionBoxSphere renvoie si une boîte de collision et une sphère entrent en collision ou non :

bool CheckCollisionBoxSphere(BoundingBox box, Vector3 centerSphere, float radiusSphere);

- Le paramètre box correspond à la boîte de collision.
- Le paramètre centerSphere correspond à la position du centre de la sphère.
- Le paramètre radiusSphere correspond au rayon de la sphère.

La fonction CheckCollisionRaySphere renvoie si un rayon et une sphère entrent en collision ou non :

bool CheckCollisionRaySphere(Ray ray, Vector3 spherePosition, float sphereRadius);

- Le paramètre ray correspond au rayon.
- Le paramètre spherePosition correspond à la position du centre de la sphère.
- Le paramètre sphereRadius correspond au rayon de la sphère.

La fonction CheckCollisionRaySphereEx renvoie si un rayon et une sphère entrent en collision ou non :

bool CheckCollisionRaySphereEx(Ray ray, Vector3 spherePosition, float sphereRadius, Vector3 *collisionPoint);

- Le paramètre ray correspond au rayon.
- Le paramètre spherePosition correspond à la position du centre de la sphère.
- Le paramètre sphereRadius correspond au rayon de la sphère.
- Le paramètre collisionPoint correspond au point de collision.

**Remarque :** Ce dernier paramètre est modifié par la fonction pour renvoyer le point de collision.

La fonction CheckCollisionRayBox renvoie si un rayon et une boîte de collision entrent en collision ou non :

bool CheckCollisionRayBox(Ray ray, BoundingBox box);

- Le paramètre ray correspond au rayon.
- Le paramètre box correspond à la boîte de collision.

La fonction GetCollisionRayModel renvoie une structure RayHitInfo correspondant aux informations de collision entre un rayon et un modèle :

RayHitInfo GetCollisionRayModel(Ray ray, Model *model);

- Le paramètre ray correspond au rayon.
- Le paramètre model correspond au modèle.

La fonction GetCollisionRayTriangle renvoie une structure RayHitInfo correspondant aux informations de collision entre un rayon et un triangle :

RayHitInfo GetCollisionRayTriangle(Ray ray, Vector3 p1, Vector3 p2, Vector3 p3);

- Le paramètre ray correspond au rayon.
- Le paramètre p1 correspond au premier point du triangle.
- Le paramètre p2 correspond au deuxième point du triangle.
- Le paramètre p3 correspond au troisième point du triangle.

La fonction GetCollisionRayGround renvoie une structure RayHitInfo correspondant aux informations de collision entre un rayon et un plan horizontal (perpendiculaire à l'axe Y) :

RayHitInfo GetCollisionRayGround(Ray ray, float groundHeight);

- Le paramètre ray correspond au rayon.
- Le paramètre groundHeight correspond à la position Y du plan.

## Shaders [incomplet]

### Structure Shader

La structure Shader définit un shader générique :

typedef struct Shader {
    unsigned int id;
    int locs[MAX_SHADER_LOCATIONS];
} Shader;

Le champ id correspond à l'identificateur du programme du shader.
Le champ locs correspond à un tableau contenant les lieux où se trouve le shader.

**Remarque :** La constante symbolique MAX_SHADER_LOCATIONS correspond au nombre maximum de lieux stockés dans la structure Shader :

#define MAX_SHADER_LOCATIONS 32

### Fonctions liées aux shaders

raylib fournit de nombreuses fonctions pour utiliser des shaders et propose même un module autonome dédié à représenter  une couche d'abstraction OpenGL via le fichier en-tête rlgl.h :
https://github.com/raysan5/raylib/blob/master/src/rlgl.h

**Remarque :** Les fonctions de ce chapitre ne fonctionnent pas avec OpenGL 1.1.

#### Fonctions de chargement / déchargement de shaders

char *LoadText(const char *fileName);       // Load chars array from text file

Shader LoadShader(const char *vsFileName, const char *fsFileName);  // Load shader from files and bind default locations

**Attention !** Si vous utilisez cette fonction, pensez à toujours appeler la fonction UnloadShader par la suite.

Shader LoadShaderCode(char *vsCode, char *fsCode);  // Load shader from code strings and bind default locations

**Attention !** Si vous utilisez cette fonction, pensez à toujours appeler la fonction UnloadShader par la suite.

void UnloadShader(Shader shader);   // Unload shader from GPU memory (VRAM)

Shader GetShaderDefault(void);      // Get default shader

Texture2D GetTextureDefault(void);  // Get default texture

#### Fonctions de configuration de shaders

int GetShaderLocation(Shader shader, const char *uniformName);      // Get shader uniform location

void SetShaderValue(Shader shader, int uniformLoc, const void *value, int uniformType);       // Set shader uniform value

void SetShaderValueV(Shader shader, int uniformLoc, const void *value, int uniformType, int count);   // Set shader uniform value vector

void SetShaderValueMatrix(Shader shader, int uniformLoc, Matrix mat); // Set shader uniform value (matrix 4x4)

void SetShaderValueTexture(Shader shader, int uniformLoc, Texture2D texture); // Set shader uniform value for texture

void SetMatrixProjection(Matrix proj);      // Set a custom projection matrix (replaces internal projection matrix)

void SetMatrixModelview(Matrix view);       // Set a custom modelview matrix (replaces internal modelview matrix)

Matrix GetMatrixModelview();        // Get internal modelview matrix

#### Génération de carte de textures (PBR)

// NOTE: Required shaders should be provided
Texture2D GenTextureCubemap(Shader shader, Texture2D skyHDR, int size);       // Generate cubemap texture from HDR texture

Texture2D GenTextureIrradiance(Shader shader, Texture2D cubemap, int size);   // Generate irradiance texture using cubemap data

Texture2D GenTexturePrefilter(Shader shader, Texture2D cubemap, int size);    // Generate prefilter texture using cubemap data

Texture2D GenTextureBRDF(Shader shader, int size);  // Generate BRDF texture

#### Fonctions de début et fin de shaders

void BeginShaderMode(Shader shader);        // Begin custom shader drawing

**Attention !** Si vous utilisez cette fonction, pensez à toujours appeler la fonction EndShaderMode par la suite.

void EndShaderMode(void);   // End custom shader drawing (use default shader)

void BeginBlendMode(int mode);      // Begin blending mode (alpha, additive, multiplied)

**Attention !** Si vous utilisez cette fonction, pensez à toujours appeler la fonction EndBlendMode par la suite.

void EndBlendMode(void);    // End blending mode (reset to default: alpha blending)

void BeginScissorMode(int x, int y, int width, int height); // Begin scissor mode (define screen area for following drawing)

**Attention !** Si vous utilisez cette fonction, pensez à toujours appeler la fonction EndScissorMode par la suite.

void EndScissorMode(void);  // End scissor mode

## Réalité virtuelle

raylib fournit la structure VrDeviceInfo ainsi qu'un certain nombre de fonctions pour contrôler les jeux en réalité virtuelle.

### VrDeviceInfo

La structure VrDeviceInfo définit les paramètres d'un casque de réalité virtuelle (HMD) :

typedef struct VrDeviceInfo {
    int hResolution;
    int vResolution;
    float hScreenSize;
    float vScreenSize;
    float vScreenCenter;
    float eyeToScreenDistance;
    float lensSeparationDistance;
    float interpupillaryDistance;
    float lensDistortionValues[4];
    float chromaAbCorrection[4];
} VrDeviceInfo;

Le champ hResolution correspond à la résolution horizontale de l'écran (en pixels) du casque.
Le champ vResolution correspond à la résolution verticale de l'écran (en pixels) du casque.
Le champ hScreenSize correspond à la taille horizontale de l'écran (en mètres) du casque.
Le champ vScreenSize correspond à la taille verticale de l'écran (en mètres) du casque.
Le champ vScreenCenter correspond au centre de l'écran (en mètres) du casque.
Le champ eyeToScreenDistance correspond à la distance (en mètres) entre les yeux et l'écran du casque.
Le champ lensSeparationDistance correspond à la distance (en mètres) séparant les lentilles du casque.
Le champ interpupillaryDistance correspond à la distance (en mètres) entre les pupilles.
Le champ lensDistortionValues correspond à un tableau de quatre constantes définissant les paramètres de distorsion des lentilles.
Le champ chromaAbCorrection correspond à un tableau de quatre valeurs définissant les paramètres d'aberration chromatique.

### Fonctions liées à la réalité virtuelle

La fonction InitVrSimulator initialise le simulateur de réalité virtuelle pour les paramètres du périphérique sélectionné :

void InitVrSimulator(void);

La fonction CloseVrSimulator ferme le simulateur de réalité virtuelle pour le périphérique actuel :

void CloseVrSimulator(void);

La fonction UpdateVrTracking met à jour le suivi de réalité virtuelle (la position et l'orientation) et la caméra :

void UpdateVrTracking(Camera *camera);

- Le paramètre camera correspond à la caméra à utiliser.

[Incomplet]
La fonction SetVrConfiguration définit les paramètres de configuration de rendu stéréo :

void SetVrConfiguration(VrDeviceInfo info, Shader distortion);

- Le paramètre info correspond à ????????????.
- Le paramètre distortion correspond à ????????????????????.

La fonction IsVrSimulatorReady renvoie si le simulateur de réalité virtuelle est prêt ou non :
 
bool IsVrSimulatorReady(void);

La fonction ToggleVrMode active ou désactive l'expérience de réalité virtuelle :

void ToggleVrMode(void);

La fonction BeginVrDrawing signale le début du rendu stéréo pour le simulateur de réalité virtuelle :

void BeginVrDrawing(void);

**Attention !** Si vous utilisez cette fonction, pensez à toujours appeler la fonction EndVrDrawing par la suite.

La fonction EndVrDrawing signale la fin du rendu stéréo pour le simulateur de réalité virtuelle :

void EndVrDrawing(void);

## Audio

raylib fournit de nombreuses fonctions et structures de données pour gérer l'audio. Vous pouvez également vous servir de ces fonctionnalités de manière indépendante grâce au fichier en-tête raudio.h.

### Structures de données pour l'audio

#### Wave

La structure Wave définit une donnée audio au format WAVE. Elle est utilisée pour charger des fichiers de ce format en mémoire. Vous pouvez ensuite convertir cette donnée en structure Sound pour la lire : 

typedef struct Wave {
    unsigned int sampleCount;
    unsigned int sampleRate;
    unsigned int sampleSize;
    unsigned int channels;
    void *data;
} Wave;

Le champ sampleCount correspond au nombre d'échantillons de la donnée.
Le champ sampleRate correspond à la fréquence d'échantillonnage (en nombre d'échantillon par seconde) de la donnée.
Le champ sampleSize correspond au nombre de bits utilisés pour représenter un échantillon (8, 16 ou 32 bits).
Le champ channels correspond au nombre de canaux utilisés par la donnée (1 : mono, 2 : stéréo).
Le champ data correspond à un pointeur vers le tampon où se trouve la donnée brute.

#### Sound

La structure Sound définit une donnée audio de préférence courte (un son) chargée entièrement en mémoire et qui peut être lue directement :

typedef struct Sound {
    void *audioBuffer;
    unsigned int source;
    unsigned int buffer;
    int format;
} Sound;

Le champ audioBuffer correspond à un pointeur vers la donnée interne utilisée par le système audio.
Le champ source correspond à l'identifiant de la source audio.
Le champ buffer correspond à l'identifiant du tampon audio.
Le champ format correspond au spécificateur de format audio.

#### Music

L'alias Music est un pointeur vers une structure MusicData (définie dans le fichier raudio.c). Il permet de lire un fichier audio en streaming directement depuis le disque. Pour économiser des ressources, la donnée audio du fichier n'est pas chargée en mémoire mais utilise un tampon qui doit être mis à jour à chaque répétition de la boucle de jeu :

typedef struct MusicData *Music;

**Remarque :** Toute donnée audio d'une durée supérieure à 10 secondes devrait être lue en tant que flux.

#### AudioStream

La structure AudioStream définit un flux audio que vous pouvez manipuler à votre guide. C'est le type à utiliser pour effectuer des traitements sur des données audio :

typedef struct AudioStream {
    unsigned int sampleRate;
    unsigned int sampleSize;
    unsigned int channels;
    void *audioBuffer;
    int format;
    unsigned int source;
    unsigned int buffers[2];
} AudioStream;

Le champ sampleRate correspond à la fréquence (en échantillons par seconde) du flux audio.
Le champ sampleSize correspond au nombre de bits utilisés pour représenter un échantillon (8, 16 ou 32 bits) du flux audio.
Le champ channels correspond au nombre de canaux utilisés par le flux audio (1 : mono, 2 : stéréo).
Le champ audioBuffer correspond à un pointeur vers la donnée interne utilisée par le système audio.
Le champ format correspond au spécificateur du format audio.
Le champ source correspond à l'identifiant de la source audio.
Le champ buffers correspond à un tableau de deux tampons audio (double buffering).

**Remarque :** La structure AudioStream est utile pour créer des flux audio personnalisés non liés à un fichier spécifique.

### Fonctions liées à l'audio

#### Gestion du périphérique audio

La fonction InitAudioDevice initialise le périphérique audio et son contexte :

void InitAudioDevice(void);

**Attention !** Si vous utilisez cette fonction, pensez à toujours appeler la fonction CloseAudioDevice par la suite.

La fonction CloseAudioDevice ferme le périphérique audio et son contexte :

void CloseAudioDevice(void);

La fonction IsAudioDeviceReady renvoie si le périphérique audio a été initialisé avec succès ou non :

bool IsAudioDeviceReady(void);

La fonction SetMasterVolume définit le volume maître (listener) :

void SetMasterVolume(float volume);

#### Chargement / déchargement de sons

La fonction LoadWave charge une donnée audio au format WAVE depuis un fichier :

Wave LoadWave(const char *fileName);

- Le paramètre fileName correspond au nom du fichier.

**Attention !** Si vous utilisez cette fonction, pensez à toujours appeler la fonction UnloadWave par la suite.

La fonction LoadWaveEx charge une donnée audio au format WAVE depuis un tableau de données audio brutes :

Wave LoadWaveEx(void *data, int sampleCount, int sampleRate, int sampleSize, int channels);

- Le paramètre data correspond au pointeur sur la donnée audio brute.
- Le paramètre sampleRate correspond à la fréquence d'échantillonnage.
- Le paramètre sampleSize correspond au à la taille des échantillons.
- Le paramètre channels correspond au nombre de canaux.

**Attention !** Si vous utilisez cette fonction, pensez à toujours appeler la fonction UnloadWave par la suite.

La fonction UnloadWave décharge une donnée audio au format WAVE et libère la mémoire :

void UnloadWave(Wave wave);

- Le paramètre wave correspond à la donnée audio au format WAVE à décharger.

La fonction ExportWave exporte une donnée au format WAVE vers un fichier :

void ExportWave(Wave wave, const char *fileName);

- Le paramètre wave correspond à la donnée audio au format WAVE à exporter.
- Le paramètre fileName correspond au nom du fichier.

La fonction ExportWaveAsCode exporte un échantillon de donnée audio au format WAVE vers tableau contenu dans un fichier en-tête (.h) :

void ExportWaveAsCode(Wave wave, const char *fileName);

- Le paramètre wave correspond à la donnée audio au format WAVE à exporter.
- Le paramètre fileName correspond au nom du fichier.

La fonction LoadSound charge un son depuis un fichier :

Sound LoadSound(const char *fileName);

- Le paramètre fileName correspond au nom du fichier.

**Attention !** Si vous utilisez cette fonction, pensez à toujours appeler la fonction UnloadSound par la suite.

La fonction LoadSoundFromWave charge un son depuis une donnée audio au format WAVE :

Sound LoadSoundFromWave(Wave wave);

- Le paramètre wave correspond à la donnée audio au format WAVE.

**Attention !** Si vous utilisez cette fonction, pensez à toujours appeler la fonction UnloadSound par la suite.

La fonction UpdateSound met à jour le tampon audio avec une nouvelle donnée. Elle permet de modifier la donnée brute d'une donnée Sound :

void UpdateSound(Sound sound, const void *data, int samplesCount);

- Le paramètre sound correspond au son.
- Le paramètre data correspond à la donnée à passer au tampon.
- Le paramètre samplesCount correspond au nombre d'échantillons.

La fonction UnloadSound décharge un son et libère la mémoire :

void UnloadSound(Sound sound);

- Le paramètre sound correspond au son à décharger.

### Gestion des sons

La fonction PlaySound lance la lecture d'un son :

void PlaySound(Sound sound);

- Le paramètre sound correspond au son à lire.

La fonction PauseSound met en pause la lecture d'un son :

void PauseSound(Sound sound);

- Le paramètre sound correspond au son à mettre en pause.

La fonction ResumeSound reprend la lecture d'un son mis en pause :

void ResumeSound(Sound sound);

- Le paramètre sound correspond au son dont la lecture doit reprendre.

La fonction StopSound stoppe la lecture d'un son :

void StopSound(Sound sound);

- Le paramètre sound correspond au son à stopper.

La fonction IsSoundPlaying renvoie si un son est en lecture ou non :

bool IsSoundPlaying(Sound sound);

- Le paramètre sound correspond au son à contrôler.

La fonction SetSoundVolume définit le volume d'un son (1.0 correspond à la valeur maximale) :

void SetSoundVolume(Sound sound, float volume);

- Le paramètre sound correspond au son à modifier.
- Le paramètre volume correspond au volume à attribuer.

La fonction SetSoundPitch définit la hauteur d'un son (1.0 est la hauteur d'origine) :

void SetSoundPitch(Sound sound, float pitch);

- Le paramètre sound correspond au son à modifier.
- Le paramètre pitch correspond à la hauteur à attribuer.

La fonction WaveFormat convertit une donnée audio au format WAVE vers le format désiré :

void WaveFormat(Wave *wave, int sampleRate, int sampleSize, int channels);

- Le paramètre wave correspond à la donnée audio au format WAVE à modifier.
- Le paramètre sampleRate correspond à la fréquence d'échantillonnage.
- Le paramètre sampleSize correspond à la taille des échantillons.
- Le paramètre channels correspond au nombre de canaux.

La fonction WaveCopy retourne une copie d'une donnée audio au format WAVE :

Wave WaveCopy(Wave wave);

- Le paramètre wave correspond à la donnée audio au format WAVE à copier.

La fonction WaveCrop recadre une donnée audio au format WAVE sur un intervalle d'échantillons défini :

void WaveCrop(Wave *wave, int initSample, int finalSample);

- Le paramètre wave correspond à la donnée audio au format WAVE à recadrer.
- Le paramètre initSample correspond à l'échantillon de départ.
- Le paramètre finalSample correspond à l'échantillon d'arrivée.

La fonction GetWaveData renvoie les données d'échantillons depuis une donnée audio au format WAVE sous la forme d'un tableau de nombres à virgule flottante :

float *GetWaveData(Wave wave);

- Le paramètre wave correspond à la donnée audio au format WAVE à convertir.

### Gestion de musiques

La fonction LoadMusicStream charge un flux de musique depuis un fichier :

Music LoadMusicStream(const char *fileName);

- Le paramètre fileName correspond au nom du fichier.

**Attention !** Si vous utilisez cette fonction, pensez à toujours appeler la fonction UnloadMusicStream par la suite.

La fonction UnloadMusicStream décharge un flux de musique et libère la mémoire :

void UnloadMusicStream(Music music);

- Le paramètre music correspond au flux de musique à décharger.

La fonction PlayMusicStream lance la lecture d'un flux de musique :

void PlayMusicStream(Music music);

- Le paramètre music correspond au flux de musique à lire.

La fonction UpdateMusicStream met à jour les tampons associés au flux de musique :

void UpdateMusicStream(Music music);

**Attention !** Cette fonction doit être appelé à chaque répétition de la boucle de jeu pour mettre à jour le tampon associé à une donnée Music.

- Le paramètre music correspond au flux de musique à mettre à jour.

La fonction StopMusicStream stoppe la lecture d'un flux de musique :

void StopMusicStream(Music music);

- Le paramètre music correspond au flux de musique à stopper.

La fonction PauseMusicStream met en pause la lecture d'un flux de musique :

void PauseMusicStream(Music music);

- Le paramètre music correspond au flux de musique à mettre en pause.

La fonction ResumeMusicStream reprend la lecture d'un flux de musique mis en pause :

void ResumeMusicStream(Music music);

- Le paramètre music correspond au flux de musique dont la lecture doit reprendre.

La fonction IsMusicPlaying renvoie si un flux de musique est en lecture ou non :

bool IsMusicPlaying(Music music);

- Le paramètre music correspond au flux de musique à contrôler.

La fonction SetMusicVolume définit le volume d'un flux de musique (1.0 correspond à la valeur maximale) :

void SetMusicVolume(Music music, float volume);

- Le paramètre music correspond au flux de musique à modifier.
- Le paramètre volume correspond au volume à attribuer.

La fonction SetMusicPitch définit la hauteur d'un flux de musique (1.0 est la hauteur d'origine) :

void SetMusicPitch(Music music, float pitch);

- Le paramètre music correspond au flux de musique à modifier.
- Le paramètre pitch correspond à la hauteur à attribuer.

La fonction SetMusicLoopCount définit le nombre de répétitions de lecture d'un flux de musique avant son arrêt :

void SetMusicLoopCount(Music music, int count);

- Le paramètre music correspond au flux de musique.
- Le paramètre count correspond au nombre de répétition à effectuer.

La fonction GetMusicTimeLength renvoie la durée (en secondes) d'un flux de musique :

float GetMusicTimeLength(Music music);

- Le paramètre music correspond au flux de musique à examiner.

La fonction GetMusicTimePlayed renvoie le temps écoulé (en secondes) depuis le début de la lecture d'un flux de musique :

float GetMusicTimePlayed(Music music);

- Le paramètre music correspond au flux de musique à examiner.

### Gestion des flux audio

La fonction InitAudioStream initialise un flux audio (pour lire en flux continu une donnée pcm audio brute) et renvoie une structure AudioStream :

AudioStream InitAudioStream(unsigned int sampleRate, unsigned int sampleSize, unsigned int channels);

- Le paramètre sampleRate correspond à la fréquence d'échantillonnage.
- Le paramètre sampleSize correspond à la taille des échantillons.
- Le paramètre channels correspond au nombre de canaux.

**Attention !** Si vous utilisez cette fonction, pensez à toujours appeler la fonction CloseAudioStream par la suite.

La fonction UpdateAudioStream met à jour les tampons de flux audio avec la donnée correspondante :

void UpdateAudioStream(AudioStream stream, const void *data, int samplesCount);

- Le paramètre stream correspond au flux audio à mettre à jour.
- Le paramètre data correspond à la donnée à passer au flux audio.
- Le paramètre samplesCount correspond au nombre d'échantillons à mettre à jour.

**Attention !** Cette fonction doit être appelé à chaque répétition de la boucle de jeu pour mettre à jour le tampon associé à une donnée AudioStream.

La fonction CloseAudioStream ferme un flux audio et libère la mémoire :

void CloseAudioStream(AudioStream stream);

- Le paramètre stream correspond au flux audio à décharger.

La fonction IsAudioBufferProcessed renvoie si un des tampons de flux audio à besoin d'être rempli à nouveau  ou non :

bool IsAudioBufferProcessed(AudioStream stream);

- Le paramètre stream correspond au flux audio à contrôler.

La fonction PlayAudioStream lance la lecture d'un flux audio :

void PlayAudioStream(AudioStream stream);

- Le paramètre stream correspond au flux audio à lire.

La fonction PauseAudioStream met en pause la lecture d'un flux audio :

void PauseAudioStream(AudioStream stream);

- Le paramètre stream correspond au flux audio à mettre en pause.

La fonction ResumeAudioStream reprend la lecture d'un flux audio mis en pause :

void ResumeAudioStream(AudioStream stream);

- Le paramètre stream correspond au flux audio dont la lecture doit reprendre.

La fonction IsAudioStreamPlaying renvoie si un flux audio est en lecture ou non :

bool IsAudioStreamPlaying(AudioStream stream);

- Le paramètre stream correspond au flux audio à contrôler.

La fonction StopAudioStream stoppe la lecture d'un flux audio :

void StopAudioStream(AudioStream stream);

- Le paramètre stream correspond au flux audio à stopper.

La fonction SetAudioStreamVolume définit le volume d'un flux audio (1.0 correspond à la valeur maximale) :

void SetAudioStreamVolume(AudioStream stream, float volume);

- Le paramètre stream correspond au flux audio à modifier.
- Le paramètre volume correspond au volume à attribuer.

La fonction SetAudioStreamPitch définit la hauteur d'un flux de musique (1.0 est la hauteur d'origine) :

void SetAudioStreamPitch(AudioStream stream, float pitch);

- Le paramètre stream correspond au flux audio à modifier.
- Le paramètre pitch correspond à la hauteur à attribuer.
