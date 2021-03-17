# Mémo Git

*par flashjaysan*

## Introduction

Git est un système de contrôle de versions. Autrement dit, c'est un logiciel qui vous permet de gérer différentes versions d'un projet.

Avec Git vous pouvez par exemple :

- Sauvegarder facilement l'état actuel d'un projet.
- Créer différentes versions (branches) d'un projet.
- Restaurer un état antérieur d'un projet si besoin.
- Travailler à plusieurs sur un projet commun.

## Fonctionnement

Le tout premier commit définit l'état initial du projet. Tout nouveau commit enregistrera uniquement les différences entre ce commit initial et le commit actuel.

## Différence entre Git et Github

Il arrive souvent de confondre Git et Github mais ce sont deux choses bien différentes.

- Git est un logiciel qui s'installe sur votre ordinateur. Une fois installé, vous pouvez vous en servir sans connexion à internet pour gérer les version d'un projet local à votre machine.
- Github est un service en ligne d'hébergement de dépots. Il est principalement utilisé conjointement avec Git mais vous pouvez également vous en servir pour stocker un projet sans utiliser Git. Il existe d'autres services similaires tels que Gitlab et Bitbucket.

L'intérêt principal de ces services d'hébergement de dépots est de permettre le stockage en ligne des différentes versions d'un projet. Cela vous permet de sauvegarder votre projet en ligne et ainsi de le préserver d'éventuelles pannes sur votre machine. Cela permet également l'accès à votre projet par plusieurs personnes. Chaque personne ayant accès au projet peut créer une branche à partir d'une copie du projet maître et travailler librement sur cette branche sans risquer de provoquer de conflit avec les autres membres de l'équipe.

## Télécharger et installer Git



## Terminologie

- Repository (dépot en français) : emplacement (sur votre ordinateur ou sur un serveur distant) où est stocké tout l'historique d'un projet avec les différentes modifications sauvegardées.
- Commit : 
- Stage :
- Branch :
- Master :
- Merge :
- Pull :
- Push :
- Pull Request /PR :
- Clone :
- Conflict :
- Track :


## Utilisation

Ouvrez une ligne de commande puis placez-vous dans le dossier cible.

Pour créer un repository :

```
git init
```

**Attention !** Le repository est créé à l'emplacement où se trouve la console au moment de la saisie de cette commande.

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

Vous pouvez également ajouter tout le contenu du dossier :

```
git add .
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

Pour voir l'ensemble des branches :

```
git branch
```

Pour créer une branche :

```
git checkout -b
```

Ou :

```
git checkout -b nom_de_branche
```

Pour fusionner des branches, positionnez vous sur la branche à remplacer puis :

```
git merge nom_de_branche
```

Pour supprimer une banche :

```
git branch -D nom_de_branche
```










