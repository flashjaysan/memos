# Mémo HTTP

*par flashjaysan*

## Principe

Une connexion HTTP envoie une **requête** à un serveur et ce dernier renvoie une **réponse**.

## Requêtes HTTP

Une requête est constituée d'une URI (URL + chemin de l'API), d'une méthode décrivant l'action à effectuer par le serveur, de métadonnées stockées dans son en-tête (header), et d'un corps (body) contenant les données à transmettre au serveur.

### Méthodes

- `POST` : Create.
- `GET` : Read.
- `PATCH` : Update.
- `DELETE` : Delete.

### Header

Correspond aux métadonnées de la requête.

- `Accept` : .
- `Authorization` : .
- `Connection` : .

### Body

- `` : .

## Réponses

### Code

- Le code `200` indique la réussite de la requête.
- La famille de codes `4XX` indique un problème dans la requête.
- La famille de codes `5XX` indique un problème côté serveur.

### Header

L'en-tête d'une réponse contient les métadonnées liées au serveur.

### Body

Le corps d'une réponse contient les informations (au format JSON) réelles demandées par la requête.

# express

```js
const express = require('express');
const app = express();
const PORT = 8080;

app.use(express.json());

app.get('/path', (req, res) => {
  res.status(200).send({
    cle1: valeur1,
    cle2: valeur2
  });
});
```

- `get` est la méthode.
- `'/path'` est le chemin pour attaquer le service.
- La fonction est appelée quand une requête est faite sur cette URI.
- `req` correspond aux données de la requête.
- `res` correspond aux données
- L'objet contenu dans la méthode `send` est le résultat renvoyé au client.

```js
app.post('/path/:id', (req, res) => {
  const { id } = req.params;
  const { logo } = req.body;

  if (!logo) {
    res.status(418).send({ message: 'We need a logo!' });
  }

  res.send({
    tshirt: `shirt with your ${logo} and ID of ${id}`
  });
});
```
