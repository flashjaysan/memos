# Mémo React

_par flashjaysan_

## Prérequis

Vous devez avoir une bonne connaissance générale des langages JavaScript (ES6) et HTML.

## Créer un nouveau projet

### NodeJS

Commencez par installer NodeJS.

### create-react-app

Utilisez l'outil `create-react-app` pour créer une nouvelle application React.

```
npx create-react-app nom-projet
```

Un dossier portant le nom de votre projet est créé à l'emplacement où vous avez exécuté la commande précédente.

Déplacez-vous dans ce dossier.

```
cd nom-projet
```

### Lancer l'application

Utilisez la commande `npm start` pour lancer l'exécution de l'application.

```
npm start
```

Ouvrez votre navigateur et rendez-vous sur l'URL locale `localhost:3000`.

### Visual Studio Code

Ouvrez le projet avec Visual Studio Code.

```
code .
```

## Principes de base

React crée un DOM virtuel en mémoire. Il utilise ce DOM virtuel pour appliquer les changements au DOM réel du navigateur. Il ne change que ce qui doit être changé.

A REMPLIR

## Hooks

Trois règles essentielles :

- Les hooks ne peuvent être appelées que dans des composants fonctions.
- Les hooks ne peuvent être appelés qu'au niveau le plus haut d'un composant.
- Les hooks ne peuvent pas être conditionnels.

**Remarque :** Les hooks ne fonctionnent pas dans des composants classes.

A REMPLIR

## React Router

Installez le package `react-router-dom`.

```
npm install react-router-dom
```

Utilisez le composant `BrowserRouter` pour englober la gestion des routes.

```jsx
import { BrowserRouter } from "react-router-dom";

<BrowserRouter></BrowserRouter>;
```

Utilisez le composant `Switch` pour englober les différentes routes.

```jsx
import { BrowserRouter, Switch } from "react-router-dom";

<BrowserRouter>
  <Switch></Switch>
</BrowserRouter>;
```

Utilisez le composant `Route` pour définir une route. La propriété `path` défini le chemin de la route.

```jsx
import { BrowserRouter, Switch, Route } from "react-router-dom";

<BrowserRouter>
  <Switch>
    <Route path="/">
      <Home />
    </Route>
    <Route path="/about">
      <About />
    </Route>
    <Route path="/products">
      <Products />
    </Route>
  </Switch>
</BrowserRouter>;
```

**Attention !** Par défaut, le chemin racine `"/"` est générique et est utilisé pour toutes les routes qui ne sont pas définies. Pour éviter ce comportement, ajoutez la propriété `exact` au composant `Route`.

```jsx
<Route path="/" exact>
  <Home />
</Route>
```

**Remarque :** Vous pouvez passer le composant à afficher dans la route via une propriété `component` du composant `Route`. Notez que dans ce cas, vous passez le composant directement et non comme une balise.

```jsx
<Route path="/" component={Home} />
<Route path="/about" component={About} />
<Route path="/products" component={Products} />
```

### Routes dynamiques

```jsx

```

### Routes imbriquées

Une route imbriquée est une route contenue dans une autre route. Par exemple, `/about/offers`.

Créez la route parente.

```jsx
<Route path="/about" component={About} />
```

Dans le composant `About`, créez la route imbriquée avec le chemin complet (y compris le chemin de route parent).

```jsx
<Route path="/about/offers">
  <Offers />
</Route>
```

### Routes imbriquées dynamiques

```jsx
<Route path={`${variable}/offers`}>
  <Offers />
</Route>
```

### Liens vers des routes

Vous pouvez créer des liens vers des routes via le composant `Link`.

Importez le composant `Link`.

```js
import { Link } from "react-router-dom";
```

Utilisez le composant avec la propriété `to` pour définir une route.

```jsx
<nav>
  <Link to="/">Home</Link>
  <Link to="/about">About</Link>
  <Link to="/products">Products</Link>
</nav>
```

### Redirections

Utilisez le composant `Redirect` pour rediriger une route vers une autre.

```jsx
import { Redirect } from "react-router-dom";

<Route path="/redirect">
  <Redirect to="/about" />
</Route>;
```

Utilisez la fonction `useHistory` pour rediriger vers une route.

```jsx
import { useHistory } from 'react-router-dom';

...

const history = useHistory();

...

<button onClick={() => {history.push('/route')}}>cliquez ici</button>
```

### Changement avec la version 6

La version 6 de React Router a apporté des changements qui ne sont plus compatibles avec les versions précédentes.

Installez la version 6.

```
npm install react-router-dom@6
```

Le composant `Switch` n'existe plus. Remplacez-le par le composant `Routes`.

```jsx
import { BrowserRouter, Routes } from "react-router-dom";

<BrowserRouter>
  <Routes></Routes>
</BrowserRouter>;
```

Le composant `Route` n'accepte plus de composant imbriqué et la propriété `component` n'existe plus. Une nouvelle propriété `element` vous permet de passer le composant à afficher. Ce dernier doit être utilisé comme une balise.

```jsx
<Route path="/" element={<Home />} />
<Route path="/about" element={<About />} />
<Route path="/products" element={<Products />} />
```

**Remarque :** La route avec le chemin racine `/` n'a plus besoin de préciser la propriété `exact`.

```js
<Route path="/" element={<Home />} />
```

Vous pouvez désormais insérer une structure de composants dans une route.

```jsx
<Route
  path="/test"
  element={
    <div>
      <Composant />
      <p>Texte</p>
    </div>
  }
/>
```

Le composant `Redirect` n'existe plus. Utilisez le composant `Navigate` à la place.

```jsx
import { Navigate } from "react-router-dom";

<Route path="/redirect" element={<Navigate to="/about" />} />;
```

Vous pouvez également utiliser une redirection conditionnelle.

```jsx
<Route
  path="/checkout"
  element={condition ? <Navigate to="/route1" /> : <Navigate to="/route2" />}
/>
```

La fonction `useHistory` n'est plus définie. Utilisez la fonction `useNavigate` à la place.

```jsx
import { useNavigate } from 'react-router-dom';

...

const navigate = useNavigate();

...

<button onClick={() => {navigate('/route')}}>cliquez ici</button>
```

Pour une route imbriquée, commencez par ajouter un caractère `*` au chemin de la route parent.

```jsx
<Route path="/about/*" element={<About />} />
```

Encadrez la route imbriquée du composant `Routes` et utilisez un chemin relatif à la route parent.

```jsx
<Routes>
  <Route path="/offers" element={<Offers />} />
</Routes>
```

**Remarque :** Cela fonctionne également pour les routes imbriquées dynamiques. La route parent dynamique n'apparait que dans le composant parent.
