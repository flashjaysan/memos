# Mémo pygame

_par flashjaysan_

## Présentation

pygame est une bibliothèque pour Python destinée au développement de jeux vidéos.

pygame est constitué de différents modules. Les fonctionalités graphiques tournent autour du concept de _surfaces_, similaires à des calques que vous pouvez manipuler à votre convenance.

## Installation

```python
pip install pygame
```

**Remarque :** Sur Windows, vous aurez peût-être besoin d'exécuter la commande en étant administrateur.

## Préparation

- Créez un fichier source à l'emplacement de votre choix.
- Faites référence aux ressources nécessaires (sprites, sons, etc...) relativement à cet emplacement.

## Importer le module

Importez le module `pygame`.

```python
import pygame
```

## Initialiser les différents modules

Initialisez le module `pygame` et la plupart de ses sous-modules avec la fonction `init`.

```python
pygame.init()
```

**Remarque :** Cette fonction renvoie un tuple de deux nombres. Le premier indique le nombre de modules correctement initialisés et le second indique le nombre de modules dont l'initialisation a échoué.

**Attention !** Certains sous-modules (comme par exemple `mixer`) doivent être initialisés à part si vous souhaitez les utiliser. Pensez à appeler leur propre fonction `init` pour les initialiser.

## Quitter proprement

Utilisez la fonction `quit` avant de terminer votre programme. Cette fonction dé-initialise les modules initialisés par la fonction `init`.

```python
pygame.quit()
```

**Attention !** Certains sous-modules (comme par exemple `mixer`) doivent être initialisés à part si vous souhaitez les utiliser. Pensez à appeler leur propre fonction `quit` pour terminer votre programme.

## Définir le titre de la fenêtre

Utilisez la fonction `set_caption` du sous-module `display` pour définir le titre de la fenêtre.

```python
pygame.display.set_caption(titre, titre_minifie)
```

Le paramètre `titre_minifie` est optionnel. Il définit le titre de la fenêtre lorsque celle-ci est minifiée.

```python
pygame.display.set_caption(titre)
```

## Définir l'icône de la fenêtre

Utilisez la fonction `set_icon` du sous-module `display` pour définir l'icône de la fenêtre. Passez en argument une surface (de préférence 32x32). Vous pouvez également définir une couleur transparente (voir la méthode `set_colorkey`).

```python
pygame.display.set_icon(icone)
```

**Attention !** Définissez l'icône de la fenêtre avant de créer cette dernière (avec la fonction `set_mode`). Certains environnements n'autorisent pas la définition d'une icône une fois la fenêtre créée.

## Créer et définir les dimensions de la fenêtre

Utilisez la fonction `set_mode` du sous-module `display` pour créer la fenêtre de jeu. Passez les dimensions sous forme de tuple ou de liste. Cette fonction renvoie une surface spéciale correspondant à la surface associée à la fenêtre de jeu. Je l'appelerai la _surface d'affichage_.

```python
display_surface = pygame.display.set_mode((largeur, hauteur))
```

**Remarque :** Le système de coordonnées de pygame inverse l'axe vertical par rapport au système classique mathématique. Les valeurs verticales augmentent donc vers le bas. L'origine du repère est situé dans le coin supérieur gauche de la fenêtre.

La fonction `set_mode` peut également prendre des paramètres nommés supplémentaires.

- `flags=0` : Ces _drapeaux_ permettent de configurer la surface d'affichage selon diverses options. Les drapeaux disponibles (combinables aves l'opérateur de bit `|`) sont les suivants :
  - `pygame.FULLSCREEN` : crée une fenêtre en plein écran.
  - `pygame.DOUBLEBUF` : recommandé pour les HWSURFACE ou OPENGL.
  - `pygame.HWSURFACE` : crée surface avec accélération matérielle (uniquement en plein écran).
  - `pygame.OPENGL` : crée une fenêtre prenant en charge le rendu OpenGL.
  - `pygame.RESIZABLE` : crée une fenêtre redimensionable.
  - `pygame.NOFRAME` : crée une fenêtre sans bordure ni boutons de contrôle.
  - `pygame.SCALED` : crée une fenêtre avec des graphismes zoomés adaptés à la résolution courante du système.
  - `pygame.SHOWN` : la fenêtre est visible (par défaut).
  - `pygame.HIDDEN` : la fenêtre est masquée.
- `depth=0` : Précise le nombre de bits utilisés pour représenter les couleurs sur la surface. Il est préférable de laisser ce paramètre à sa valeur par défaut et pygame configurera la meilleure option disponible pour la surface d'affichage.
- `display=0` : Définit l'écran associé à la fenêtre. Par défaut, la fenêtre s'affiche sur l'écran principal.
- `vsync=0` : Essaie d'activer la synchronisation verticale avec l'écran. La tentative d'activation peut échouer. Cette option est à l'heure actuelle expérimentale.

## Les couleurs

pygame définit une classe `Color`. Elle représente une couleur constituée des composantes rouges, vertes et bleues et d'une valeur d'opacité (alpha). Ces composantes sont représentées sous la forme d'entiers compris entre 0 et 255. Si la valeur d'opacité n'est pas précisée, elle vaut 255 par défaut. Créez une instance de la classe `Color` en passant les composantes dans un tuple (ou une liste).

```python
BLACK_COLOR = pygame.Color((0, 0, 0))
```

Vous pouvez également utiliser un entier sous forme hexadécimale (`0xrrggbbaa`) mais la valeur d'opacité est cette fois indispensable.

```python
WHITE_COLOR = pygame.Color(0xFFFFFFFF)
```

**Remarque :** Vous avez également la possibilité de passer une chaine contenant la valeur hexadécimale sous la forme `'0xrrggbbaa'` ou `'0xrrggbb'` ou encore utiliser une chaine contenant le format HTML `'#rrggbbaa'` ou `'#rrggbb'`.

Enfin, vous pouvez également utiliser l'une des [chaines suivantes](https://www.pygame.org/docs/ref/color_list.html) pour désigner une couleur prédéfine définie dans le fichier source `colordict.py` :

```
'aliceblue': (240, 248, 255, 255)
'antiquewhite': (250, 235, 215, 255)
'antiquewhite1': (255, 239, 219, 255)
'antiquewhite2': (238, 223, 204, 255)
'antiquewhite3': (205, 192, 176, 255)
'antiquewhite4': (139, 131, 120, 255)
'aquamarine': (127, 255, 212, 255)
'aquamarine1': (127, 255, 212, 255)
'aquamarine2': (118, 238, 198, 255)
'aquamarine3': (102, 205, 170, 255)
'aquamarine4': (69, 139, 116, 255)
'azure': (240, 255, 255, 255)
'azure1': (240, 255, 255, 255)
'azure3': (193, 205, 205, 255)
'azure2': (224, 238, 238, 255)
'azure4': (131, 139, 139, 255)
'beige': (245, 245, 220, 255)
'bisque': (255, 228, 196, 255)
'bisque1': (255, 228, 196, 255)
'bisque2': (238, 213, 183, 255)
'bisque3': (205, 183, 158, 255)
'bisque4': (139, 125, 107, 255)
'black': (0, 0, 0, 255)
'blanchedalmond': (255, 235, 205, 255)
'blue': (0, 0, 255, 255)
'blue1': (0, 0, 255, 255)
'blue2': (0, 0, 238, 255)
'blue3': (0, 0, 205, 255)
'blue4': (0, 0, 139, 255)
'blueviolet': (138, 43, 226, 255)
'brown': (165, 42, 42, 255)
'brown1': (255, 64, 64, 255)
'brown2': (238, 59, 59, 255)
'brown3': (205, 51, 51, 255)
'brown4': (139, 35, 35, 255)
'burlywood': (222, 184, 135, 255)
'burlywood1': (255, 211, 155, 255)
'burlywood2': (238, 197, 145, 255)
'burlywood3': (205, 170, 125, 255)
'burlywood4': (139, 115, 85, 255)
'cadetblue': (95, 158, 160, 255)
'cadetblue1': (152, 245, 255, 255)
'cadetblue2': (142, 229, 238, 255)
'cadetblue3': (122, 197, 205, 255)
'cadetblue4': (83, 134, 139, 255)
'chartreuse': (127, 255, 0, 255)
'chartreuse1': (127, 255, 0, 255)
'chartreuse2': (118, 238, 0, 255)
'chartreuse3': (102, 205, 0, 255)
'chartreuse4': (69, 139, 0, 255)
'chocolate': (210, 105, 30, 255)
'chocolate1': (255, 127, 36, 255)
'chocolate2': (238, 118, 33, 255)
'chocolate3': (205, 102, 29, 255)
'chocolate4': (139, 69, 19, 255)
'coral': (255, 127, 80, 255)
'coral1': (255, 114, 86, 255)
'coral2': (238, 106, 80, 255)
'coral3': (205, 91, 69, 255)
'coral4': (139, 62, 47, 255)
'cornflowerblue': (100, 149, 237, 255)
'cornsilk': (255, 248, 220, 255)
'cornsilk1': (255, 248, 220, 255)
'cornsilk2': (238, 232, 205, 255)
'cornsilk3': (205, 200, 177, 255)
'cornsilk4': (139, 136, 120, 255)
'cyan': (0, 255, 255, 255)
'cyan1': (0, 255, 255, 255)
'cyan2': (0, 238, 238, 255)
'cyan3': (0, 205, 205, 255)
'cyan4': (0, 139, 139, 255)
'darkblue': (0, 0, 139, 255)
'darkcyan': (0, 139, 139, 255)
'darkgoldenrod': (184, 134, 11, 255)
'darkgoldenrod1': (255, 185, 15, 255)
'darkgoldenrod2': (238, 173, 14, 255)
'darkgoldenrod3': (205, 149, 12, 255)
'darkgoldenrod4': (139, 101, 8, 255)
'darkgray': (169, 169, 169, 255)
'darkgreen': (0, 100, 0, 255)
'darkgrey': (169, 169, 169, 255)
'darkkhaki': (189, 183, 107, 255)
'darkmagenta': (139, 0, 139, 255)
'darkolivegreen': (85, 107, 47, 255)
'darkolivegreen1': (202, 255, 112, 255)
'darkolivegreen2': (188, 238, 104, 255)
'darkolivegreen3': (162, 205, 90, 255)
'darkolivegreen4': (110, 139, 61, 255)
'darkorange': (255, 140, 0, 255)
'darkorange1': (255, 127, 0, 255)
'darkorange2': (238, 118, 0, 255)
'darkorange3': (205, 102, 0, 255)
'darkorange4': (139, 69, 0, 255)
'darkorchid': (153, 50, 204, 255)
'darkorchid1': (191, 62, 255, 255)
'darkorchid2': (178, 58, 238, 255)
'darkorchid3': (154, 50, 205, 255)
'darkorchid4': (104, 34, 139, 255)
'darkred': (139, 0, 0, 255)
'darksalmon': (233, 150, 122, 255)
'darkseagreen': (143, 188, 143, 255)
'darkseagreen1': (193, 255, 193, 255)
'darkseagreen2': (180, 238, 180, 255)
'darkseagreen3': (155, 205, 155, 255)
'darkseagreen4': (105, 139, 105, 255)
'darkslateblue': (72, 61, 139, 255)
'darkslategray': (47, 79, 79, 255)
'darkslategray1': (151, 255, 255, 255)
'darkslategray2': (141, 238, 238, 255)
'darkslategray3': (121, 205, 205, 255)
'darkslategray4': (82, 139, 139, 255)
'darkslategrey': (47, 79, 79, 255)
'darkturquoise': (0, 206, 209, 255)
'darkviolet': (148, 0, 211, 255)
'deeppink': (255, 20, 147, 255)
'deeppink1': (255, 20, 147, 255)
'deeppink2': (238, 18, 137, 255)
'deeppink3': (205, 16, 118, 255)
'deeppink4': (139, 10, 80, 255)
'deepskyblue': (0, 191, 255, 255)
'deepskyblue1': (0, 191, 255, 255)
'deepskyblue2': (0, 178, 238, 255)
'deepskyblue3': (0, 154, 205, 255)
'deepskyblue4': (0, 104, 139, 255)
'dimgray': (105, 105, 105, 255)
'dimgrey': (105, 105, 105, 255)
'dodgerblue': (30, 144, 255, 255)
'dodgerblue1': (30, 144, 255, 255)
'dodgerblue2': (28, 134, 238, 255)
'dodgerblue3': (24, 116, 205, 255)
'dodgerblue4': (16, 78, 139, 255)
'firebrick': (178, 34, 34, 255)
'firebrick1': (255, 48, 48, 255)
'firebrick2': (238, 44, 44, 255)
'firebrick3': (205, 38, 38, 255)
'firebrick4': (139, 26, 26, 255)
'floralwhite': (255, 250, 240, 255)
'forestgreen': (34, 139, 34, 255)
'gainsboro': (220, 220, 220, 255)
'ghostwhite': (248, 248, 255, 255)
'gold': (255, 215, 0, 255)
'gold1': (255, 215, 0, 255)
'gold2': (238, 201, 0, 255)
'gold3': (205, 173, 0, 255)
'gold4': (139, 117, 0, 255)
'goldenrod': (218, 165, 32, 255)
'goldenrod1': (255, 193, 37, 255)
'goldenrod2': (238, 180, 34, 255)
'goldenrod3': (205, 155, 29, 255)
'goldenrod4': (139, 105, 20, 255)
'gray': (190, 190, 190, 255)
'gray0': (0, 0, 0, 255)
'gray1': (3, 3, 3, 255)
'gray2': (5, 5, 5, 255)
'gray3': (8, 8, 8, 255)
'gray4': (10, 10, 10, 255)
'gray5': (13, 13, 13, 255)
'gray6': (15, 15, 15, 255)
'gray7': (18, 18, 18, 255)
'gray8': (20, 20, 20, 255)
'gray9': (23, 23, 23, 255)
'gray10': (26, 26, 26, 255)
'gray11': (28, 28, 28, 255)
'gray12': (31, 31, 31, 255)
'gray13': (33, 33, 33, 255)
'gray14': (36, 36, 36, 255)
'gray15': (38, 38, 38, 255)
'gray16': (41, 41, 41, 255)
'gray17': (43, 43, 43, 255)
'gray18': (46, 46, 46, 255)
'gray19': (48, 48, 48, 255)
'gray20': (51, 51, 51, 255)
'gray21': (54, 54, 54, 255)
'gray22': (56, 56, 56, 255)
'gray23': (59, 59, 59, 255)
'gray24': (61, 61, 61, 255)
'gray25': (64, 64, 64, 255)
'gray26': (66, 66, 66, 255)
'gray27': (69, 69, 69, 255)
'gray28': (71, 71, 71, 255)
'gray29': (74, 74, 74, 255)
'gray30': (77, 77, 77, 255)
'gray31': (79, 79, 79, 255)
'gray32': (82, 82, 82, 255)
'gray33': (84, 84, 84, 255)
'gray34': (87, 87, 87, 255)
'gray35': (89, 89, 89, 255)
'gray36': (92, 92, 92, 255)
'gray37': (94, 94, 94, 255)
'gray38': (97, 97, 97, 255)
'gray39': (99, 99, 99, 255)
'gray40': (102, 102, 102, 255)
'gray41': (105, 105, 105, 255)
'gray42': (107, 107, 107, 255)
'gray43': (110, 110, 110, 255)
'gray44': (112, 112, 112, 255)
'gray45': (115, 115, 115, 255)
'gray46': (117, 117, 117, 255)
'gray47': (120, 120, 120, 255)
'gray48': (122, 122, 122, 255)
'gray49': (125, 125, 125, 255)
'gray50': (127, 127, 127, 255)
'gray51': (130, 130, 130, 255)
'gray52': (133, 133, 133, 255)
'gray53': (135, 135, 135, 255)
'gray54': (138, 138, 138, 255)
'gray55': (140, 140, 140, 255)
'gray56': (143, 143, 143, 255)
'gray57': (145, 145, 145, 255)
'gray58': (148, 148, 148, 255)
'gray59': (150, 150, 150, 255)
'gray60': (153, 153, 153, 255)
'gray61': (156, 156, 156, 255)
'gray62': (158, 158, 158, 255)
'gray63': (161, 161, 161, 255)
'gray64': (163, 163, 163, 255)
'gray65': (166, 166, 166, 255)
'gray66': (168, 168, 168, 255)
'gray67': (171, 171, 171, 255)
'gray68': (173, 173, 173, 255)
'gray69': (176, 176, 176, 255)
'gray70': (179, 179, 179, 255)
'gray71': (181, 181, 181, 255)
'gray72': (184, 184, 184, 255)
'gray73': (186, 186, 186, 255)
'gray74': (189, 189, 189, 255)
'gray75': (191, 191, 191, 255)
'gray76': (194, 194, 194, 255)
'gray77': (196, 196, 196, 255)
'gray78': (199, 199, 199, 255)
'gray79': (201, 201, 201, 255)
'gray80': (204, 204, 204, 255)
'gray81': (207, 207, 207, 255)
'gray82': (209, 209, 209, 255)
'gray83': (212, 212, 212, 255)
'gray84': (214, 214, 214, 255)
'gray85': (217, 217, 217, 255)
'gray86': (219, 219, 219, 255)
'gray87': (222, 222, 222, 255)
'gray88': (224, 224, 224, 255)
'gray89': (227, 227, 227, 255)
'gray90': (229, 229, 229, 255)
'gray91': (232, 232, 232, 255)
'gray92': (235, 235, 235, 255)
'gray93': (237, 237, 237, 255)
'gray94': (240, 240, 240, 255)
'gray95': (242, 242, 242, 255)
'gray96': (245, 245, 245, 255)
'gray97': (247, 247, 247, 255)
'gray98': (250, 250, 250, 255)
'gray99': (252, 252, 252, 255)
'gray100': (255, 255, 255, 255)
'green': (0, 255, 0, 255)
'green1': (0, 255, 0, 255)
'green2': (0, 238, 0, 255)
'green3': (0, 205, 0, 255)
'green4': (0, 139, 0, 255)
'greenyellow': (173, 255, 47, 255)
'grey': (190, 190, 190, 255)
'grey0': (0, 0, 0, 255)
'grey1': (3, 3, 3, 255)
'grey2': (5, 5, 5, 255)
'grey3': (8, 8, 8, 255)
'grey4': (10, 10, 10, 255)
'grey5': (13, 13, 13, 255)
'grey6': (15, 15, 15, 255)
'grey7': (18, 18, 18, 255)
'grey8': (20, 20, 20, 255)
'grey9': (23, 23, 23, 255)
'grey10': (26, 26, 26, 255)
'grey11': (28, 28, 28, 255)
'grey12': (31, 31, 31, 255)
'grey13': (33, 33, 33, 255)
'grey14': (36, 36, 36, 255)
'grey15': (38, 38, 38, 255)
'grey16': (41, 41, 41, 255)
'grey17': (43, 43, 43, 255)
'grey18': (46, 46, 46, 255)
'grey19': (48, 48, 48, 255)
'grey20': (51, 51, 51, 255)
'grey21': (54, 54, 54, 255)
'grey22': (56, 56, 56, 255)
'grey23': (59, 59, 59, 255)
'grey24': (61, 61, 61, 255)
'grey25': (64, 64, 64, 255)
'grey26': (66, 66, 66, 255)
'grey27': (69, 69, 69, 255)
'grey28': (71, 71, 71, 255)
'grey29': (74, 74, 74, 255)
'grey30': (77, 77, 77, 255)
'grey31': (79, 79, 79, 255)
'grey32': (82, 82, 82, 255)
'grey33': (84, 84, 84, 255)
'grey34': (87, 87, 87, 255)
'grey35': (89, 89, 89, 255)
'grey36': (92, 92, 92, 255)
'grey37': (94, 94, 94, 255)
'grey38': (97, 97, 97, 255)
'grey39': (99, 99, 99, 255)
'grey40': (102, 102, 102, 255)
'grey41': (105, 105, 105, 255)
'grey42': (107, 107, 107, 255)
'grey43': (110, 110, 110, 255)
'grey44': (112, 112, 112, 255)
'grey45': (115, 115, 115, 255)
'grey46': (117, 117, 117, 255)
'grey47': (120, 120, 120, 255)
'grey48': (122, 122, 122, 255)
'grey49': (125, 125, 125, 255)
'grey50': (127, 127, 127, 255)
'grey51': (130, 130, 130, 255)
'grey52': (133, 133, 133, 255)
'grey53': (135, 135, 135, 255)
'grey54': (138, 138, 138, 255)
'grey55': (140, 140, 140, 255)
'grey56': (143, 143, 143, 255)
'grey57': (145, 145, 145, 255)
'grey58': (148, 148, 148, 255)
'grey59': (150, 150, 150, 255)
'grey60': (153, 153, 153, 255)
'grey61': (156, 156, 156, 255)
'grey62': (158, 158, 158, 255)
'grey63': (161, 161, 161, 255)
'grey64': (163, 163, 163, 255)
'grey65': (166, 166, 166, 255)
'grey66': (168, 168, 168, 255)
'grey67': (171, 171, 171, 255)
'grey68': (173, 173, 173, 255)
'grey69': (176, 176, 176, 255)
'grey70': (179, 179, 179, 255)
'grey71': (181, 181, 181, 255)
'grey72': (184, 184, 184, 255)
'grey73': (186, 186, 186, 255)
'grey74': (189, 189, 189, 255)
'grey75': (191, 191, 191, 255)
'grey76': (194, 194, 194, 255)
'grey77': (196, 196, 196, 255)
'grey78': (199, 199, 199, 255)
'grey79': (201, 201, 201, 255)
'grey80': (204, 204, 204, 255)
'grey81': (207, 207, 207, 255)
'grey82': (209, 209, 209, 255)
'grey83': (212, 212, 212, 255)
'grey84': (214, 214, 214, 255)
'grey85': (217, 217, 217, 255)
'grey86': (219, 219, 219, 255)
'grey87': (222, 222, 222, 255)
'grey88': (224, 224, 224, 255)
'grey89': (227, 227, 227, 255)
'grey90': (229, 229, 229, 255)
'grey91': (232, 232, 232, 255)
'grey92': (235, 235, 235, 255)
'grey93': (237, 237, 237, 255)
'grey94': (240, 240, 240, 255)
'grey95': (242, 242, 242, 255)
'grey96': (245, 245, 245, 255)
'grey97': (247, 247, 247, 255)
'grey98': (250, 250, 250, 255)
'grey99': (252, 252, 252, 255)
'grey100': (255, 255, 255, 255)
'honeydew': (240, 255, 240, 255)
'honeydew1': (240, 255, 240, 255)
'honeydew2': (224, 238, 224, 255)
'honeydew3': (193, 205, 193, 255)
'honeydew4': (131, 139, 131, 255)
'hotpink': (255, 105, 180, 255)
'hotpink1': (255, 110, 180, 255)
'hotpink2': (238, 106, 167, 255)
'hotpink3': (205, 96, 144, 255)
'hotpink4': (139, 58, 98, 255)
'indianred': (205, 92, 92, 255)
'indianred1': (255, 106, 106, 255)
'indianred2': (238, 99, 99, 255)
'indianred3': (205, 85, 85, 255)
'indianred4': (139, 58, 58, 255)
'ivory': (255, 255, 240, 255)
'ivory1': (255, 255, 240, 255)
'ivory2': (238, 238, 224, 255)
'ivory3': (205, 205, 193, 255)
'ivory4': (139, 139, 131, 255)
'khaki': (240, 230, 140, 255)
'khaki1': (255, 246, 143, 255)
'khaki2': (238, 230, 133, 255)
'khaki3': (205, 198, 115, 255)
'khaki4': (139, 134, 78, 255)
'lavender': (230, 230, 250, 255)
'lavenderblush': (255, 240, 245, 255)
'lavenderblush1': (255, 240, 245, 255)
'lavenderblush2': (238, 224, 229, 255)
'lavenderblush3': (205, 193, 197, 255)
'lavenderblush4': (139, 131, 134, 255)
'lawngreen': (124, 252, 0, 255)
'lemonchiffon': (255, 250, 205, 255)
'lemonchiffon1': (255, 250, 205, 255)
'lemonchiffon2': (238, 233, 191, 255)
'lemonchiffon3': (205, 201, 165, 255)
'lemonchiffon4': (139, 137, 112, 255)
'lightblue': (173, 216, 230, 255)
'lightblue1': (191, 239, 255, 255)
'lightblue2': (178, 223, 238, 255)
'lightblue3': (154, 192, 205, 255)
'lightblue4': (104, 131, 139, 255)
'lightcoral': (240, 128, 128, 255)
'lightcyan': (224, 255, 255, 255)
'lightcyan1': (224, 255, 255, 255)
'lightcyan2': (209, 238, 238, 255)
'lightcyan3': (180, 205, 205, 255)
'lightcyan4': (122, 139, 139, 255)
'lightgoldenrod': (238, 221, 130, 255)
'lightgoldenrod1': (255, 236, 139, 255)
'lightgoldenrod2': (238, 220, 130, 255)
'lightgoldenrod3': (205, 190, 112, 255)
'lightgoldenrod4': (139, 129, 76, 255)
'lightgoldenrodyellow': (250, 250, 210, 255)
'lightgray': (211, 211, 211, 255)
'lightgreen': (144, 238, 144, 255)
'lightgrey': (211, 211, 211, 255)
'lightpink': (255, 182, 193, 255)
'lightpink1': (255, 174, 185, 255)
'lightpink2': (238, 162, 173, 255)
'lightpink3': (205, 140, 149, 255)
'lightpink4': (139, 95, 101, 255)
'lightsalmon': (255, 160, 122, 255)
'lightsalmon1': (255, 160, 122, 255)
'lightsalmon2': (238, 149, 114, 255)
'lightsalmon3': (205, 129, 98, 255)
'lightsalmon4': (139, 87, 66, 255)
'lightseagreen': (32, 178, 170, 255)
'lightskyblue': (135, 206, 250, 255)
'lightskyblue1': (176, 226, 255, 255)
'lightskyblue2': (164, 211, 238, 255)
'lightskyblue3': (141, 182, 205, 255)
'lightskyblue4': (96, 123, 139, 255)
'lightslateblue': (132, 112, 255, 255)
'lightslategray': (119, 136, 153, 255)
'lightslategrey': (119, 136, 153, 255)
'lightsteelblue': (176, 196, 222, 255)
'lightsteelblue1': (202, 225, 255, 255)
'lightsteelblue2': (188, 210, 238, 255)
'lightsteelblue3': (162, 181, 205, 255)
'lightsteelblue4': (110, 123, 139, 255)
'lightyellow': (255, 255, 224, 255)
'lightyellow1': (255, 255, 224, 255)
'lightyellow2': (238, 238, 209, 255)
'lightyellow3': (205, 205, 180, 255)
'lightyellow4': (139, 139, 122, 255)
'linen': (250, 240, 230, 255)
'limegreen': (50, 205, 50, 255)
'magenta': (255, 0, 255, 255)
'magenta1': (255, 0, 255, 255)
'magenta2': (238, 0, 238, 255)
'magenta3': (205, 0, 205, 255)
'magenta4': (139, 0, 139, 255)
'maroon': (176, 48, 96, 255)
'maroon1': (255, 52, 179, 255)
'maroon2': (238, 48, 167, 255)
'maroon3': (205, 41, 144, 255)
'maroon4': (139, 28, 98, 255)
'mediumaquamarine': (102, 205, 170, 255)
'mediumblue': (0, 0, 205, 255)
'mediumorchid': (186, 85, 211, 255)
'mediumorchid1': (224, 102, 255, 255)
'mediumorchid2': (209, 95, 238, 255)
'mediumorchid3': (180, 82, 205, 255)
'mediumorchid4': (122, 55, 139, 255)
'mediumpurple': (147, 112, 219, 255)
'mediumpurple1': (171, 130, 255, 255)
'mediumpurple2': (159, 121, 238, 255)
'mediumpurple3': (137, 104, 205, 255)
'mediumpurple4': (93, 71, 139, 255)
'mediumseagreen': (60, 179, 113, 255)
'mediumslateblue': (123, 104, 238, 255)
'mediumspringgreen': (0, 250, 154, 255)
'mediumturquoise': (72, 209, 204, 255)
'mediumvioletred': (199, 21, 133, 255)
'midnightblue': (25, 25, 112, 255)
'mintcream': (245, 255, 250, 255)
'mistyrose': (255, 228, 225, 255)
'mistyrose1': (255, 228, 225, 255)
'mistyrose2': (238, 213, 210, 255)
'mistyrose3': (205, 183, 181, 255)
'mistyrose4': (139, 125, 123, 255)
'moccasin': (255, 228, 181, 255)
'navajowhite': (255, 222, 173, 255)
'navajowhite1': (255, 222, 173, 255)
'navajowhite2': (238, 207, 161, 255)
'navajowhite3': (205, 179, 139, 255)
'navajowhite4': (139, 121, 94, 255)
'navy': (0, 0, 128, 255)
'navyblue': (0, 0, 128, 255)
'oldlace': (253, 245, 230, 255)
'olivedrab': (107, 142, 35, 255)
'olivedrab1': (192, 255, 62, 255)
'olivedrab2': (179, 238, 58, 255)
'olivedrab3': (154, 205, 50, 255)
'olivedrab4': (105, 139, 34, 255)
'orange': (255, 165, 0, 255)
'orange1': (255, 165, 0, 255)
'orange2': (238, 154, 0, 255)
'orange3': (205, 133, 0, 255)
'orange4': (139, 90, 0, 255)
'orangered': (255, 69, 0, 255)
'orangered1': (255, 69, 0, 255)
'orangered2': (238, 64, 0, 255)
'orangered3': (205, 55, 0, 255)
'orangered4': (139, 37, 0, 255)
'orchid': (218, 112, 214, 255)
'orchid1': (255, 131, 250, 255)
'orchid2': (238, 122, 233, 255)
'orchid3': (205, 105, 201, 255)
'orchid4': (139, 71, 137, 255)
'palegreen': (152, 251, 152, 255)
'palegreen1': (154, 255, 154, 255)
'palegreen2': (144, 238, 144, 255)
'palegreen3': (124, 205, 124, 255)
'palegreen4': (84, 139, 84, 255)
'palegoldenrod': (238, 232, 170, 255)
'paleturquoise': (175, 238, 238, 255)
'paleturquoise1': (187, 255, 255, 255)
'paleturquoise2': (174, 238, 238, 255)
'paleturquoise3': (150, 205, 205, 255)
'paleturquoise4': (102, 139, 139, 255)
'palevioletred': (219, 112, 147, 255)
'palevioletred1': (255, 130, 171, 255)
'palevioletred2': (238, 121, 159, 255)
'palevioletred3': (205, 104, 137, 255)
'palevioletred4': (139, 71, 93, 255)
'papayawhip': (255, 239, 213, 255)
'peachpuff': (255, 218, 185, 255)
'peachpuff1': (255, 218, 185, 255)
'peachpuff2': (238, 203, 173, 255)
'peachpuff3': (205, 175, 149, 255)
'peachpuff4': (139, 119, 101, 255)
'peru': (205, 133, 63, 255)
'pink': (255, 192, 203, 255)
'pink1': (255, 181, 197, 255)
'pink2': (238, 169, 184, 255)
'pink3': (205, 145, 158, 255)
'pink4': (139, 99, 108, 255)
'plum': (221, 160, 221, 255)
'plum1': (255, 187, 255, 255)
'plum2': (238, 174, 238, 255)
'plum3': (205, 150, 205, 255)
'plum4': (139, 102, 139, 255)
'powderblue': (176, 224, 230, 255)
'purple': (160, 32, 240, 255)
'purple1': (155, 48, 255, 255)
'purple2': (145, 44, 238, 255)
'purple3': (125, 38, 205, 255)
'purple4': (85, 26, 139, 255)
'red': (255, 0, 0, 255)
'red1': (255, 0, 0, 255)
'red2': (238, 0, 0, 255)
'red3': (205, 0, 0, 255)
'red4': (139, 0, 0, 255)
'rosybrown': (188, 143, 143, 255)
'rosybrown1': (255, 193, 193, 255)
'rosybrown2': (238, 180, 180, 255)
'rosybrown3': (205, 155, 155, 255)
'rosybrown4': (139, 105, 105, 255)
'royalblue': (65, 105, 225, 255)
'royalblue1': (72, 118, 255, 255)
'royalblue2': (67, 110, 238, 255)
'royalblue3': (58, 95, 205, 255)
'royalblue4': (39, 64, 139, 255)
'salmon': (250, 128, 114, 255)
'salmon1': (255, 140, 105, 255)
'salmon2': (238, 130, 98, 255)
'salmon3': (205, 112, 84, 255)
'salmon4': (139, 76, 57, 255)
'saddlebrown': (139, 69, 19, 255)
'sandybrown': (244, 164, 96, 255)
'seagreen': (46, 139, 87, 255)
'seagreen1': (84, 255, 159, 255)
'seagreen2': (78, 238, 148, 255)
'seagreen3': (67, 205, 128, 255)
'seagreen4': (46, 139, 87, 255)
'seashell': (255, 245, 238, 255)
'seashell1': (255, 245, 238, 255)
'seashell2': (238, 229, 222, 255)
'seashell3': (205, 197, 191, 255)
'seashell4': (139, 134, 130, 255)
'sienna': (160, 82, 45, 255)
'sienna1': (255, 130, 71, 255)
'sienna2': (238, 121, 66, 255)
'sienna3': (205, 104, 57, 255)
'sienna4': (139, 71, 38, 255)
'skyblue': (135, 206, 235, 255)
'skyblue1': (135, 206, 255, 255)
'skyblue2': (126, 192, 238, 255)
'skyblue3': (108, 166, 205, 255)
'skyblue4': (74, 112, 139, 255)
'slateblue': (106, 90, 205, 255)
'slateblue1': (131, 111, 255, 255)
'slateblue2': (122, 103, 238, 255)
'slateblue3': (105, 89, 205, 255)
'slateblue4': (71, 60, 139, 255)
'slategray': (112, 128, 144, 255)
'slategray1': (198, 226, 255, 255)
'slategray2': (185, 211, 238, 255)
'slategray3': (159, 182, 205, 255)
'slategray4': (108, 123, 139, 255)
'slategrey': (112, 128, 144, 255)
'snow': (255, 250, 250, 255)
'snow1': (255, 250, 250, 255)
'snow2': (238, 233, 233, 255)
'snow3': (205, 201, 201, 255)
'snow4': (139, 137, 137, 255)
'springgreen': (0, 255, 127, 255)
'springgreen1': (0, 255, 127, 255)
'springgreen2': (0, 238, 118, 255)
'springgreen3': (0, 205, 102, 255)
'springgreen4': (0, 139, 69, 255)
'steelblue': (70, 130, 180, 255)
'steelblue1': (99, 184, 255, 255)
'steelblue2': (92, 172, 238, 255)
'steelblue3': (79, 148, 205, 255)
'steelblue4': (54, 100, 139, 255)
'tan': (210, 180, 140, 255)
'tan1': (255, 165, 79, 255)
'tan2': (238, 154, 73, 255)
'tan3': (205, 133, 63, 255)
'tan4': (139, 90, 43, 255)
'thistle': (216, 191, 216, 255)
'thistle1': (255, 225, 255, 255)
'thistle2': (238, 210, 238, 255)
'thistle3': (205, 181, 205, 255)
'thistle4': (139, 123, 139, 255)
'tomato': (255, 99, 71, 255)
'tomato1': (255, 99, 71, 255)
'tomato2': (238, 92, 66, 255)
'tomato3': (205, 79, 57, 255)
'tomato4': (139, 54, 38, 255)
'turquoise': (64, 224, 208, 255)
'turquoise1': (0, 245, 255, 255)
'turquoise2': (0, 229, 238, 255)
'turquoise3': (0, 197, 205, 255)
'turquoise4': (0, 134, 139, 255)
'violet': (238, 130, 238, 255)
'violetred': (208, 32, 144, 255)
'violetred1': (255, 62, 150, 255)
'violetred2': (238, 58, 140, 255)
'violetred3': (205, 50, 120, 255)
'violetred4': (139, 34, 82, 255)
'wheat': (245, 222, 179, 255)
'wheat1': (255, 231, 186, 255)
'wheat2': (238, 216, 174, 255)
'wheat3': (205, 186, 150, 255)
'wheat4': (139, 126, 102, 255)
'white': (255, 255, 255, 255)
'whitesmoke': (245, 245, 245, 255)
'yellow': (255, 255, 0, 255)
'yellow1': (255, 255, 0, 255)
'yellow2': (238, 238, 0, 255)
'yellow3': (205, 205, 0, 255)
'yellow4': (139, 139, 0, 255)
'yellowgreen': (154, 205, 50, 255)
```

Créez une couleur en utilisant le constructeur de la classe `pygame.Color` en lui passant une chaine de caractères correspondant à une constante prédéfinie.

```python
RED_COLOR = pygame.Color('red')
```

Ou passez un tuple de trois valeurs RGB (comprises entre `0` et `255`).

```python
RED_COLOR = pygame.Color((255, 0, 0))
```

**Remarque :** Depuis la version 2 de pygame, vous pouvez faire encore plus simple. Partout où une couleur est attendue, vous pouvez utiliser directement une des chaînes prédéfinies sans instancier d'objet `Color`.

```python
surface.fill('yellow') # au lieu de surface.fill(pygame.Color('yellow'))
```

## Remplir la surface d'affichage avec une couleur

Utilisez la méthode `fill` avec la couleur de votre choix.

```python
display_surface.fill('black')
```

**Remarque :** Cette méthode peut s'appliquer à toute surface et pas uniquement à la surface d'affichage. Si vous souhaitez créer une surface remplie d'une certaine couleur, utilisez cette méthode.

```python
yellow_square = pygame.Surface((16, 16))
yellow_square.fill('yellow')
```

## Rafraîchir l'affichage

Pour éviter des bugs d'affichage, vous devez rafraichir la surface d'affichage à chaque boucle de jeu. Utilisez la fonction `flip` du sous-module `display` sans arguments pour mettre à jour intégralement la surface d'affichage.

```python
pygame.display.flip()
```

**Remarque :** Techniquement, la fonction `flip` inverse la surface d'affichage d'arrière plan et celle d'avant plan. On travaille sur deux surfaces pour éviter de dessiner directement sur la surface d'affichage à l'écran ce qui pourrait provoquer des affichages de formes incomplètes. Ainsi, on dessine sur un tampon d'arrière plan et une fois terminé, on bascule les deux surfaces. On appelle cette technique, le _double buffering_.

pygame fournit également la fonction `update` qui vous permet de rafraichir intégralement la surface d'affichage si vous ne passez pas d'argument (équivalent à la méthode `flip`) mais qui vous permet surtout de rafraichir seulement certaines zones de la surface d'affichage si vous passez un objet de type `Rect` ou une liste de ces objets. En principe, cette méthode permet d'améliorer la performance car on ne "rafraichit" que les zones ayant changé et pas toute la surface d'affichage.

```python
pygame.display.update(rectangles_list)
```

**Remarque :** Si besoin, pensez à remplir la surface d'affichage avec une couleur pour _effacer_ son contenu précédent avant de dessiner sur la surface d'affichage et enfin d'appeler la fonction `flip`.

```python
display_surface.fill('black')
# instructions de dessin
pygame.display.flip()
```

## Créer une boucle de jeu

Créez simplement une boucle `while` avec un booléen initialisé à `True` et que vous passerez à `False` lorsque vous souhaiterez quitter le programme.

```python
running = True

while running:
    if end_game:
        running = False
```

**Attention !** Vous devez ajouter la gestion de l'évènement de fermeture pour que votre jeu se termine correctement. Cet évènement est déclenché lorsque l'utilisateur clique sur le bouton de fermeture de la fenêtre ou appuie sur les touches `ALT + F4`.

## Limiter le taux de rafraichissement

Créez une instance de la classe `pygame.time.Clock` et appelez sa méthode `tick` pour obtenir le délai (en millisecondes) depuis le dernier appel de cette méthode et forcer une pause si le taux de rafraichissement dépasse le paramètre passé à cette méthode.

```python
clock = pygame.time.Clock()
...

while running:
    ...
    delta_time = clock.tick(60) / 1000
    FPS = 1 / delta_time
```

## Gérer les évènements

La fonction `get` du sous-module `event` renvoie la liste des évènements non traités. Parcourez cette liste pour traiter individuellement chaque évènement.

```python
for event in pygame.event.get():
    # traitement des évènements
```

### Types d'évènements

Chaque évènement possède un attribut `type` qui vous permet de déterminer quel genre d'évènement s'est déclenché.

- `pygame.QUIT` : se déclenche lorsque l'utilisateur clique sur le bouton de fermeture de la fenêtre ou appuie sur `ALT + F4`. Cet évènement ne possède pas d'autre attribut.
- `pygame.ACTIVEEVENT` : se déclenche lorsque l'utilisateur ???. Cet évènement possède également les attributs `gain` et `state`.
- `pygame.KEYDOWN` : se déclenche lorsque l'utilisateur enfonce une touche du clavier. Cet évènement possède également les attributs `key`, `mod`, `unicode` et `scancode`.
- `pygame.KEYUP` : se déclenche lorsque l'utilisateur relâche une touche du clavier. Cet évènement possède également les attributs `key` et `mod`.
- `pygame.MOUSEMOTION` : se déclenche lorsque l'utilisateur déplace la souris. Cet évènement possède également les attributs `pos`, `rel` et `buttons`.
- `pygame.MOUSEBUTTONUP` : se déclenche lorsque l'utilisateur relâche un bouton de souris. Cet évènement possède également les attributs `pos` et `button`.
- `pygame.MOUSEBUTTONDOWN` : se déclenche lorsque l'utilisateur enfonce un bouton de souris. Cet évènement possède également les attributs `pos` et `button`.
- `pygame.JOYAXISMOTION` : se déclenche lorsque l'utilisateur pousse un stick analogique de manette. Cet évènement possède également les attributs `instance_id`, `axis` et `value`.
- `pygame.JOYBALLMOTION` : se déclenche lorsque l'utilisateur ???. Cet évènement possède également les attributs `instance_id`, `ball` et `rel`.
- `pygame.JOYHATMOTION` : se déclenche lorsque l'utilisateur ???. Cet évènement possède également les attributs `instance_id`, `hat` et `value`.
- `pygame.JOYBUTTONUP` : se déclenche lorsque l'utilisateur relâche un bouton de manette. Cet évènement possède également les attributs `instance_id` et `button`.
- `pygame.JOYBUTTONDOWN` : se déclenche lorsque l'utilisateur enfonce un bouton de manette. Cet évènement possède également les attributs `instance_id` et `button`.
- `pygame.VIDEORESIZE` : se déclenche lorsque l'utilisateur change la taille de la fenêtre. Utile pour adapter le contenu à afficher à la taille de la fenêtre.Cet évènement possède également les attributs `size`, `w` et `h`.
- `pygame.VIDEOEXPOSE` : se déclenche lorsque l'utilisateur ???. Cet évènement ne possède pas d'autre attribut.
- `pygame.USEREVENT` : se déclenche lorsque l'utilisateur ???. Cet évènement possède également l'attribut `code`.

### Evènement de fermeture de fenêtre

Lorsque l'utilisateur clique sur le bouton de fermeture de la fenêtre ou appuie sur les touches `ALT + F4` un évènement de type `pygame.QUIT` est déclenché. Utilisez ce type pour stopper la boucle de jeu.

```python
if event.type == pygame.QUIT:
    running = False
```

### Evènement de touches de clavier

Deux types d'évènements peuvent se produire avec les touches du clavier :

- L'évènement de type `pygame.KEYDOWN` se déclenche lorsque l'utilisateur enfonce une touche.
- L'évènement de type `pygame.KEYUP` se déclenche lorsque l'utilisateur relâche une touche enfoncée précédemment.

La propriété `key` de l'évènement permet de déterminer quelle touche vient d'être enfoncée ou relâchée. Consultez la section sur les constantes associées au touches du clavier pour une liste complète.

```python
if event.type == pygame.KEYDOWN:
    if event.key == K_SPACE:
        print('La touche espace vient juste d''être enfoncée.')
```

## Contrôles

La méthode `get_pressed` du module `pygame.key` renvoie une liste d'état des touches du clavier. Utilisez une constante associée à une touche du clavier en tant que clé pour savoir si une touche est enfoncée ou non.

```python
keys_pressed = pygame.key.get_pressed()

if keys_pressed[pygame.K_SPACE]:
    print('La touche espace est actuellement enfoncée.')
else:
    print('La touche espace est actuellement relâchée.')
```

### Constantes associées aux touches du clavier

Voici les constantes associées aux touches du clavier :

```
K_BACKSPACE   \b      backspace
K_TAB         \t      tab
K_CLEAR               clear
K_RETURN      \r      return
K_PAUSE               pause
K_ESCAPE      ^[      escape
K_SPACE               space
K_EXCLAIM     !       exclaim
K_QUOTEDBL    "       quotedbl
K_HASH        #       hash
K_DOLLAR      $       dollar
K_AMPERSAND   &       ampersand
K_QUOTE               quote
K_LEFTPAREN   (       left parenthesis
K_RIGHTPAREN  )       right parenthesis
K_ASTERISK    *       asterisk
K_PLUS        +       plus sign
K_COMMA       ,       comma
K_MINUS       -       minus sign
K_PERIOD      .       period
K_SLASH       /       forward slash
K_0           0       0
K_1           1       1
K_2           2       2
K_3           3       3
K_4           4       4
K_5           5       5
K_6           6       6
K_7           7       7
K_8           8       8
K_9           9       9
K_COLON       :       colon
K_SEMICOLON   ;       semicolon
K_LESS        <       less-than sign
K_EQUALS      =       equals sign
K_GREATER     >       greater-than sign
K_QUESTION    ?       question mark
K_AT          @       at
K_LEFTBRACKET [       left bracket
K_BACKSLASH   \       backslash
K_RIGHTBRACKET ]      right bracket
K_CARET       ^       caret
K_UNDERSCORE  _       underscore
K_BACKQUOTE   `       grave
K_a           a       a
K_b           b       b
K_c           c       c
K_d           d       d
K_e           e       e
K_f           f       f
K_g           g       g
K_h           h       h
K_i           i       i
K_j           j       j
K_k           k       k
K_l           l       l
K_m           m       m
K_n           n       n
K_o           o       o
K_p           p       p
K_q           q       q
K_r           r       r
K_s           s       s
K_t           t       t
K_u           u       u
K_v           v       v
K_w           w       w
K_x           x       x
K_y           y       y
K_z           z       z
K_DELETE              delete
K_KP0                 keypad 0
K_KP1                 keypad 1
K_KP2                 keypad 2
K_KP3                 keypad 3
K_KP4                 keypad 4
K_KP5                 keypad 5
K_KP6                 keypad 6
K_KP7                 keypad 7
K_KP8                 keypad 8
K_KP9                 keypad 9
K_KP_PERIOD   .       keypad period
K_KP_DIVIDE   /       keypad divide
K_KP_MULTIPLY *       keypad multiply
K_KP_MINUS    -       keypad minus
K_KP_PLUS     +       keypad plus
K_KP_ENTER    \r      keypad enter
K_KP_EQUALS   =       keypad equals
K_UP                  up arrow
K_DOWN                down arrow
K_RIGHT               right arrow
K_LEFT                left arrow
K_INSERT              insert
K_HOME                home
K_END                 end
K_PAGEUP              page up
K_PAGEDOWN            page down
K_F1                  F1
K_F2                  F2
K_F3                  F3
K_F4                  F4
K_F5                  F5
K_F6                  F6
K_F7                  F7
K_F8                  F8
K_F9                  F9
K_F10                 F10
K_F11                 F11
K_F12                 F12
K_F13                 F13
K_F14                 F14
K_F15                 F15
K_NUMLOCK             numlock
K_CAPSLOCK            capslock
K_SCROLLOCK           scrollock
K_RSHIFT              right shift
K_LSHIFT              left shift
K_RCTRL               right control
K_LCTRL               left control
K_RALT                right alt
K_LALT                left alt
K_RMETA               right meta
K_LMETA               left meta
K_LSUPER              left Windows key
K_RSUPER              right Windows key
K_MODE                mode shift
K_HELP                help
K_PRINT               print screen
K_SYSREQ              sysrq
K_BREAK               break
K_MENU                menu
K_POWER               power
K_EURO                Euro
```

### Accéder à l'état des touches du clavier

pygame fournit la fonction `get_pressed` du sous-module `key` qui renvoie un dictionnaire contenant l'état des touches du clavier. Utilisez une constante représentant un caractère en tant que clé de ce dictionnaire pour accéder à l'état d'une touche spécifique. L'état est soit `True` quand la touche est actuellement enfoncée, soit `False` quand la touche n'est pas actuellement enfoncée.

```python
keys_pressed = pygame.key.get_pressed()
if keys_pressed[pygame.K_LEFT]:
    # instructions si la touche GAUCHE est enfoncée
if keys_pressed[pygame.K_RIGHT]:
    # instructions si la touche DROITE est enfoncée
```

## Gérer la vitesse de rafraichissement de l'affichage

Créez un objet de la classe `Clock` défini dans le sous-module `time`.

```python
clock = pygame.time.Clock()
```

Utilisez ensuite la méthode `tick` pour obtenir le temps passé, en millisecondes, depuis le dernier appel à cette méthode. Passez en paramètre le nombre d'images par seconde attendues. Cette méthode met en pause l'exécution du programme seulement si la boucle de jeu va plus vite que la vitesse attendue.

```pygame
BASE_FPS = 60
delta_time = clock.tick(BASE_FPS) / 1000
```

## Squelette de base

Voici un squelette de base utilisant toutes les fonctionnalités décrites précédemment :

```python
import pygame


pygame.init()

display_size = 1280, 720
display_surface = pygame.display.set_mode(display_size)
pygame.display.set_caption('Titre')

BASE_FPS = 60
clock = pygame.time.Clock()

running = True

while running:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False

    delta_time = self.clock.tick(BASE_FPS) / 1000
    # logique du jeu
    display_surface.fill('black')
    # affichage des éléments du jeu
    pygame.display.flip()

pygame.quit()
```

## Structures utiles

### Vecteurs

pygame définit deux classes pour représenter les vecteurs.

- la classe `Vector2` représente un couple de deux nombres. Utilisez cette classe pour définir les coordonnées d'un point ou un déplacement dans un espace à deux dimensions.
- la classe `Vector3` représente un ensemble de trois nombres. Utilisez cette classe pour définir les coordonnées d'un point ou un déplacement dans un espace à trois dimensions.

#### Vector2

Créez une instance de la classe `Vector2` en passant les coordonnées du point ou du déplacement.

```python
vecteur2 = pygame.Vector2(x, y)
```

**Remarque :** La classe `Vector2` est définie dans le module `pygame.math` mais depuis la version 1.9.4 de pygame vous pouvez l'instancier directement depuis le module `pygame`.

#### Vector3

Créez une instance de la classe `Vector3` en passant les coordonnées du point ou du déplacement.

```python
vecteur3 = pygame.Vector3(x, y, z)
```

**Remarque :** La classe `Vector3` est définie dans le module `pygame.math` mais depuis la version 1.9.4 de pygame vous pouvez l'instancier directement depuis le module `pygame`.

### Rect

pygame définit la classe `Rect` pour représenter un rectangle aligné sur les axes. Cette classe est définie par la position de son coin supérieur gauche et ses dimensions.

Elle possède notamment des méthodes très utiles pour gérer les collisions avec d'autres rectangles.

Créez une instance de la classe `Rect` en passant les coordonnées de son coin supérieur gauche et la largeur et la hauteur du rectangle.

```python
rectangle = pygame.Rect(x, y, largeur, hauteur)
```

La classe `Rect` fournit également des propriétés virtuelles bien pratiques car vous pouvez aussi bien y accéder en lecture qu'en écriture.

Positions :

- `x` ou `left` : position horizontale du bord gauche
- `right` : position horizontale du bord droit
- `y` ou `top` : position verticale du bord supérieur
- `bottom` : position verticale du bord inférieur
- `centerx` : position horizontale du centre du rectangle
- `centery` : position verticale du centre du rectangle
- `topleft` : coordonnées du coin supérieur gauche (x, y)
- `bottomleft` : coordonnées du coin inférieur gauche (x, y)
- `topright` : coordonnées du coin supérieur droit (x, y)
- `bottomright` : coordonnées du coin inférieur droit (x, y)
- `midtop` : coordonnées du milieu du bord supérieur (x, y)
- `midleft` : coordonnées du milieu du bord gauche (x, y)
- `midbottom` : coordonnées du milieu du bord inférieur (x, y)
- `midright` : coordonnées du milieu du bord gauche (x, y)
- `center` : coordonnées du centre du rectangle (x, y)

Dimensions :

- `width` ou `w` : largeur du rectangle
- `height` ou `h` : hauteur du rectangle
- `size` : dimensions du rectangle (largeur, hauteur)

**Remarque :** Seules les propriétés de dimensions modifient les dimensions du rectangle. Les autres propriétés déplacent juste le rectangle.

Pour dupliquer un rectangle, utilisez la méthode `copy`.

```python
rect_copy = rect.copy()
```

Pour déplacer un rectangle depuis sa position actuelle, utilisez la méthode `move` avec les valeurs de déplacement horizontal et vertical.

```python
moved_rect = rect.move(x, y)
```

**Attention !** Cette méthode renvoie un nouveau rectangle déplacé mais le rectangle d'origine n'est pas affecté. Utilisez la méthode `move_ip` pour affecter le rectangle d'origine.

```python
rect.move(x, y)
```

Pour agrandir (ou réduire) un rectangle depuis la position actuelle de son centre, utilisez la méthode `inflate` avec les valeurs (en pixels) horizontales et verticales à ajouter (ou soustraire) à la dimension actuelle.

```python
inflated_rect = rect.inflate(x, y)
```

**Attention !** Cette méthode renvoie un nouveau rectangle agrandi mais le rectangle d'origine n'est pas affecté. Utilisez la méthode `inflate_ip` pour affecter le rectangle d'origine.

```python
rect.inflate(x, y)
```

### Sprites

pygame fournit une classe de base `Sprite`. Elle définit des propriétés et des méthodes générales. Créez des sous-classes de cette classe pour définir des comportements spécifiques.

Pour créer un nouveau sprite, instanciez la classe `pygame.sprite.Sprite`.

```python
sprite = pygame.sprite.Sprite()
```

**Remarque :** Vous pouvez également passer au constructeur une séquence de groupes de sprites pour ajouter ce sprite à ces groupes dès sa création.

```python
sprite = pygame.sprite.Sprite(sprites_group)
```

Pour ajouter un sprite à un ou plusieurs groupes de sprites à la fois, utilisez la méthode `add`.

```python
sprite.add(sprites_groups)
```

Pour retirer un sprite d'un ou de plusieurs groupes de sprites à la fois, utilisez la méthode `remove`.

```python
sprite.remove(sprites_groups)
```

Pour retirer un sprite de tous les groupes de sprites où il est présent, utilisez la méthode `kill`.

```python
sprite.kill()
```

Pour tester si un sprite est présent dans au moins un groupe de sprites, utilisez la méthode `alive`.

```python
if sprite.alive():
    ...
```

Pour obtenir la liste des groupes de sprites où un sprite est présent, utilisez la méthode `groups`.

```python
sprites_group_list = sprite.groups()
```

La classe `Sprite` définit une méthode `update` vide. Si vous souhaitez définir un comportement spécifique, vous devez sous-classer la méthode `Sprite` et implémenter la méthode `update`.

```python
class MySprite(pygame.sprite.Sprite):
    def __init__(self):
       pygame.sprite.Sprite.__init__(self)
       self.image = pygame.Surface((10, 10))
       self.image.fill('white')
       self.rect = self.image.get_rect()

    def update(self):
        self.rect.x += 5
```

### Groupes de sprites

pygame fournit une classe `Group` qui représente un groupe de sprites (_sprites group_). Cela vous permet de regrouper un ensemble de sprites. Via cette classe, vous pouvez facilement automatiser l'appel à la méthode `update` de chaque sprite présent dans le groupe de sprites.

**Attention !** Un sprite peut être présent dans plusieurs groupes de sprites en même temps. C'est à vous de gérer correctement vos groupes de sprites.

Pour créer un nouveau groupe de sprites, instanciez la classe `pygame.sprite.Group`.

```python
sprites_group = pygame.sprite.Group()
```

**Remarque :** Vous pouvez également passer au constructeur une séquence de sprites que le groupe de sprites ajoutera à sa liste.

```python
sprites_group = pygame.sprite.Group(sprites)
```

Pour appeler la méthode `update` de chaque sprite appartenant au groupe de sprites, utilisez sa méthode `update`.

```python
sprites_group.update()
```

Pour dessiner chaque sprite présent dans le groupe de sprites, utilisez sa méthode `draw` en lui passant la surface sur laquelle dessiner les sprites.

```python
sprites_group.draw(surface)
```

**Attention !** Cette méthode exige que chaque sprite du groupe définisse les propriétés `image` et `rect` de la classe `Sprite`. En effet, la méthode `draw` _blit_ simplement chaque sprite sur la surface :

```python
surface.blit(sprite.image, sprite.rect)
```

Pour ajouter un sprite à un groupe de sprites, utilisez la méthode `add`.

```python
sprites_group.add(sprite)
```

Pour retirer un sprite d'un groupe de sprites, utilisez la méthode `remove`.

```python
sprites_group.remove(sprite)
```

Pour vider un groupe de sprites, utilisez la méthode `empty`.

```python
sprites_group.empty()
```

Pour dupliquer un groupe de sprites, utilisez la méthode `copy`.

```python
sprites_group_copy = sprites_group.copy()
```

Pour tester si un sprite est présent dans un groupe de sprites, utilisez la méthode `has`.

```python
if sprites_group.has(sprite):
    ...
```

**Remarque :** Vous pouvez passer plusieurs sprites séparés par une virgule, ou une séquence de sprites.

```python
if sprites_group.has(sprite1, sprite2):
    ...
```

```python
if sprites_group.has(sprites):
    ...
```

Vous pouvez également utiliser le mot clé `in`.

```python
if sprite in sprites_group:
    ...
```

Pour obtenir la liste des sprites présents dans un groupe de sprites, utilisez la méthode `sprites`.

```python
sprites_list = sprites_group.sprites()
```

Pour obtenir le nombre de sprites présents dans le groupe de sprites, utilisez la fonction `len`.

```python
sprites_number = len(sprites_group)
```

Pour tester si le groupe de sprites contient au moins un sprite, utilisez la fonction `bool`.

```python
if bool(sprites_group):
    ...
```

## Collision

`pygame.sprite.spritecollide`
Find sprites in a group that intersect another sprite.
`pygame.sprite.collide_rect`
Collision detection between two sprites, using rects.
`pygame.sprite.collide_rect_ratio`
Collision detection between two sprites, using rects scaled to a ratio.
`pygame.sprite.collide_circle`
Collision detection between two sprites, using circles.
`pygame.sprite.collide_circle_ratio`
Collision detection between two sprites, using circles scaled to a ratio.
`pygame.sprite.collide_mask`
Collision detection between two sprites, using masks.
`pygame.sprite.groupcollide`
Find all sprites that collide between two groups.
`pygame.sprite.spritecollideany`
Simple test if a sprite intersects anything in a group.
`pygame.Rect.contains`
`pygame.Rect.collidepoint`
test if a point is inside a rectangle
`pygame.Rect.colliderect`
test if two rectangles overlap
`pygame.Rect.collidelist`
test if one rectangle in a list intersects
`pygame.Rect.collidelistall`
test if all rectangles in a list intersect
`pygame.Rect.collidedict`
test if one rectangle in a dictionary intersects
`pygame.Rect.collidedictall`
test if all rectangles in a dictionary intersect

To find the collisions, the Sprites are required to have a Surface.rect attribute assigned.

## Dessin

Le sous-module `draw` contient un ensemble de fonctions vous permettant de dessiner des formes géométriques sur la surface de votre choix (y compris la surface d'affichage).

**Remarque :** Lorsque vous utilisez un tuple de deux nombres pour représenter une coordonnée, vous pouvez également utiliser un objet de type `Vector2` (du sous-module `math`).

**Attention !** Si vous ne le faites pas manuellement, les fonctions de dessin _bloquent_ automatiquement la surface cible avant de dessiner dessus et la débloquent une fois le dessin terminé. Lorsque vous souhaitez dessiner de nombreuses formes sur la même surface, commencez par bloquer la surface avec la méthode `lock` et débloquez-la une fois terminé avec la méthode `unlock`.

```python
surface.lock()
# fonctions de dessin
surface.unlock()
```

### Dessiner un pixel de couleur

La méthode `set_at` des surfaces, dessine un pixel de couleur sur une surface. Passez en argument un tuple de deux nombres correspondant à la position du pixel sur la surface et la couleur à utiliser.

```python
surface.set_at((x, y), couleur)
```

**Remarque :** `set_at` est une méthode de la classe `Surface` et non une fonction du sous-module `draw`. Cependant, comme pour ce sous-module, cette méthode bloque la surface avant de dessiner le pixel et la débloque ensuite.

### Dessiner un segment

La fonction `line` du sous-module `draw` dessine un segment droit sur une surface. Passez en argument la surface sur laquelle dessiner, la couleur à utiliser, un tuple de deux valeurs correspondant au point de départ, un tuple de deux valeurs correspondant au point d'arrivée et la largeur du trait à dessiner.

```python
pygame.draw.line(surface, couleur, (depart_x, depart_y), (arrivee_x, arrivee_y), largeur_trait)
```

**Remarque :** La largeur du trait est optionnelle. Par défaut, la valeur vaut `1`.

### Dessiner une série de segments

La fonction `lines` du sous-module `draw` dessine une série de segments droits sur une surface. Passez en argument la surface sur laquelle dessiner, la couleur à utiliser, un booléen pour préciser s'il faut fermer ou non la forme, une liste contenant des tuples de deux valeurs correspondants aux différents points à relier et la largeur du trait à dessiner.

```python
pygame.draw.lines(surface, couleur, ferme, liste_de_points, largeur_trait)
```

**Remarque :** La largeur du trait est optionnelle. Par défaut, la valeur vaut `1`.

### Dessiner un polygone de couleur

La fonction `polygon` du sous-module `draw` dessine un polygone sur une surface. Passez en argument la surface sur laquelle dessiner, la couleur à utiliser pour dessiner et une liste contenant des tuples de deux valeurs correspondantes aux différents points à relier.

```python
pygame.draw.polygon(surface, couleur, ferme, liste_de_points)
```

### Dessiner un contour de polygone de couleur

La fonction `polygon` du sous-module `draw` dessine un polygone sur une surface. Passez en argument la surface sur laquelle dessiner, la couleur à utiliser pour dessiner, une liste contenant des tuples de deux valeurs correspondantes aux différents points à relier et la largeur du trait à dessiner.

```python
pygame.draw.polygon(surface, couleur, liste_de_points, largeur_trait)
```

### Dessiner un rectangle de couleur

La fonction `rect` du sous-module `draw` dessine un rectangle sur une surface. Passez en argument la surface sur laquelle dessiner, la couleur à utiliser pour dessiner le rectangle et un objet de type `pygame.Rect` definissant la position et les dimensions du rectangle.

```python
pygame.draw.rect(surface, couleur, rectangle)
```

### Dessiner un contour de rectangle de couleur

La fonction `rect` du sous-module `draw` dessine un rectangle sur une surface. Passez en argument la surface sur laquelle dessiner, la couleur à utiliser pour dessiner le contour du rectangle, un objet de type `pygame.Rect` definissant la position et les dimensions du rectangle et la largeur (en pixels) du contour à dessiner.

```python
pygame.draw.rect(surface, couleur, rectangle, largeur_contour)
```

### Dessiner un cercle de couleur

La fonction `circle` du sous-module `draw` dessine un cercle sur une surface. Passez en argument la surface, la couleur, un tuple de deux valeurs correspondant à la position du centre du cercle et le rayon du cercle.

```python
pygame.draw.circle(surface, couleur, (centre_x, centre_y), rayon)
```

### Dessiner un contour de cercle de couleur

La fonction `circle` du sous-module `draw` dessine un cercle sur une surface. Passez en argument la surface, la couleur, un tuple de deux valeurs correspondant à la position du centre du cercle, le rayon du cercle et la largeur (en pixels) du contour à dessiner.

```python
pygame.draw.circle(surface, couleur, (centre_x, centre_y), rayon, largeur_contour)
```

### Dessiner une ellipse de couleur

La fonction `ellipse` du sous-module `draw` dessine une ellipse sur une surface. Passez en argument la surface sur laquelle dessiner, la couleur à utiliser pour dessiner l'ellipse et un objet de type `pygame.Rect` definissant la position et les dimensions du rectangle englobant l'ellipse.

```python
pygame.draw.ellipse(surface, couleur, rectangle_englobant)
```

### Dessiner un contour d'ellipse de couleur

La fonction `ellipse` du sous-module `draw` dessine une ellipse sur une surface. Passez en argument la surface sur laquelle dessiner, la couleur à utiliser pour dessiner l'ellipse, un objet de type `pygame.Rect` definissant la position et les dimensions du rectangle englobant l'ellipse et la largeur (en pixels) du contour à dessiner.

```python
pygame.draw.ellipse(surface, couleur, rectangle_englobant, largeur_contour)
```

## Surfaces

Pour créer une surface, appelez le constructeur de la classe `Surface` en lui passant les dimensions (en pixels) de la surface à créer. Les dimensions peuvent être un tuple de deux valeurs ou un `Vector2`.

```python
new_surface = pygame.Surface(dimensions)
```

### Afficher une surface

Pour afficher une surface, utilisez la méthode `blit` de la surface d'affichage et passez la surface à afficher ainsi que la position de l'image sur la surface d'affichage (un tuple de deux valeurs, un `Vector2` ou un `Rect`).

```python
display_surface.blit(surface, position)
```

### Récupérer le rectangle associé à une surface

Utilisez la méthode `get_rect` de la classe `pygame.Surface`.

```python
rectangle = surface.get_rect()
```

La méthode accepte également des paramètres nommés correspondants aux propriétés de la classe `pygame.Rect`.

```python
rectangle = surface.get_rect(center=(100, 100))
```

## Images

### Charger une image

pygame prend toujours en charge par défaut le format BMP non compressé. Chargez une image dans ce format en utilisant la fonction `load_basic` du sous-module `image`. Une image chargée dans pygame devient une surface.

```python
surface = pygame.image.load_basic(fichier_bmp)
```

Si vous souhaitez charger d'autres formats vérifiez si pygame les prend en charge avec la fonction `get_extended` du sous-module `image`.

```python
if pygame.image.get_extended():
    # pygame prend en charge les formats d'images étendus
```

Ensuite, chargez une image au format JPG, PNG, GIF, ... avec la fonction `load` du sous-module `image`.

```python
surface = pygame.image.load(fichier_image)
```

**Remarque :** Même si pygame prend en charge les formats d'images étendus, il n'est pas garanti que pygame prenne en charge tous les formats d'image existants.

### Améliorer la performance des images

Par défaut, une image chargée dans une surface est au même format que celui du fichier image d'origine. Utilisez la méthode `convert` sans arguments (de la classe `Surface`) pour convertir une surface dans un format adapté à celui de la surface d'affichage. Cela accélère son affichage.

```python
surface = pygame.image.load(fichier_image).convert()
```

**Remarque :** Cette méthode ne prend pas en charge l'opacité. Les pixels transparents ou semi transparents prennent une opacité maximale. Si vous souhaitez conserver les informations d'opacité de l'image d'origine, utilisez la méthode `convert_alpha`.

### Conserver la couche alpha d'une image

Utilisez la méthode `convert_alpha` sans arguments (de la classe `Surface`) pour convertir une image dans un format idéal pour l'affichage sur la surface d'affichage mais conservant les données d'opacité des pixels. Cela accélère leur affichage (mais est un peu moins performant que la méthode `convert`).

```python
surface = pygame.image.load(fichier_image).convert_alpha()
```

### Définir la couleur transparente

Utilisez la méthode `set_colorkey` pour définir la couleur qui sera considérée comme transparente si votre image contient uniquement des pixels totalement opaques et totalement transparents. Cela est plus efficace que d'utiliser une image avec des pixels semi-transparents.

```python
surface.set_colorkey(couleur)
```

### Obtenir le rectangle à partir d'une image

Utilisez la méthode `get_rect`.

```python
rect = image.get_rect()
```

### Afficher une image

Pour afficher une image, utilisez la même technique que pour afficher une surface (car une image chargée en mémoire est une surface).

Utilisez la méthode `blit` sur la surface d'affichage et passez la surface représentant l'image à afficher ainsi qu'un tuple correspondant à la position de l'image sur la surface d'affichage.

```python
display_surface.blit(surface, (x, y))
```

## Déplacer un rectangle avec le clavier

```python
speed = 5
keys_pressed = pygame.key.get_pressed()
if keys_pressed[pygame.K_LEFT]:
    position_x -= speed
if keys_pressed[pygame.K_RIGHT]:
    position_x += speed
if keys_pressed[pygame.K_UP]:
    position_y -= speed
if keys_pressed[pygame.K_DOWN]:
    position_y += speed
```

## Plein écran et fenêtre redimensionnable

```python
import pygame, sys

mainClock = pygame.time.Clock()
from pygame.locals import *
pygame.init()
pygame.display.set_caption('game base')
monitor_size = [pygame.display.Info().current_w, pygame.display.Info().current_h]
screen = pygame.display.set_mode((500, 500), pygame.RESIZABLE)

fullscreen = False

while True:

    screen.fill((0, 0, 50))

    pygame.draw.rect(screen, (255, 0, 0), pygame.Rect(screen.get_width() - 5 - (screen.get_width() / 5), 50, screen.get_width() / 5, 50))

    for event in pygame.event.get():
        if event.type == QUIT:
            pygame.quit()
            sys.exit()
        if event.type == VIDEORESIZE:
            if not fullscreen:
                screen = pygame.display.set_mode((event.w, event.h), pygame.RESIZABLE)
        if event.type == KEYDOWN:
            if event.key == K_ESCAPE:
                pygame.quit()
                sys.exit()
            if event.key == K_f:
                fullscreen = not fullscreen
                if fullscreen:
                    screen = pygame.display.set_mode(monitor_size, pygame.FULLSCREEN)
                else:
                    screen = pygame.display.set_mode((screen.get_width(), screen.get_height()), pygame.RESIZABLE)

    pygame.display.update()
    mainClock.tick(60)
```
