# Mémo JavaFX

*par flashjaysan*

## Installation

- Installez Java JDK.
- Téléchargez JavaFX.
- Dézippez JavaFX à l'emplacement de votre choix.

## Configuration d'Eclipse

- Installez Eclipse.
- Créez un projet Java.
- Faites un clic droit sur le projet dans le panneau `Package Explorer` et sélectionnez l'option `Build Path -> Configure Build Path...`.
- Dans l'onglet `Libraries`, sélectionnez `Modulepath`.
- Cliquez sur le bouton `Add External JARs...`.
- Placez-vous dans le dossier `lib` où vous avez dézippé JavaFX.
- Sélectionnez tous les fichiers `.jar` et cliquez sur le bouton `Open`.
- Cliquez sur le bouton `Apply and Close`.

## Voir les sources

Importez la classe `javafx.application.Application`.

```java
import javafx.application.Application;
```

- Survolez la classe `Application` et cliquez sur la petite icône verte du tooltip.
- Cliquez sur le bouton `Attach Source...`.
- Cochez `External location`.
- Cliquez sur le bouton `External File...`.
- Placez-vous dans le dossier `lib` où vous avez dézippé JavaFX.
- Sélectionnez le fichier `src.zip` et cliquez sur le bouton `Open`.
- Cliquez sur le bouton `OK`.

## Utilisation

Créez une classe héritant de la classe `javafx.application.Application`.

```java
import javafx.application.Application;

public class HelloApplication extends Application {

}
```

**Remarque : ** Si vous utilisez un module, vous devez préciser qu'il recquiert le module `javafx.controls` ou `javafx.graphics`.

```java
module com.javafxhello {
    requires javafx.graphics;
}
```

Survolez le nom de la classe et choisissez l'option `Add unimplemented methods` pour créer automatiquement la méthode `start` à implémenter.

```java
import javafx.application.Application;
import javafx.stage.Stage;

public class HelloApplication extends Application {

	@Override
	public void start(Stage primaryStage) throws Exception {
		// TODO Auto-generated method stub
		
	}

}
```

Comme vous pouvez le voir, la méthode `start` prend un paramètre de type `Stage`. Dans JavaFX, une fenêtre est appelée `Stage`. Le paramètre `primaryStage` de la fonction `start` correspond à la fenêtre principale de l'application. Cette fenêtre principale sera générée automatiquement par JavaFX lors de l'exécution.

## Exécuter le projet

- Faites un clic droit sur le projet dans le panneau `Package Explorer`.
- Sélectionnez l'option `Run As -> Java Application`.
- Sélectionnez la classe à exécuter si besoin.

Un message d'erreur apparait.

- Faites un clic droit sur le projet dans le panneau `Package Explorer`.
- Sélectionnez l'option `Run As -> Run Configuration...`.
- A gauche, cliquez sur `Java Application`.
- Cliquez sur le bouton `New launch configuration`.
- Donnez un nom à la configuration (par exemplen, `HelloApplication`).
- Dans l'onglet `Main`, champ `Main class`, saisissez le nom complet de la classe contenant la méthode `main` (par exemple, `com.javafx.HelloApplication`).
- Cliquez sur le bouton `Apply`.

La nouvelle configuration apparaît à gauche.

- Cliquez sur le bouton `Run` pour exécuter le projet.

## Afficher la fenêtre principale

Dans la méthode `start`, appelez la méthode `show` de l'objet `primaryStage`.

```java
import javafx.application.Application;
import javafx.stage.Stage;

public class HelloApplication extends Application {

	@Override
	public void start(Stage primaryStage) throws Exception {
		primaryStage.show();
	}

}
```

## Modifier le titre de la fenêtre principale

Utilisez la méthode `setTitle` d'un objet de type `Stage`.

```java
import javafx.application.Application;
import javafx.stage.Stage;

public class HelloApplication extends Application {

	@Override
	public void start(Stage primaryStage) throws Exception {
        primaryStage.setTitle("Hello");
		primaryStage.show();
	}

}
```

## Centrer la fenêtre principale

Utilisez la méthode `centerOnScreen` après la méthode `show`.

```java
import javafx.application.Application;
import javafx.stage.Stage;

public class HelloApplication extends Application {

	@Override
	public void start(Stage primaryStage) throws Exception {
        primaryStage.setTitle("Hello");
		primaryStage.show();
        primaryStage.centerOnScreen();
	}

}
```

## Définir les dimensions de la fenêtre principale

- Utilisez la méthode `setWidth` pour définir la largeur de la fenêtre.
- Utilisez la méthode `setHeight` pour définir la hauteur de la fenêtre.

```java
import javafx.application.Application;
import javafx.stage.Stage;

public class HelloApplication extends Application {

	@Override
	public void start(Stage primaryStage) throws Exception {
        primaryStage.setTitle("Hello");
        primaryStage.setWidth(640);
        primaryStage.setHeight(360);
		primaryStage.show();
        primaryStage.centerOnScreen();
	}

}
```








