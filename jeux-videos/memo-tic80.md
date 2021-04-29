# Mémo TIC-80

*par flashjaysan*

## Console

### Lister les dossiers et les fichiers

```
ls
```

ou

```
dir
```

### Afficher le dossier dans l'explorateur du système

```
folder
```

### Créer un dossier

```
mkdir nom_dossier
```

### Changer de dossier

Pour descendre d'un niveau :

```
cd nom_dossier
```

Pour remonter d'un niveau :

```
cd ..
```

### Ajouter les jeux démos

```
demo
```

### Ajouter un jeu

```
add
```

puis sélectionnez le fichier à ajouter à TIC-80.

### Trouver des jeux

Rendez vous sur le [site officiel de TIC-80](https://tic80.com/play).

### Créer un jeu

```
new
```

### Charger un jeu

```
load nom_jeu
```

**Remarque :** Par défaut, l'extension des jeux est `.tic`. La version pro vous permet également de charger le jeu depuis un fichier Lua. Faites suivre le nom du jeu par l'extension `.lua`.

```
load nom_jeu.lua
```

### Sauvegarder le jeu en cours d'édition

```
save nom_jeu
```

**Remarque :** Par défaut, l'extension des jeux est `.tic`. La version pro vous permet également de sauvegarder le jeu sous forme de fichier Lua. Faites suivre le nom du jeu par l'extension `.lua`.

```
save nom_jeu.lua
```

### Exécuter le jeu en cours d'édition

```
run
```

### Supprimer un dossier ou un fichier

```
del nom_fichier_ou_dossier
```

### Passer de la console à l'éditeur

```
edit
```

ou appuyez sur `ECHAP`.

## Jeu

### Quitter le jeu et revenir à la console

Appuyez sur `ECHAP`.

## Editeur

### Passer de l'éditeur à la console

Appuyez sur `ECHAP`.

### Informations sur la cartouche

En tête du fichier source, créez quatre commentaires.

```lua
-- title:  nom_cartouche.tic
-- author: votre nom
-- desc:   description du jeu
-- script: lua
```

### Fonction principale

TIC-80 nécessite l'utilisation de la fonction `TIC` pour définir la boucle principale. Elle se répète 60 fois par seconde et elle est appelée automatiquement par TIC-80.

```lua
function TIC()
  -- votre code
end
```

## Contrôles

La fonction `btn` renvoie `true` si la touche associée est appuyée dans la boucle en cours.

```lua
if btn(indice_touche) then
  -- code si touche appuyée
end
```

La fonction `btnp` renvoie `true` si la touche associée est appuyée dans la boucle en cours mais qu'elle ne l'était pas dans la boucle précédente. Autrement dit, la touche vient juste d'être appuyée.

```lua
if btnb(indice_touche) then
  -- code si touche juste appuyée
end
```

Pour un clavier QWERTY, les indices correspondent aux touches suivantes :

- `0` : Touche clavier `HAUT`.
- `1` : Touche clavier `BAS`.
- `2` : Touche clavier `GAUCHE`.
- `3` : Touche clavier `DROITE`.
- `4` : Touche clavier `Z`.
- `5` : Touche clavier `X`.
- `6` : Touche clavier `A`.
- `7` : Touche clavier `S`.

### Fonctions de dessin

#### Remplir l'écran avec une couleur

```lua
cls(indice_couleur)
```

L'indice de couleur correspond à l'indice associé à une couleur de la palette.



