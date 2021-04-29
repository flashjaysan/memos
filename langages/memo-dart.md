# Mémo Dart

*par flashjaysan*

## Introduction



## Syntaxe

### Commentaires

```dart
// commentaire sur une ligne

/*
commentaire sur
plusieurs lignes
*/

/// commentaire de documentation sur une ligne

/**
commentaire de documentation
sur plusieurs lignes
*/
```

Les commentaires peuvent s'inbriquer.

### Types

Tous les types sont des objets, même les types primitifs.

### Types primitifs

```dart
bool booleen = true; // ou false
int entier = 0; // entier 64 bits
double nombreAVirgule = 0.0; // norme IEEE 754
```

Les types `int` et `double` héritent du type `num` (`dart:core`).

### Inférence de type

```dart
var uneVariable = expression; // L'expression détermine le type de la variable
```

**Conseil :** Il est recommandé d'utiliser l'inférence de type plutôt que la spécification explicite de type.

Si vous voulez une variable ayant un type dynamique, donnez-lui le type `Object` ou le `dynamic`.

```dart
Object uneVariable = 'Bonjour !';
uneVariable = 5;
```

## Valeurs par défaut

Une variable non initialisée a la valeur `null` sauf si son type .

## Point d'entrée

```dart
void main() {

}
```

## Afficher du texte

```dart
print('Hello, world!');
```

## Assertions

Utilisez la fonction `assert` pour tester si une condition est remplie. Si ce n'est pas le cas, une erreur est déclenchée.

```dart
assert(condition);
```





