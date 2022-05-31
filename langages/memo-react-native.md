# Mémo React Native

_par flashjaysan_

## Introduction

Utilise React pour créer des applications mobiles (Android et iOS).

Crée une application via un arbre de composants. On passe des données aux composants via des _props_ (properties).

## Prérequis

- JavaScript
- ES6
- React
- React hooks et contexts

## Installation

Installez VS Code.

Installez l'extension ES7 React/Redux/GraphQL/React-Native snippets pour VS Code.

Expo CLI ou React Native CLI ?

Expo CLI est plus simple pour les débutants. Propose un projet prêt à l'emploi.

React Native CLI demande plus de configuration au démarrage mais propose un projet de départ plus _pure_.

Installez NodeJS.

Lancez VS Code.

Ouvrez un terminal.

Installez Expo CLI.

```
npm install expo-cli --global
```

## Créer un projet

Placez vous dans le dossier où vous souhaitez créer le projet.

```
expo init nom-projet
```

Choisissez l'option `blank`.

Saisissez le nom du projet et validez.

## Démarrer le projet

Positionnez vous dans le dossier du projet.

```
cd nom-projet
```

Ouvrez VS Code.

```
code .
```

Ouvrez un terminal VS Code.

Lancez le projet.

```
npm start
```

## Tester l'application

Emulateur

Mobile physique

Navigateur

[A REDIGER]

## Point d'entrée

Le composant `App` est le composant racine de l'application.

```js
import React from 'react';
import { StyleSheet, Text, View } from 'react-native';

export default function App() {
  return (
    <View style={styles.container}>
      <Text>Open up App.js to start working on your app!</Text>
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
    alignItems: 'center',
    justifyContent: 'center',
  },
});
```

## Styles

Les composants acceptent une propriété appelé `style` pour contrôler leur apparence. Utilisez l'objet `StyleSheet` et sa méthode `create` pour définir des styles similaires à des CSS. Passez à cette méthode un objet JavaScript.

**Remarque :** Contrairement aux CSS où on utilise des propriétés CSS en séparant les mots par un tiret (`justify-content`), ici, on utilise la convention `camelCase` (`justifyContent`).

Les styles ne sont pas automatiquement hérités par les composants enfants.

## Composants standards

### View

Le composant `View` permet de créer des subdivisions (comme la balise `div` en HTML). Ce composant accepte la propriété `style`.

```js
import { View } from 'react-native';

export default function Composant() {
  return (
    <View></View>
  );
}
```

### ScrollView

Le composant `View` n'est pas scrollable. Si son contenu sort de l'écran, on ne peut pas le faire défiler. Utilisez le composant `ScrollView` si vous souhaitez permettre le défilement.

```js
import { ScrollView } from 'react-native';

export default function Composant() {
  return (
    <ScrollView></ScrollView>
  );
}
```

**Attention !** Le composant `ScrollView` affiche tout son contenu y compris le contenu en dehors de l'écran. Pour améliorer les performances avec des listes, utilisez le composant `FlatList`.

### Text

Le composant `Text` permet d'afficher du texte. Ce composant accepte la propriété `style`.

```js
import { Text } from 'react-native';

export default function Composant() {
  return (
    <Text>Texte à afficher.</Text>
  );
}
```

### TextInput

Le composant `TextInput` permet d'afficher une zone de saisie de texte.

**Remarque :** Ce composant n'a pas de balise fermante. Passez lui des informations via ses propriétés.

```js
import { TextInput } from 'react-native';

export default function Composant() {
  return (
    <TextInput />
  );
}
```

Ce composant accepte la propriété `style`.

```js
import { TextInput, StyleSheet } from 'react-native';

export default function Composant() {
  return (
    <TextInput style={styles.textInput} />
  );
}

const styles = StyleSheet.create({
  textInput: {
    borderWidth: 1,
    borderColor: '#777'
    padding: 8,
    margin: 10,
    width: 200,
  }
});
```

La propriété `placeholder` vous permet de donner une valeur affichée lorsque l'utilisateur n'a rien saisi.

```js
<TextInput placeholder="texte" />
```

La propriété `onChangeText` vous permet de définir la fonction à appeler lorsque l'utilisateur saisit du texte. Cette fonction prend un paramètre contenant la chaine saisie.

```js
const textInputChangeHandler = (input) => {};

...

<TextInput onChangeText={textInputChangeHandler} />
```

**Remarque :** On utilise généralement un état dans la fonction qui gère l'évènement pour indiquer à React que l'application doit rafraichir son rendu.

La propriété `multiline` vous permet d'indiquer que le champ de saisie accepte plusieurs lignes de texte.

```js
<TextInput multiline />
```

La propriété `keyboardType` vous permet d'indiquer le type de clavier virtuel à afficher pour la saisie. Utilisez l'une des chaines suivantes :

- `default` : clavier standard (valeur par défaut).
- `number-pad` : pavé numérique.
- `decimal-pad` : pavé numérique.
- `numeric` : pavé numérique.
- `email-address` : clavier facilitant la saisie d'adresses e-mail.
- `phone-pad` : pavé de téléphone.
- `url` : clavier facilitant la saisie d'adresses web.

Spécifique à iOS :

- `ascii-capable` : .
- `numbers-and-punctuation` : .
- `name-phone-pad` : .
- `twitter` : .
- `web-search` : .

Spécifique à Android :

- `visible-password` : .

```js
<TextInput keyboardType="numeric" />
```

#### Masquer le clavier virtuel

Importez le composant `TouchableWithoutFeedback`.

```js
import { TouchableWithoutFeedback } from 'react-native';
```

Englobez toute l'application dans un composant `TouchableWithoutFeedback`.

```js
<TouchableWithoutFeedback>
  ...
</TouchableWithoutFeedback>
```

Utilisez la propriété `onPress` pour gérer l'interaction utilisateur partout dans l'écran.

```js
<TouchableWithoutFeedback onPress={() => {}}>
  ...
</TouchableWithoutFeedback>
```

Importer la classe `Keyboard`.

```js
import { Keyboard } from 'react-native';
```

Appelez la méthode `dismiss` dans la fonction de rappel de l'évènement `onPress` du composant `TouchableWithoutFeedback`.

```js
<TouchableWithoutFeedback onPress={() => {
  Keyboard.dismiss();
}}>
  ...
</TouchableWithoutFeedback>
```

### Bouton

Le composant `Button` vous permet de créer un widget de type bouton cliquable.

**Remarque :** Ce composant n'a pas de balise fermante. Passez lui des informations via ses propriétés.

```js
import { Button } from 'react-native';

export default function Composant() {
  return (
    <Button />
  );
}
```

La propriété `title` vous permet de définir le texte à afficher dans le bouton.

```js
<Button title="texte du bouton" />
```

La propriété `onPress` vous permet de définir la fonction à appeler lorsque l'utilisateur clique sur le bouton.

```js
const clickHandler = () => {};

...

<Button onPress={clickHandler} />
```

**Remarque :** On utilise généralement un état dans la fonction qui gère l'évènement pour indiquer à React que l'application doit rafraichir son rendu.

Ce composant n'accepte pas de propriété `style`. Pour lui donner un style, placez ce composant dans un composant `View`.

```js
<View style={styles.buttonContainer}>
  <Button />
</View>
```

### Listes

Pour gérer une liste de composants, vous devez définir une structure dont chaque élément est identifiable de manière unique via un identificateur.

```js
import { useState } from 'react';

const [people, setPeople] = useState([
  { name: 'Marc', key: '1' },
  { name: 'David', key: '2' },
  { name: 'Paul', key: '3' },
  { name: 'Franck', key: '4' },
  { name: 'Eddy', key: '5' },
]);
```

Utilisez la fonction `map` appliquable sur les tableaux.

```js
<View>
  { people.map((person) => {
    return (
      <View key={person.key}>
        <Text>{person.name}</Text>
      </View>
    );
  }) }
</View>
```

### FlatList

Le composant `View` ne permet pas le défilement en cas de contenu trop important pour l'écran. Vous pouvez tiliser le composant `ScrollView` pour permettre le défilement mais ce dernier génère le rendu pour tous les composants, y compris ceux en dehors de l'écran. Dans le cas de listes de composants, il est préférable d'utiliser le composant `FlatList`.

**Remarque :** Ce composant n'a pas de balise fermante. Passez lui des informations via ses propriétés.

```js
import { FlatList } from 'react-native';

<FlatList />
```

La propriété `data` vous permet de définir la donnée à utiliser pour itérer sur ses éléments. Utilisez de préférence une propriété `key` pour chaque élement de donnée.

```js
import { useState } from 'react';

const [people, setPeople] = useState([
  { name: 'Marc', key: '1' },
  { name: 'David', key: '2' },
  { name: 'Paul', key: '3' },
  { name: 'Franck', key: '4' },
  { name: 'Eddy', key: '5' },
]);
```

```js
<FlatList data={people} />
```

La propriété `renderItem` vous permet de définir ce que le composant doit générer pour chaque élément de la donnée.

```js
FlatList data={people} renderItem={({ item }) => (
  <Text>{item.name}</Text>
)} />
```

**Attention !** On déstructure l'`item` dans la fonction de rappel car l'objet utilisé ne contient pas seulement une ligne de la donnée source.

**Remarque :** Dans le cas où les éléments n'ont pas de propriété `key`, utilisez la propriété `keyExtractor` du composant `FlatList`. Donnez à cette propriété une fonction renvoyant une clé unique pour chaque élément.

```js
import { useState } from 'react';

const [people, setPeople] = useState([
  { name: 'Marc', id: '1' },
  { name: 'David', id: '2' },
  { name: 'Paul', id: '3' },
  { name: 'Franck', id: '4' },
  { name: 'Eddy', id: '5' },
]);
```

```js
<FlatList data={people} keyExtractor={(item) => item.id} />
```

La propriété `numColumns` vous permet de définir le nombre de colonnes à utiliser pour afficher les éléments.

```js
<FlatList numColumns={2} />
```

### TouchableOpacity

Le composant `TouchableOpacity` vous permet d'ajouter un évènement `onPress` sur un composant non touchable.

```js
import { TouchableOpacity } from 'react-native';
```

**Remarque :** Il existe une multitude de composants `Touchable`. Le composant `TouchableOpacity` rend le composant semi transparent lorqu'il est touché par l'utilisateur.

Encadrez le composant à rendre touchable avec le composant `TouchableOpacity`.

```js
<TouchableOpacity>
  <Text>Texte</Text>
</TouchableOpacity>
```

La propriété `onPress` vous permet de définir la fonction à appeler lorsque l'utilisateur touche le composant.

```js
<TouchableOpacity onPress={() => {}}>
  <Text>Texte</Text>
</TouchableOpacity>
```

## Utiliser les états

```js
import React, { useState } from 'react';
import { View, Text, Button } from 'react-native';

export default function Composant() {
  const [name, setName] = useState(valeur_initiale);

  return (
    <View>
      <Text>My name is {name}.</Text>
      <Button />
    </View>
  );
}
```

Utilisez la fonction `setName` pour modifier l'état et indiquer à React de relancer un rendu.

```js
setName(nouvelle_valeur);
```

Lorsqu'on souhaite modifier l'état en utilisant l'état courant, il faut passer par une fonction de rappel.

```js
setName((previousName) => return previousName.filter((item) => {item.id != id;}));
```

## Alert

Pour afficher un message d'avertissement, importez la classe `Alert`.

```js
import { Alert } from 'react-native';
```

Appelez la méthode `alert`. Elle prend en paramètre le titre de l'avertissement, le message de l'avertissement et un tableau d'objets. Ce dernier contient des objets ayant une propriété `text` (correspondant à l'intitulé du bouton de fermeture de la fenêtre d'avertissement) et un nom d'évènement.

```js
Alert.alert('titre', 'message', [
  {text: 'Understood', onPress: () => console.log('alert closed')}
]);
```

## Astuces

### Prendre en compte la barre de statut

Sur iOS, utilisez le composant `SafeAreaView` pour définir une vue en dehors de la barre de statut. Sur Android, ce composant est considéré comme un composant `View`. Cependant, vous pouvez vérifier sur quel environnement l'application s'exécute et prévoir une règle CSS pour décaler la vue générale uniquement sur Android (via la propriété CSS `paddingTop`). Pour déterminer la hauteur de la barre de statut, utilisez les constantes définies dans `expo-constants`.

```js
import { SafeAreaView, StyleSheet } from "react-native";
import Constants from "expo-constants";

const Screen = () => {
  return (
    <SafeAreaView style={styles.screen}>
      
    </SafeAreaView>
  );
};

const styles = StyleSheet.create({
  screen: {
    paddingTop: Constants.statusBarHeight,
    flex: 1,
  },
});

export default Screen;
```
