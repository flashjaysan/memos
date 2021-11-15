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

Utilisez le mot clé `var` pour indiquer que la variable est automatiquement du type de la valeur d'initialisation.

```dart
var uneVariable = expression; // L'expression détermine le type de la variable
```

**Conseil :** Il est recommandé d'utiliser l'inférence de type plutôt que la spécification explicite de type.

Si vous voulez une variable ayant un type dynamique, donnez-lui le type `Object` ou `dynamic`.

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

```dart
if (year >= 2001) {
  print('21st century');
} else if (year >= 1901) {
  print('20th century');
}

for (final object in flybyObjects) {
  print(object);
}

for (int month = 1; month <= 12; month++) {
  print(month);
}

while (year < 2016) {
  year += 1;
}

int fibonacci(int n) {
  if (n == 0 || n == 1) return n;
  return fibonacci(n - 1) + fibonacci(n - 2);
}

var result = fibonacci(20);

flybyObjects.where((name) => name.contains('turn')).forEach(print);
```



