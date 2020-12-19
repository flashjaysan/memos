# Mémo Eclipse

par *flashjaysan*

## Importer un projet Git dans Eclipse

- Dans Eclipse, cliquez sur le menu `File -> Import...`.
- Dans la boîte de dialogue `Import`, sélectionnez `Git -> Projects from Git` puis cliquez sur `Next`.
- Dans la boîte de dialogue `Import Projects from Git`, Sélectionnez `Clone URI` puis cliquez sur `Next`.
- Collez l'adresse du projet Git dans le champ `URI` puis cliquez sur `Next`.
- Cochez la branche à cloner (`master`) puis cliquez sur `Next`.
- Dans le champ `Directory`, définissez un dossier vide. Vérifiez que le champ `Remote name` fasse bien référence au bon projet puis cliquez sur `Next`.
- Sélectionnez l'option `Import as general project` puis cliquez sur `Next`.
- Dans le champ `Project name`, définissez le nom du projet puis cliquez sur `Finish`.

## Mettre à jour le projet stocké sur Git

- Dans le panneau `Package Explorer`, faites un clic droit sur la racine du projet puis sélectionnez `Team -> Pull`.
- Si nécessaire, saisissez votre identifiant de connexion et votre mot de passe puis validez.

## Définir la nature d'un projet Maven

- Dans le panneau `Package Explorer`, faites un clic droit sur la racine du projet puis sélectionnez `Properties`.
- Dans la boîte de dialogue `Properties for nom_du_projet`, sélectionnez l'option `Project Natures`.
- Cliquez sur le bouton `Add`.
- Si la boîte de dialogue `Confirm nature update` apparaît, cliquez sur le bouton `OK`.
- Dans la boîte de dialogue `Select Nature`, sélectionnez l'option `Maven Nature` puis cliquez sur le bouton `OK`.
- Cliquez sur le bouton `Apply and close`.
- Dans le panneau `Package Explorer`, faites un clic droit sur la racine du projet puis sélectionnez `Maven -> Update Project...`.
- Dans la boîte de dialogue `Update Maven Project`, cochez le projet à mettre à jour puis cliquez sur `OK`.
- Dans le panneau `Package Explorer`, faites un clic droit sur la racine du projet puis sélectionnez `Run As -> Maven Install`.

**Attention !** Pour fonctionner, le projet autour de *JDBC-JAXB* de Martin nécessite d'éditer le fichier `db-products.properties` dans le dossier `src/main/resources`.

- Les propriétés `database` et `user` sont identiques et correspondent à votre identifiant.
- La propriété `password` correspond à votre mot de passe.
- Sauvegardez ce fichier et refaites un `Maven Install`.

## Importer automatiquement les classes

Dans l'éditeur, pointez le curseur de la souris sur une classe pour faire apparaître le tooltip d'Eclipse. Cliquez sur l'option `Import 'NomDeClasse' (nom.de.package)`.

## Ouvrir la définition d'un élément

Dans l'éditeur, faites un CTRL + clic sur un élément pour ouvrir le fichier source contenant sa définition.

Dans le panneau `Package Explorer`, cliquez sur le bouton `double flèche` (`Link with Editor`) pour afficher l'arborescence de fichiers sources où se trouve le fichier.

## Forcer la console à afficher la totalité d'un log

- Cliquez sur le menu `Window -> Preferences`.
- Dans la section `Run/Debug -> Console`, décochez `Limit console output`.
- Cliquez sur `Apply and Close`.

## Utiliser MySQL avec JDBC

Dans le fichier pom.xml de votre projet Maven, ajoutez la dépendance au driver MySQL :

```java
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.18</version>
</dependency>
```

Le code suivant permet d'obtenir une connection à la base de donnée MySQL appelée `gestion` :

```java
String databaseName = "gestion";
java.sql.Connection connection = java.sql.DriverManager.getConnection("jdbc:mysql://localhost:3306/" + databaseName, 
user, password);
```

**Remarque :** Si vous avez le message `The server time zone value 'Paris, Madrid' is unrecognized or represents more than one time zone. You must configure either the server or JDBC driver (via the serverTimezone configuration property) to use a more specifc time zone value if you want to utilize time zone support.` dans la console, ajoutez la chaîne `"?useLegacyDatetimeCode=false&serverTimezone=UTC"` après le nom de la base de donnée dans votre adresse de connexion.

```java
String databaseName = "gestion";
java.sql.Connection connection = java.sql.DriverManager.getConnection("jdbc:mysql://localhost:3306/" + databaseName + "?useLegacyDatetimeCode=false&serverTimezone=UTC", 
user, password);
```
