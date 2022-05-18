# Mémo Firebase

_par flashjaysan_

Firebase 9 propose une approche modulaire qui n'importe que les fonctions qu'on utilise.

## Préparatifs

### NodeJS

Installez NodeJS.

### Projet

- Créez un fichier `index.js` à la racine du projet.
- Créez un dossier `dist` à la racine du projet. Ce dossier contiendra les fichiers rassemblés pour être déployés.
- Créez un fichier `index.html` dans le dossier `dist`.

```html
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta http-equiv="X-UA-Compatible" content="IE=edge" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Firebase 9</title>
  </head>
  <body>
    <h1>Getting started</h1>
    <script src="bundle.js"></script>
  </body>
</html>
```

Ouvrez un terminal et saisissez la commande :

```
npm init -y
```

### Webpack

Vous devez également installer un bundler de modules (en l'occurence _webpack_). Généralement, avec React, il est déjà installé.

```
nmp i webpack webpack-cli -D
```

Créez un fichier `webpack.config.js` à la racine du projet.

```js
const path = require("path");

module.exports = {
  mode: "development",
  entry: "./src/index.js",
  output: {
    path: path.resolve(__dirname, "dist"),
    filename: "bundle.js",
  },
  watch: true,
};
```

Ouvrez le fichier `package.json` et ajoutez un nouveau script.

```json
{
  ...
  "scripts": {
    ...
    build: "webpack",
    ...
  }
  ...
}
```

Exécutez la commande pour lancer le bundler.

```
npm run build
```

### Live Server

Installez l'extension Live Server dans VS Code.

Faites un clic droit dans le fichier `index.html` et choisissez l'option `Open with Live Server` pour afficher la page dans le navigateur.

## Créez un projet Firebase

- Allez dans la console Firebase et cliquez sur le bouton `Add project`.
- Saisissez le nom de votre projet et cliquez sur le bouton `Continue`.
- Désactivez l'option `Enable Google Analytics for this project` et cliquez sur le bouton `Create project`.
- Cliquez sur le bouton `Continue` pour terminer la création du projet.

## Création du frontend de l'application

- Cliquez sur l'icone web pour créer une application web.
- Saisissez le nom de l'application web.
- Cliquez sur le bouton `Register app`.
- Cliquez sur le bouton `Continue to console`.

- Dans le dashboard du projet, cliquez sur l'application web dans la liste et cliquez sur l'icône roue crantée.
- Faites défiler l'affichage pour atteindre la section `SDK setup and configuration`.
- Cochez le bouton radio `Config`.
- Copiez le texte en dessous.
- Collez ce texte dans le fichier `index.js` du projet.

## Installer Firebase

```
npm install firebase
```

## Initialiser Firebase

Avant Firebase 9, on importait toute la lib Firebase.

```js
import firebase from 'firebase/app';

...

firebase.initializeApp(firebaseConfig);
```

Depuis Firebase 9, on importe les fonctions plutôt que la lib.

```js
import { initializeApp } from 'firebase/app';

...

initializeApp(firebaseConfig);
```

## Créer une base de données

- Dans le dashboard de Firebase, cliquez sur l'option `Firestore Database`.
- Cliquez sur le bouton `Create database`.
- Cochez l'option `Start in test mode`.
- Cliquez sur le bouton `Next`.
- Choisissez un emplacement dans le cloud.
- Cliquez sur le bouton `Enable`.

## Créer une collection

- Dans la base de données, cliquez sur le bouton `Start collection`.
- Saisissez le nom de la collection (Collection ID).
- Cliquez sur le bouton `Next`.
- Saisissez le nom du premier document (Document ID).

**Remarque :** Vous pouvez également cliquez sur le champ `Auto-ID` pour générer automatiquement un nom aléatoire de document.

- Saisissez un nom de propriété (Field) et définissez son type et sa valeur (Value).
- Cliquez sur le bouton `+` si vous souhaitez ajouter de nouvelles propriétés au document.
- Cliquez sur le bouton `Save`.

- Cliquez sur le champ `Add document` pour créer un nouveau document et renseigner ses propriétés.
- Cliquez sur le champ `Add field` pour ajouter une propriété au document sélectionné.

## Accéder à la base de données

Importez la fonction `getFirestore`.

```js
import { getFirestore } from "firebase/firestore";
```

Appelez cette fonction pour obtenir un lien vers la base de données.

```js
const database = getFirestore();
```

## Accéder à une collection

Importez la fonction `collection`.

```js
import { collection } from "firebase/firestore";
```

Appelez cette fonction en lui passant la référence à la base de données et le nom de la collection.

```js
const collectionReference = collection(database, "nom_collection");
```

## Accéder aux documents

Importez la fonction `getDocs`.

```js
import { getDocs } from "firebase/firestore";
```

Appelez cette fonction en lui passant la référence à la collection.

```js
getDocs(collectionReference);
```

**Remarque :** Cette fonction asynchrone renvoie une _promise_. Vous pouvez donc appeler la méthode `then` pour exécuter une callback après avoir terminé l'exécution (après avoir récupéré les documents). Cette callback prend un `snapshot` qui contient tous les documents au travers de sa propriété `docs`.

```js
getDocs(collectionReference).then((snapshot) => {
  console.log(snapshot.docs);
});
```

Utilisez la méthode `data` sur chaque élément de la propriété `docs` pour accéder aux données.

```js
getDocs(collectionReference)
  .then((snapshot) => {
    let documentDatas = [];

    snapshot.docs.forEach((doc) => {
      documentDatas.push({ ...doc.data(), id: doc.id });
    });

    console.log(documentDatas);
  })
  .catch((err) => {
    console.log(err.message);
  });
```

## Créer un document depuis l'application

Importez la fonction `addDoc`.

```js
import { addDoc } from "firebase/firestore";
```

Dans le fichier `index.html` ajoutez un formulaire.

```html
<form class="add">
  <label for="title">Title: </label>
  <input type="text" name="title" required />

  <label for="author">Author: </label>
  <input type="text" name="author" required />

  <button>Add data</button>
</form>
```

Dans le fichier `index.js` ajoutez le code :

```js
const addBookForm = document.querySelector(".add");

addBookForm.addEventListener("submit", (e) => {
  e.preventDefault();

  addDoc(collectionReference, {
    title: addBookForm.title.value,
    author: addBookForm.author.value,
  }).then(() => {
    addBookForm.reset();
  });
});
```

La base de données est mise à jour avec l'ajout du document mais la page web n'affiche pas cette mise à jour si vous utilisez la fonction `getDocs`.

## Supprimer un document depuis l'application

Importez la fonction `deleteDoc` et la fonction `doc`.

```js
import { deleteDoc, doc } from "firebase/firestore";
```

Dans le fichier `index.html` ajoutez un formulaire qui permet de saisir un id.

```html
<form class="delete">
  <label for="id">Document id: </label>
  <input type="text" name="id" required />

  <button>Delete data</button>
</form>
```

**Remarque :** Rappelez-vous que chaque document possède un id unique (généré aléatoirement par Firebase) permettant d'identifier un document dans une collection. C'est grâce à cet id que l'on peut supprimer un document précis.

Dans le fichier `index.js` ajoutez le code :

```js
const deleteBookForm = document.querySelector(".delete");

deleteBookForm.addEventListener("submit", (e) => {
  e.preventDefault();

  const docRef = doc(database, "nom_collection", deleteBookForm.id.value);

  deleteDoc(docRef).then(() => {
    deleteBookForm.reset();
  });
});
```

La base de données est mise à jour avec la suppression du document mais la page web n'affiche pas cette mise à jour si vous utilisez la fonction `getDocs`.

## Accéder aux données en temps réel

Au lieu d'utiliser la fonction `getDocs`, utilisez la fonction `onSnapshot`.

Importez cette fonction.

```js
import { onSnapshot } from "firebase/firestore";
```

Supprimez la fonction `getDocs` et appelez la fonction `onSnapshot` à la place.

```js
onSnapshot(collectionReference, (snapshot) => {
  let documentDatas = [];

  snapshot.docs.forEach((doc) => {
    documentDatas.push({ ...doc.data(), id: doc.id });
  });

  console.log(documentDatas);
});
```

Notez que la fonction `onSnapshot` prends une callback en second argument. Cette callback s'exécute lors de l'appel à la fonction `onSnapshot` mais également à chaque changement dans la base de données.

## Effectuer une requête sur la base de données

Importez les fonctions `query` et `where`.

```js
import { query, where } from "firebase/firestore";
```

Appelez la fonction `query` en lui passant la référence à la collection et la fonction `where` pour récupérer une liste filtrée de document.

```js
const q = query(collectionReference, where("nom_propriete", "==", "valeur"));
```

La fonction `where` prend un nom de propriété des documents à filtrer, un opérateur de comparaison et une valeur à comparer.

Appelez la fonction onSnaptshot en lui passant la liste filtrée de documents à la place de la référence à la collection.

```js
onSnapshot(q, (snapshot) => {
  let documentDatas = [];

  snapshot.docs.forEach((doc) => {
    documentDatas.push({ ...doc.data(), id: doc.id });
  });

  console.log(documentDatas);
});
```

## Obtenir un document particulier

Importez la fonction `getDoc`.

```js
import { getdoc } from "firebase/firestore";
```

```js
const documentReference = doc(database, "nom_collection", "document_id");

getDoc(documentReference).then((doc) => {
  console.log(doc.data(), doc.id);
});
```

Si vous souhaitez obtenir les valeurs du document si elles changent, appelez la fonction `onSnapshot`.

```js
onSnapshot(documentReference, (doc) => {
  console.log(doc.data(), doc.id);
});
```

## Trier les documents

Importez la fonction `orderBy`.

```js
import { orderBy } from "firebase/firestore";
```

Appelez la fonction `query` comme précédemment mais avec un nouvel argument appelant la faonction `orderBy`.

```js
const q = query(
  collectionReference,
  where("nom_propriete", "==", "valeur"),
  orderBy("nom_propriete", "desc")
);
```

La fonction `orderBy` prend un nom de propriété des documents et un ordre. L'ordre est croissant par défaut. Il peut avoir comme valeur :

- `'asc'` pour un tri croissant.
- `'desc'` pour un tri décroissant.

**Attention :** Le tri ne peut être effectué que si la collection est configurée pour que les documents possèdent un index. Allez sur le dashboard Firebase du projet, cliquez sur la section `Firestore Database`, sélectionnez la collection et cliquez sur le bouton `Create index`.

## Ajouter un timestamp à un document

Plutôt qu'utiliser la fonction JavaScript `Date`, utilisez la fonction `serverTimestamp`. Importez-la.

```js
import { serverTimestamp } from "firebase/firestore";
```

Appelez ensuite la fonction pour créer un timestamp à l'instant de l'appel.

```js
created = serverTimestamp();
```

## Mettre à jour un document

Importez la fonction `updateDoc`.

```js
import { updateDoc } from "firebase/firestore";
```

Créez un event listener pour gérer la validation du formulaire.

```js
const updateForm = document.querySelector(".update");
```

```js
updateForm.addEventListener("submit", (e) => {
  e.preventDefault();
});
```

Obtenez la référence au document à mettre à jour.

```js
const documentReference = doc(database, "nom_collection", updateForm.id.value);
```

Appelez la fonction `updateDoc` en lui passant le document à mettre à jour et un objet avec les nouvelles clés/valeurs.

```js
updateDoc(documentReference, {
  title: "updated",
});
```

**Attention !** Seules les clés passées sont modifiées. Les clés non présentes restent à leur ancienne valeur.

La fonction updateDoc renvoie une Promise. Utilisez la méthode `then` au besoin.

```js
updateDoc(documentReference, {
  title: "updated",
}).then(() => {
  updateForm.reset();
});
```

## Authentification

### Activer l'authentification

- Dans le dashboard Firebase, cliquez sur la section `Authentication`.
- Dans l'onglet `Sign-in method`, cliquez sur l'option `Email/Password`.
- Activez le bouton `Enable`.
- Cliquez sur le bouton `Save`.

**Remarque :** Dans l'onglet `Sign-in method`, Firebase propose également d'autres méthodes de connexion via des plateformes telles que Google, Facebook ou Github.

### Initialiser l'authentification

Importer la fonction `getAuth`.

```js
import { getAuth } from "firebase/auth";
```

Initialisez l'authentification en appelant cette fonction et stockez son résultat dans une variable.

```js
const auth = getAuth();
```

Créez un formulaire.

```html
<form class="signup">
  <label for="email">email : </label>
  <input type="email" name="email" />
  <label for="password">password : </label>
  <input type="password" name="password" />
  <button>signup</button>
</form>
```

Attachez un évènement à ce formulaire.

```js
const signupForm = document.querySelector(".signup");

signupForm.addEventListener("submit", (e) => {
  e.preventDefault();
});
```

**Remarque :** Firebase impose des mots de passe d'au moins six caractères.

### Créer un nouvel utilisateur

Importez la fonction `createUserWithEmailAndPassword`.

```js
import { createUserWithEmailAndPassword } from "firebase/auth";
```

Dans l'event listener, appelez cette fonction. Passez l'objet `auth`, l'email et le mot de passe.

```js
signupForm.addEventListener("submit", (e) => {
  e.preventDefault();

  const email = signupForm.email.value;
  const password = signupForm.password.value;

  createUserWithEmailAndPassword(auth, email, password);
});
```

**Remarque :** La fonction `createUserWithEmailAndPassword` est asynchrone. Elle renvoit une Promise. Vous pouvez donc appeler la méthode `then` sur ce qu'elle renvoit. Utilisez un paramètre de callback représentant les données d'authentification de l'utilisateur (_user crendentials_) créé.

```js
signupForm.addEventListener("submit", (e) => {
  e.preventDefault();

  const email = signupForm.email.value;
  const password = signupForm.password.value;

  createUserWithEmailAndPassword(auth, email, password)
    .then((userCredential) => {
      console.log("User created: ", userCredential.user);
      signupForm.reset();
    })
    .catch((error) => {
      console.log(error.message);
    });
});
```

**Remarque :** `userCredential.user` est un objet contenant diverses informations dont une propriété `uid` identifiant l'utilisateur de manière unique dans Firebase.
