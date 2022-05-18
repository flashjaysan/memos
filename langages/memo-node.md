# Mémo NodeJS

_par flashjaysan_

## Introduction

NodeJS est un environnement d'exécution utilisant le langage de programmation JavaScript. Il repose sur le moteur JavaScript V8 de Chrome.

Il embarque de nombreuses fonctionnalités pour le back end mais ne possède pas les fonctionnalités intégrées aux navigateurs. Il intègre un gestionnaire de bibliothèques (NPM) qui permet d'étendre les fonctionnalités avec de très nombreuses bibliothèques tierces.

L'environnement d'exécution est monothread et asynchrone. Cela signifie qu'il est idéal pour la gestion de gros volumes de données (fichiers ou bases de données) mais qu'il est peu adapté à des applications exigeantes en puissance processeur.

## Exécuter un script

`node nom_script.js`

## Créer un projet

```
nmp install
```

Crée un fichier `package.json` dans le dossier courant. Pour éviter de saisir des informations et créer un fichier par défaut, ajouter l'option `-y` à la commande.

```
npm install -y
```

**Remarque :** Vous pouvez également créer vous-même le fichier.

```json
{
  "name": "nom_projet",
  "author": "votre_nom",
  "private": true,
  "dependencies": {}
}
```

## Installer un module

```
npm install nom_module --save
```

**Remarque :** L'option `--save` enregistre le module dans le fichier `package.json`. Cela permet de partager le projet avec d'autres personnes et ces dernières peuvent ensuite installer les modules automatiquement avec la commande `npm install`.

```
npm install
```

## Ignorer les modules dans Git

## Fonctions globales

Les commandes suivantes sont accessibles par défaut. Elles font en réalité partie de l'objet global `global`. Vous pouvez donc ajouter le préfixe `global.` si vous le souhaitez.

```js
console.log();
setTimeout();
clearTimeout();
setInterval();
clearInterval();
```

Les identifiants déclarés au plus haut niveau d'un fichier ne sont pas associés à l'objet `global` pour éviter les clashs entre fichiers sources.

## Modules

Chaque fichier source est un module. Les identifiants déclarés dans un module sont inaccessibles depuis d'autres modules à moins de les exporter explicitement.

### Créer un module

Dans un fichier source où vous souhaitez exporter des identifiants, associez ces identifiants à l'objet `module.exports`.

```js
function print(message) {
  console.log(message);
}

module.exports.print = print;
```

**Remarque :** Si vous ne voulez exporter qu'un seul identifiant (par exemple une classe), associez l'identifiant directement à l'objet `module.exports`.

```js
function print(message) {
  console.log(message);
}

module.exports = print;
```

### Charger un module

Dans un fichier source où vous souhaitez utiliser des identifiants d'un autre module, utilisez la fonction `require`.

```js
const monModule = require("module_path");
monModule.print("Hello.");
```

**Remarque :** L'extension est optionnelle. Vous pouvez écrire `require('module_path.js');`.

Si le module exporté est directement associé à l'objet `module.exports`, utilisez le directement.

```js
const monModule = require("module_path");
monModule("Hello.");
```

### Variables d'environnement

Créez un fichier `.env.local` à la racine du projet.

Editez ce fichier et créez les variables d'environnement de votre choix.

```
NOM_VARIABLE_ENVIRONNEMENT=valeur
```

Pour utiliser une variable d'environnement dans votre projet, utilisez `process.env`.

```
variable = process.env.NOM_VARIABLE_ENVIRONNEMENT
```

**Remarque :** Si vous avez une exécution de node en cours, redémarrez l'exécution.
