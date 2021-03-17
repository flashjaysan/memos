Mémo TypeScript

*par flashjaysan*

# Installation

Rendez-vous sur [le site officiel dédié à TypeScript](https://www.typescriptlang.org/) et installez les outils.

## Exemple d'installation

Installez [NodeJS](https://nodejs.org/fr/).

Ouvrez une Invite de commande.

Saisissez `npm install -g typescript`.

Saisissez `tsc`. Si la commande est reconnue, TypeScript est installé.

## Compiler un fichier TypeScript

```
tsc nom_du_fichier.ts
```

## Types de base

```ts
let variableQuelconque: any;
let nombre: number; // 5, 5.2, -5
let chaine: string; // "Dupont", 'Durand', `Duchemin`
let booleen: boolean; // true, false

let tableauDeValeurs: any[]; // [5, 'Dupont', true]
let tableauDeNombres: number[]; // [5, -5]
let tableauDeChaines: string[]; // ['Dupont', 'Durand']
let tableauDeBooleens: boolean[]; // [true, false]
```

## Type par inférence

```ts
const cinq = 5; // type number
const dupont = 'Dupont'; // type string
const vrai = true; // type boolean
```

## Type des objets

```ts
const objet = {
    nom: 'Dupond',
    age: 25
}
```

`objet` est de type `{nom: string; age:number;}`. Vous pouvez définir le type explicitement.

```ts
const objet: {
    nom: string;
    age:number;
    } = {
    nom: 'Dupond',
    age: 25
}
```

```ts
let objet1: object;
let objet2: {};
```

`objet1` et `objet2` sont de type `object`. Similaire aux objets JavaScript.

## Tuples

Un tuple est un tableau de dimension et de types fixes. Vous devez déclarer le type explicitement.

```ts
let tupleNombreChaine: [number, string]; // [5, 'Dupont']
```

Le premier élément est obligatoirement de type `number` et le second élément obligatoirement de type `string`.

## Unions

Un type union permet de limiter une variable à un certain nombre de types différents.

```ts
let variable: number | string; // 5 ou 'Dupont'
```

## Enumérations

```ts
enum NomEnumeration {
    VALEUR1, // 0
    VALEUR2, // 1
    VALEUR3 = 30,
    VALEUR4 // 31
}

const valeur: NomEnumeration = NomEnumeration.VALEUR1;
```

## Fonctions

```ts
function add(nombre1: number, nombre2: number): number {
    return nombre1 + nombre2;
}
```
