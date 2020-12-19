# Mémo SQL

par *flashjaysan*

## Voir les bases de données

Propre à *MySQL*.

```sql
SHOW DATABASES;
```

## Gestion de base de données

### Créer une base de donnée

```sql
CREATE DATABASE nomDeBaseDeDonnee;
```

### Supprimer une base de donnée

```sql
DROP DATABASE nomDeBaseDeDonnee;
```

### Sélectionner une base de donnée à utiliser

```sql
USE nomDeBaseDeDonnee;
```

## Gestion des tables d'une base de données

### Voir les tables de la base de donnée en cours d'utilisation

Propre à *MySQL*.

```sql
SHOW TABLES;
```

### Créer une nouvelle table

```sql
CREATE TABLE nomDeTable (
    nomDeColonne TYPE NOT NULL,
    nomDeColonne TYPE NOT NULL,
    ...
    nomDeColonne TYPE,
    PRIMARY KEY (nomDeColonne),
    FOREIGN KEY(nomDeColonne) REFERENCES nomDeTable(nomDeColonne)
);
```

Exemple :

```sql
CREATE TABLE products (
	id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(30),
    price DECIMAL(3,2)
);

CREATE TABLE customers (
	id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(30),
    last_name VARCHAR(30),
    gender ENUM('M','F'),
    phone_number VARCHAR(11)
);

CREATE TABLE orders (
	id INT AUTO_INCREMENT PRIMARY KEY,
    product_id INT,
    customer_id INT,
    order_time DATETIME,
    FOREIGN KEY(product_id) REFERENCES products(id),
    FOREIGN KEY(customer_id) REFERENCES customers(id)
);
```

**Attention !** N'oubliez pas le point virgule terminal.

Les types autorisés les plus communs sont :

- `BOOLEAN` : un booléen `True` ou `False`.
- `INT` : un entier relatif.
- `FLOAT(M,D)` : valeur approchée d'un nombre décimal à virgule. `M` correspond au nombre de chiffres. `D` correspond au nombre de chiffres après la virgule.
- `DECIMAL(M,D)` : valeur exacte d'un nombre décimal à virgule. `M` correspond au nombre de chiffres. `D` correspond au nombre de chiffres après la virgule.
- `CHAR(N)` : suite de caractères (de longueur fixe).
- `VARCHAR(N)` : suite de caractères (de longueur variable).
- `ENUM('M','F')` : une énumération.
- `DATE` : une date `(AAAA-MM-JJ)`.
- `DATETIME` : une date et une heure `(AAAA-MM-JJ HH-MM-SS)`.
- `TIME` : une heure `(HHH-MM-SS)`.
- `YEAR` : une année `(AAAA)`.

Les littéraux de chaînes de caractères sont écrits entre apostrophes. Pour insérer une apostrophe, doublez-la.

**Remarque :** Pour une valeur représentant un prix, utilisez plutôt le type `DECIMAL`.

#### Clé primaire (*primary key*)

Une clé primaire est une valeur unique identifiant un enregistrement précis dans une table. Elle ne peut pas être nulle. Une table n'a qu'une seule clé primaire.

```sql
CREATE TABLE nomDeTable (
	nomDeChamp type PRIMARY KEY
);
```

ou

```sql
CREATE TABLE nomDeTable (
	nomDeColonne type,
    PRIMARY KEY (nomDeColonne)
);
```

Exemple :

```sql
CREATE TABLE products (
	id INT PRIMARY KEY
);
```

#### Clé étrangère (*foreign key*)

Une clé étrangère dans une table est une valeur correspondant à la clé primaire d'une autre table. Une clé étrangère est utilisée pour relier deux tables différentes. La table avec la clé primaire est appelée table référence (ou parent) et la table avec la clé étrangère est appelée la table enfant. Une valeur d'une clé étrangère fait référence à une valeur d'une clé primaire d'une autre table. Une table peut avoir plusieurs clés étrangères.

```sql
FOREIGN KEY(nomDeColonne) REFERENCES nomDeTable(nomDeClePrimaire)
```

Exemple :

```sql
CREATE TABLE orders (
	id INT AUTO_INCREMENT PRIMARY KEY,
    product_id INT,
    customer_id INT,
    FOREIGN KEY(product_id) REFERENCES products(id),
    FOREIGN KEY(customer_id) REFERENCES customers(id)
);
```

### Ajouter une colonne dans une table

```sql
ALTER TABLE nomDeTable ADD COLUMN nomDeColonne type;
```

### Renommer une colonne d'une table

```sql
ALTER TABLE nomDeTable CHANGE `anCienNomDeColonne` `nouveauNomDeColonne` type;
```

Exemple :

```sql
CREATE TABLE products (
	id INT PRIMARY KEY,
    name VARCHAR(30)
);

ALTER TABLE products CHANGE `name` `item` VARCHAR(30);
```

### Modifier le type d'une colonne d'une table

```sql
ALTER TABLE nomDeTable MODIFY nomDeColonne type;
```

Exemple :

```sql
CREATE TABLE products (
	id INT PRIMARY KEY,
    name VARCHAR(30)
);

ALTER TABLE products MODIFY name VARCHAR(50);
```

**Attention !** Changer le type d'une colonne ne peut être effectué si la table possède des enregistrements et que les données contenues dans la colonnes sont incompatibles avec le nouveau type.

### Supprimer une colonne d'une table

```sql
ALTER TABLE nomDeTable DROP COLUMN nomDeColonne;
```

### Supprimer une table

```sql
DROM TABLE nomDeTable;
```

### Supprimer tous les enregistrements d'une table

```sql
TRUNCATE TABLE nomDeTable;
```

### Définir une colonne en tant que clé primaire dans une table

```sql
ALTER TABLE nomDeTable ADD PRIMARY KEY (nomDeColonne);
```

### Supprimer la clé primaire d'une table

```sql
ALTER TABLE nomDeTable DROP PRIMARY KEY;
```

### Définir une colonne en tant que clé secondaire dans une table

```sql
ALTER TABLE nomDeTable ADD CONSTRAINT nomDeContrainte FOREIGN KEY nomDeColonne REFERENCES nomDeTable(nomDeColonne);
```

Exemple :

```sql
CREATE TABLE products (
	id INT AUTO_INCREMENT PRIMARY KEY
);

CREATE TABLE customers (
	id INT AUTO_INCREMENT PRIMARY KEY
);

CREATE TABLE orders (
	id INT AUTO_INCREMENT PRIMARY KEY,
    product_id INT,
    customer_id INT
);

ALTER TABLE orders ADD CONSTRAINT FK_products_id FOREIGN KEY product_id REFERENCES products(id);
ALTER TABLE orders ADD CONSTRAINT FK_customers_id FOREIGN KEY customer_id REFERENCES customers(id);
```

### Supprimer une clé secondaire d'une table

```sql
ALTER TABLE nomDeTable DROP FOREIGN KEY nomDeContrainte;
```

Exemple :

```sql
ALTER TABLE orders ADD DROP FOREIGN KEY FK_products_id;
ALTER TABLE orders ADD DROP FOREIGN KEY FK_customers_id;
```

### Contraintes

#### Valeurs uniques

Pour forcer une colonne à avoir une valeur unique pour chaque enregistrement :

```sql
ALTER TABLE nomDeTable ADD CONSTRAINT nomDeContrainte UNIQUE (nomDeColonne);
```

#### Supprimer une contrainte

```sql
ALTER TABLE nomDeTable DROP INDEX nomDeContrainte;
```

## Gestion des données

### Insérer un enregistrement dans une table

```sql
INSERT INTO nomDeTable(nomDeColonne1, nomDeColonne2, ..., nomDeColonneN) VALUES (valeur1, valeur2, ..., valeurN);
```

**Remarque :** Vous pouvez passer plusieurs groupes de valeurs en les séparant par une virgule.

Exemple :

```sql
INSERT INTO products (name, price, coffee_origin) VALUES ('Espresso', 2.50, 'Brasil');
INSERT INTO products (name, price, coffee_origin) VALUES ('Macchiato', 3.00, 'Brasil'), ('Cappuccino', 3.50, 'Costa Rica');
```

### Supprimer un enregistrement d'une table

```sql
DELETE FROM nomDeTable WHERE condition;
DELETE FROM nomDeTable WHERE nomDeColonne = valeur;
```

**Remarque :** Vous pouvez supprimer tous les enregistrements en omettant la clause `WHERE` :

```sql
DELETE FROM nomDeTable;
```

### Modifier un enregistrement d'une table

```sql
UPDATE nomDeTable SET nomDeColonne = valeur WHERE condition;
UPDATE nomDeTable SET nomDeColonne = valeur WHERE nomDeColonne = valeur;
```

Exemple :

```sql
UPDATE products SET coffee_origin = 'Sri Lanka' WHERE id = 7;
```

Vous pouvez modifier deux colonnes à la fois en les séparant par une virgule.

```sql
UPDATE nomDeTable SET nomDeColonne = valeur, nomDeColonne = valeur WHERE condition;
UPDATE nomDeTable SET nomDeColonne = valeur, nomDeColonne = valeur WHERE nomDeColonne = valeur;
```

**Remarque :** *MySQL* impose par défaut que la condition porte sur la clé primaire. Pour outrepasser cette limitation, utilisez la commande :

```sql
SET SQL_SAFE_UPDATES=0;
UPDATE products SET price = 3.25, coffee_origin = 'Ethiopia' WHERE name = 'Americano';
```

### Consulter le contenu complet d'un table

```sql
DESCRIBE nomDeTable;
```

ou

```sql
DESC nomDeTable;
```

## Sélection des données dans une table

### Sélectionner toutes les colonnes

```sql
SELECT * FROM nomDeTable;
```
### Sélectionner une ou plusieurs colonnes


```sql
SELECT nomDeColonne FROM nomDeTable;
```

```sql
SELECT nomDeColonne, nomDeColonne FROM nomDeTable;
```

### Sélectionner des données répondant à une ou des condition(s)

```sql
SELECT * FROM nomDeTable WHERE condition;
```

```sql
SELECT nomDeColonne FROM nomDeTable WHERE condition;
```

Vous pouvez utiliser :

- l'opérateur d'addition `+`.
- l'opérateur de soustraction `-`.
- l'opérateur de multiplication `*`.
- l'opérateur de division `/`.
- l'opérateur de reste `%`.
- l'opérateur d'égalité `=`.
- l'opérateur de différence `<>` (certaines bases de données prennent en charge l'opérateur `!=` mais ce n'est pas standard).
- l'opérateur inférieur `<`.
- l'opérateur inférieur ou égal `<=`.
- l'opérateur supérieur `>`.
- l'opérateur supérieur ou égal `>=`.
- l'opérateur de négation `NOT`.
- l'opérateur ET logique `AND`.
- l'opérateur OU logique `OR`.

Pour vérifier si une valeur dans une colonne est nulle ou non, une syntaxe particulière est nécessaire.

```sql
SELECT nomDeColonne FROM nomDeTable WHERE nomDeColonne IS NULL;
SELECT nomDeColonne FROM nomDeTable WHERE nomDeColonne IS NOT NULL;
```

#### Sélectionner des données dont une colonne a une valeur parmi plusieurs

```sql
SELECT * FROM nomDeTable WHERE nomDeColonne IN (valeur, valeur);
SELECT nomDeColonne FROM nomDeTable WHERE nomDeColonne IN (valeur, valeur);
SELECT * FROM nomDeTable WHERE nomDeColonne NOT IN (valeur, valeur);
SELECT nomDeColonne FROM nomDeTable WHERE nomDeColonne NOT IN (valeur, valeur);
```

#### Sélectionner des données dont une colonne a une valeur dans un intervalle

```sql
SELECT * FROM nomDeTable WHERE nomDeColonne BETWEEN valeur AND valeur;
SELECT nomDeColonne FROM nomDeTable WHERE nomDeColonne BETWEEN valeur AND valeur;
SELECT * FROM nomDeTable WHERE nomDeColonne NOT BETWEEN valeur AND valeur;
SELECT nomDeColonne FROM nomDeTable WHERE nomDeColonne NOT BETWEEN valeur AND valeur;
```
