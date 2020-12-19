# Mémo JUnit

par *flashjaysan*

## Liens

[JUnit avec Maven](https://github.com/junit-team/junit5-samples/tree/r5.6.0/junit5-jupiter-starter-maven)

## Structure d'un projet

- A la racine du projet, le fichier `pom.xml` définit les dépendances et leurs versions.
- Les classes de l'application se placent dans le dossier `src/main/java`.
- Les classes de test se placent dans le dossier `src/test/java`. En général, on utilise le même nom que la classe de l'application à tester suivi de `Tests`. Vous pouvez également regrouper plusieurs tests sur des classes différentes dans une seule classe de test si nécessaire.

## Dépendances

Voici un exemple de fichier `pom.xml` gérant les dépendances dans Maven :

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
		 xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>

	<groupId>com.example</groupId>
	<artifactId>junit5-jupiter-starter-maven</artifactId>
	<version>1.0-SNAPSHOT</version>

	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<maven.compiler.source>1.8</maven.compiler.source>
		<maven.compiler.target>${maven.compiler.source}</maven.compiler.target>
		<junit.jupiter.version>5.6.0</junit.jupiter.version>
	</properties>

	<dependencies>
		<dependency>
			<groupId>org.junit.jupiter</groupId>
			<artifactId>junit-jupiter</artifactId>
			<version>${junit.jupiter.version}</version>
			<scope>test</scope>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.8.1</version>
			</plugin>
			<plugin>
				<artifactId>maven-surefire-plugin</artifactId>
				<version>2.22.2</version>
			</plugin>
		</plugins>
	</build>
</project>
```

## Annotations

Consultez le lien suivant sur les [annotations](https://junit.org/junit5/docs/current/user-guide/#writing-tests-annotations).

- Avant la définition de la classe de test, ajoutez l'annotation `@Testable`.
- Avant une définition de méthode de test, ajoutez l'annotation `@Test` pour indiquer que la méthode est une méthode de test.
- Les annotation `@BeforeAll`, `@AfterAll`, `@BeforeEach` et `@AfterEach` permettent de contrôler plus finement l'ordre des tests. 

Pour que Maven exécute les tests automatiquement, faites commencer vos noms de méthode de test par `test`.

## Assertions

Utilisez les assertions pour tester le bon fonctionnement.

- `assertNull` contrôle si le premier paramètre est égal à `null`. Si ce n'est pas le cas (si le paramètre est différent de `null`), cela lève une exception avec la chaîne passée en second paramètre.
- `assertNotNull` contrôle si le premier paramètre est différent de `null`. Si ce n'est pas le cas (si le paramètre est égal à `null`), cela lève une exception avec la chaîne passée en second paramètre.
- `assertTrue` contrôle si le premier paramètre est égal à `true`. Si ce n'est pas le cas, cela lève une exception avec la chaîne passée en second paramètre.
- `assertEquals` contrôle si le premier paramètre est égal au deuxième paramètre. Si ce n'est pas le cas, cela lève une exception avec la chaîne passée en second paramètre.




