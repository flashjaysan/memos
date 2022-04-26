# Mémo express

_par flashjaysan_

## Préparatifs

```
npm init -y
```

```
npm i -s express nodemon
```

`-s` pour save.

Editez le fichier `package.json`.

```json
{
  ...
  "scripts": {
    "start": "nodemon index.js"
  }
  ...
}
```

```
npm start
```

## Projet

```js
const express = require("express");
const app = express();

const callback = () => {
  console.log("Server started: 5500.");
};

app.listen(5500, callback);
```

Créer un dossier `models`.
