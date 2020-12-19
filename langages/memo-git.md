# Mémo Git

*par flashjaysan*

## Installer Git



## Utilisation

Ouvrez une ligne de commande puis placez-vous dans le dossier cible.

Pour créer un projet :

```
git init
```

Pour configurer votre adresse mail liée à votre projet :

```
git config --global user.email "adresse_mail"
```

Pour configurer votre nom lié à votre projet :

```
git config --global user.name "nom"
```

Pour afficher la configuration du projet :

```
git config --list
```

Pour afficher le status actuel du projet :

```
git status
```

Lorsque vous créez de nouveaux fichiers, ils ne sont pas pris en charge par Git. Ils sont "untracked". Vous devez les ajouter.

Pour ajouter un fichier :

```
git add nom_fichier
```

Pour ajouter tous les fichiers :

```
git add --all
```

Pour que Git ignore un fichier, créer un fichier `.gitignore`. Ce fichier texte vous permet d'ajouter le chemin des fichiers à ignorer. Placez-en un par ligne. Vous pouvez utiliser le caractère `*` pour désigner un groupe de fichiers (par exemple `*.txt`).

Pour commit le projet :

```
git commit -m "message"
```

Pour afficher les commits précédents :

```
git log
```

Pour n'afficher qu'un certain nombre de commits précédents :

```
git log --n nombre_de_commits
```

Pour afficher les commits précédents de manière plus concise :

```
git log --oneline
```

Pour afficher les différences entre le projet en cours et le dernier commit :

```
git diff
```

Pour revoir l'état d'un commit précédent :

```
git checkout cle_sha1_commit
```

Pour voir l'état du projet actuel :

```
git checkout master
```

Cela provoque une erreur si vous avez fait des modifications sans les commit.

Pour rétablir un fichier d'un commit précédent dans le projet actuel :

```
git checkout cle_sha1_commit nom_de_fichier
```

Pensez à commit le changement.








