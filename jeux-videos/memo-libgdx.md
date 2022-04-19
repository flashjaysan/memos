# Mémo libGDX

par *flashjaysan*

## Prérequis

Pour suivre ce mémo, vous aurez besoin :

- D'une bonne connaissance du langage Java.
- D'un JDK Java. Il est conseillé d'utiliser un JDK Java 8. Par exemple, installer [OpenJDK](https://adoptopenjdk.net/).
- D'[Android Studio](https://developer.android.com/studio/).

## Créer un projet libGDX

Si vous deviez créer vous-même un projet libGDX, vous devriez créer un projet pour le coeur du jeu et un projet pour chaque plateforme cible sur laquelle vous souhaiteriez déployer votre projet. Vous devriez ensuite configurer ces différents projets et les lier entre eux. Cela est compliqué et fastidieux. Heureusement, les développeurs de libGDX ont créé un fichier *jar* exécutable permettant de générer un projet utilisant libGDX et le configurer automatiquement pour les différentes plateformes cibles.

- Téléchargez le générateur de projet de libGDX (fichier `gdx-setup.jar`) sur le [site officiel de libGDX](https://libgdx.badlogicgames.com/download.html).

**Attention !** Java 13 n'est pas compatible avec ce générateur de projet. J'ai pu le faire fonctionner avec Java 11 mais on m'a conseillé d'installer et d'utiliser de préférence Java 8.

- Exécutez le fichier `gdx-setup.jar`.
- Dans le *libGDX Project Setup*, saisissez les informations nécessaires :
  - Le champ `Name` correspond au nom de votre jeu.
  - Le champ `Package` correspond au package du projet.
  - Le champ `Game Class` correspond au nom de la classe racine de votre jeu.
  - Le champ `Destination` correspond à l'emplacement sur disque de votre projet.
  - Le champ `Android SDK` correspond à l'emplacement sur disque où se trouve le SDK Android.
- La section `Sub Projects` vous permet de définir sur quelles plateformes cibles vous souhaitez exporter votre jeu. Vous pouvez tout cocher ou ne cocher qu'une seule plateforme.
- La section `Extensions` vous propose d'ajouter au projet des extensions fréquemment utilisées. Vous pouvez tout décocher pour commencer.
- Cliquez sur le bouton `Generate`.

**Remarque :** Pour déterminer l'emplacement du SDK Android, vous pouvez utiliser Android Studio :

- Ouvrez Android Studio.
- Cliquez sur le menu deroulant `Configure -> SDK Manager`.
- La section `Appearance & Behavior -> System Settings -> Android SDK` indique l'emplacement du SDK Android.

## Ouvrir un projet libGDX dans Android Studio

- Sur l'écran d'accueil d'Android Studio, cliquez sur l'option `Import project (gradle, eclipse adt, etc.)`. Si un projet est déjà ouvert, cliquez sur le menu `File -> New -> Import Project...`.
- Sélectionnez le dossier contenant le projet libGDX puis cliquez sur le bouton `OK`.

## Exécuter un projet

### Windows

**Attention !** Vous devez avoir paramétré le projet en cochant `Desktop` dans la section `Sub Projects`.

#### Créer une configuration pour Windows

- Cliquez sur le menu `Run-> Edit Configurations`.
- Cliquez sur le bouton `+`.
- Sélectionnez `Application`.
- Dans le champ `Name`, saisissez `Desktop`.
- Dans le champ `Use classpath of module`, sélectionnez le dossier `desktop` (ou `desktop_main`).
- Cliquez sur le bouton `...` du champ `Main class`.
- Sélectionnez la classe `DesktopLauncher`.
- Dans le champ `Working directory`, sélectionnez le dossier `android/assets/` ou `core/assets/` du projet.
- Cliquez sur le bouton `Apply` puis sur le bouton `OK`.

## Structure d'un projet libGDX

Le code source spécifique à une plateforme se situe dans un dossier portant le nom de la plateforme. Par exemple dans les dossiers `desktop`, `android` ou `html`. Le code source du jeu en lui-même se situe dans un dossier appelé `core`. C'est dans ce dossier que vous placerez la plupart de votre code source.

#### Exécuter le projet

- Cliquez sur le bouton `Open edit Run/Debug configurations dialog` et sélectionnez la configuration `Desktop`.
- Cliquez sur le bouton `Run (Desktop)`.

### Android

**Attention !** Vous devez avoir paramétré le projet en cochant `Android` dans la section `Sub Projects`.

### IOS

**Attention !** Vous devez avoir paramétré le projet en cochant `Ios` dans la section `Sub Projects`.

Before you can run on iOS you need to install the RoboVM IntelliJ IDEA plugin or Intel Multi-OS Engine. Run -> Edit Configurations..., click the plus (+) button and select RoboVM iOS. Set the Name to iOS. The Module should be set to ios if not already done. To run on the simulator select Simulator as radio button and select a Device. Click Apply and Run If you run on a device, you need to provision it to be able to deploy to it!

### HTML

**Attention !** Vous devez avoir paramétré le projet en cochant `Html` dans la section `Sub Projects`.

View -> Tool Window -> Terminal, in the terminal, make sure you are in the root folder of your project. Then execute gradlew.bat html:superDev (Windows) or ./gradlew html:superDev (Linux, Mac OS X). This will take a while, as your Java code is compiled to Javascript. Once you see the message The code server is ready, fire up your browser and go to http://localhost:8080/index.html. This is your app running in the browser! When you change any of your Java code or assets, just click the SuperDev refresh button while you are on the site and the server will recompile your code and reload the page! To kill the process, simply press CTRL + C in the terminal window. 

IMPORTANT The port 9876 is used when doing normal GWT development. Therefore, trying to access the game in any other way than using the port 8080 will not launch your project.

Once this bug in the Gradle tooling API is fixed, we can simplify running the HTML5 by using the Gradle integration. At the moment, the Gradle process will run forever even if canceled.

## Debugger votre projet

Follow the steps for running the project, but instead of launching via the run (Play) button, launch your configuration via the debug (bug) button. Debugging the HTML5 project is a bit more involved.

Run the superDev Gradle task as before. Go to http://localhost:8080/html, click on the SuperDev Refresh button and hit Compile. In Chrome, press F12 to bring up the developer tools, go to the sources tab and find the Java file you want to debug. Set breakpoints, step and inspect variables using the power of source maps!

## Exporter votre projet

[Documentation officielle](https://libgdx.badlogicgames.com/documentation/gettingstarted/Packaging.html) sur l'export vers les plateformes cibles.

## Cycle de vie d'un jeu avec libGDX

Une application libGDX a un cycle de vie bien défini qui gouverne les états d'une application tels que la création, la pause, la reprise, le rendu et la destruction d'une application.

### ApplicationListener

Un développeur d'application exploite ces évènements du cycle de vie en implémentant l'interface `ApplicationListener` et en passant une instance de cette implémentation à l'implémentation concrète de l'interface `Application` d'une plateforme spécifique. De là, l'interface `Application` appellera l'`ApplicationListener` à chaque fois qu'un évènement de niveau application surviendra. Une implémentation basique d'`ApplicationListener` pourrait ressembler au code suivant :

```java
public class Game implements ApplicationListener {

   @Override
   public void create () {}

   @Override
   public void render () {}

   @Override
   public void resize (int width, int height) {}

   @Override
   public void pause () {}

   @Override
   public void resume () {}

   @Override
   public void dispose () {}

}
```

**Remarque :** Vous pouvez également créer une classe dérivée de la classe `ApplicationAdapter` (qui implémente elle-même l'interface `ApplicationListener`) si toutes les méthodes de l'interface ne vous sont pas utiles.

Une fois passée à l'`Application`, les méthodes de l'`ApplicationListener` seront appelées comme suit :

- `create()` : Méthode appelée une seule fois lorsque l'application est créée. Utilisée pour l'initialisation et chargement des ressources du jeu.
- `resize(int width, int height)` : Méthode appelée chaque fois que l'écran de jeu est redimensionné et que le jeu n'est pas dans un état de pause. Elle est également appelée une fois juste après la méthode `create()` lors de l'initialisation. Les paramètres correspondent à la nouvelle largeur et hauteur de l'écran de jeu redimensionné (en pixels).
- `render()` : Méthode appelée par la boucle de jeu depuis l'application chaque fois qu'un rendu doit être exécuté. Les mises à jour de la logique de jeu et l'affichage sont généralement exécutées dans cette méthode.
- `pause()` : Sur Android, cette méthode est appelée lorsque le bouton `Home` est appuyé ou si un appel est reçu. Sur ordinateur, elle est appelée juste avant la méthode `dispose()` lorsque le jeu se termine. Une bon endroit pour sauvegarder l'état du jeu.
- `resume()` : Cette méthode est seulement appelée sur Android, lorsque l'application reprend après un état de pause.
- `dispose()` : Méthode appelée lorsque l'application est détruite. Elle est précédée d'un appel à la méthode `pause()`.

Le diagramme suivant illustre visuellement le cycle de vie :

![diagramme du cycle de vie](images/libgdx_diagramme_cycle_de_vie.png)

### Où est la boucle principale ?

LibGDX est basé sur les évènements par nature. Cela est principalement dû à la façon dont fonctionnent *Android* et *JavaScript*. Une boucle principale explicite n'existe pas. Cependant la méthode `ApplicationListener.render()` peut être considérée comme le corps d'une telle boucle.

## Modules

libGDX est composé de six interfaces qui fournissent les fonctionnalités pour interagir avec le système de la plateforme cible. Chaque plateforme cible possède une implémentation spécifique de ces interfaces. 

- **Application :** exécute l'application et transmet à l'API cliente les évènements de niveau application. Fournit des fonctionnalités d'identification et de requètes.
- **Files :** expose le système de fichiers sous jacent de la plateforme cible. Fournit une abstraction sur différent types d'emplacements de fichiers par dessus un système de gestion de fichier personalisé. N'est pas compatible avec la classe `File` Java.
- **Input:** informe l'API cliente des entrées utilisateur. Les évènements et le sondage sont pris en charge.
- **Net:** fournit les moyens d'accéder à des ressources via HTTP/HTTPS d'une manière cross-plateforme ainsi que la création de serveur TCP et de sockets client.
- **Audio:** fournit les moyens de lire des effets audio et de la music en streaming ainsi que l'accès direct au matériel audio pour les entrées sorties PCM.
- **Graphics:** expose OpenGL ES 2.0 (quand il est disponible) et permet la récupération et le paramétrage des modes videos et d'autres choses similaires.

### Classes de démarrage

Le seul code spécifique à une plateforme cible que vous devez écrire est contenu dans les classes de démarrage. Pour chaque plateforme cible, un bout de code va instancier une implémentation concrète de l'interface `Application`, fournie par les classes de bas niveau pour la plateforme.

Pour Windows et Mac OS cela peut ressembler au code suivant (qui utilise la couche *Lwjgl*) :

```java
public class DesktopStarter {
   public static void main(String[] argv) {
      LwjglApplicationConfiguration config = new LwjglApplicationConfiguration();
      new LwjglApplication(new Game(), config);
   }
}
```

Pour Android, la classe de démarrage ressemblera plutôt au code suivant :

```java
public class AndroidStarter extends AndroidApplication {
   public void onCreate(Bundle bundle) {
      super.onCreate(bundle);
      AndroidApplicationConfiguration config = new AndroidApplicationConfiguration();
      initialize(new Game(), config);
   }
}
```

Ces deux classes vivent généralement dans des projets séparés (par exemple un projet `Desktop` et un projet `Android`).

Le code réel de l'application est situé dans une classe qui implémente l'interface `ApplicationListener` (`MyGame` dans les exemples précédents). Une instance de cette classe est passée aux méthodes d'initialisation respectives à chaque implémentation bas-niveau de l'`Application`. L'application va ensuite appeler les méthodes de l'interface `ApplicationListener` au moment approprié.

### Accès aux modules

Les modules décrits précédemment peuvent être accéder via des champs statiques de la classe `Gdx`. C'est essentiellement un jeu de variables globales qui permettent un accès facile à n'importe quel module de libGDX. Généralement considéré comme une mauvaise pratique, nous avons décidé d'utiliser ce mécanisme pour alléger la difficulté associée avec le passage de références aux choses utilisées souvent dans tous les types d'endroits dans le code.

Par exemple, pour accéder au module `audio`, utilisez simplement le code suivant :

```java
// creates a new AudioDevice to which 16-bit PCM samples can be written
AudioDevice audioDevice = Gdx.audio.newAudioDevice(44100, false);
```

`Gdx.audio` est une référence à l'implémentation bas-niveau qui a été instanciée au démarrage de l'application par l'instance de l'interface `Application`. Les autres modules sont accessibles de la même manière (par exemple, `Gdx.app` pour ccéder à l'implémentation du module `Application`, `Gdx.files` pour accéder à l'implémentation du module `Files`, etc...).

### Le module Application

Le module application est accessible depuis `Gdx.app`. Il donne accès à des fonctionnalités de logging, à une méthode pour quitter le jeu de manière sûre, à la persistence de données, à la récupération de la version de l'API Android ou du type de la plateforme et à l'utilisation de la mémoire.

#### Logging

Le niveau de log par défaut est `LOG_INFO`. Vous pouvez modifier le niveau de log avec la méthode `setLogLevel`.

```java
Gdx.app.setLogLevel(Application.LOG_DEBUG);
```

Vous pouvez utiliser ces différents niveaux de log :

- `LOG_NONE` : aucun log n'est affiché et la fonctionnalité est désactivée.
- `LOG_ERROR` : affiche uniquement les logs d'erreur.
- `LOG_INFO` : affiche les logs d'erreur et d'information.
- `LOG_DEBUG` : affiche les logs d'erreur, d'information et de debug.

Pour afficher un log sur la console, utlisez le code suivant :

```java
Gdt.app.log("balise de test", "Ceci est un log d'information.");
Gdt.app.debug("balise de test", "Ceci est un log de debug.");
Gdt.app.error("balise de test", "Ceci est un log d'erreur.");
```

#### Quitter l'application

Utilisez la méthode `exit` pour quitter l'application dans le bon ordre en libérant correctement la mémoire.

```java
Gdx.app.exit();
```

**Remarque :** Utilisez toujours cette méthode pour terminer votre application et vous assurer que la mémoire est totalement libérée.



## Liens utiles

La ressource la plus utile pour apprendre libGDX est le [wiki officiel](https://github.com/libgdx/libgdx/wiki).

**Attention !** La [documentation officiel](https://libgdx.badlogicgames.com/documentation/) sur le site de badlogic est atrocement limitée pour apprendre à utiliser libGDX. Elle propose juste d'expliquer quels outils utiliser et comment les configurer pour démarrer. Elle contient également des informations pour exporter un projet sur les plateformes cibles. D'une manière générale, utilisez de préférence le wiki !

L'autre ressource essentielle est l'[API de libGDX](https://libgdx.badlogicgames.com/ci/nightlies/docs/api/).

## Système de coordonnées

L'origine se situe en bas à gauche de l'affichage. Les valeurs sur l'axe Y augmentent lorsqu'on monte. Pareil pour les images.

## Assets

Placez vos assets graphiques et audio dans le dossier `assets` du dossier de projet `android` ou du dossier général `core` ou encore dans le dossier `resources` du dossier de projet `desktop`.

## Créer une classe de constantes

Pour stocker des valeurs constantes utilisables partout dans votre projet, créez un package `utils`, puis dans ce dernier, créez une classe `Constants`.

```java
public class Constants {}
```

Dans cette classe, créez un membre `VIEWPORT_WIDTH` pour représenter la largeur du viewport.

```java
public final static int VIEWPORT_WIDTH = 640;
```

Créez un membre `VIEWPORT_HEIGHT` pour représenter la hauteur du viewport.

```java
public final static int VIEWPORT_HEIGHT = 360;
```

Créez un membre `WINDOW_WIDTH` pour représenter la largeur de la fenêtre dans l'environnement desktop.

```java
public final static int WINDOW_WIDTH = 1280;
```

Créez un membre `WINDOW_HEIGHT` pour représenter la hauteur de la fenêtre dans l'environnement desktop.

```java
public final static int WINDOW_HEIGHT = 720;
```

Créez un membre `GAME_TITLE` pour représenter le titre du jeu.

```java
public final static STRING GAME_TITLE = "My game";
```

La classe complète :

```java
public class Constants {
   public final static int VIEWPORT_WIDTH = 640;
   public final static int VIEWPORT_HEIGHT = 360;
   public final static int WINDOW_WIDTH = 1280;
   public final static int WINDOW_HEIGHT = 720;
   public final static STRING GAME_TITLE = "My game";
}
```

## Définir la taille de la fenêtre en plateforme desktop

Utilisez l'objet de configuration `LwjglApplicationConfiguration` de la classe de démarrage.

```java
LwjglApplicationConfiguration config = new LwjglApplicationConfiguration();
config.width = WINDOW_WIDTH;
config.height = WINDOW_HEIGHT;
config.title = Constants.GAME_TITLE;
```

## Créer des écrans de jeux

Créez un package `states` pour stocker les différentes classes utiles aux écrans de jeu.

### La classe `GameStateManager`

Créez une classe `GameStateManager`. Elle contiendra tous les écrans de jeu représentés par des objets d'une classe abstraite `GameState` que vous allez créer par la suite.

```java
public class GameStateManager {}
```

Créez un membre privé `Stack<GameState>` qui contiendra une pile d'écrans de jeu.

```java
import java.utils.Stack;
...
private Stack<GameState> gameStates;
```

Créez un constructeur pour créer une instance de la pile.

```java
public GameStateManager() {
   gameStates = new Stack<GameState>();
}
```

Créez une méthode `push` pour ajouter l'objet `gameState` sur la pile.

```java
public void push(GameState gameState) {
   gameStates.push(gameState);
}
```

Créez une methode `set` pour changer d'écran de jeu. Elle doit retirer et détruire l'écran de jeu stocké sur le dessus de la pile. Elle ajoute ensuite l'objet `gameState` passé en paramètre.

```java
public void set(GameState gameState) {
   gameStates.pop().dispose();
   gameStates.push(gameState);
}
```

Créez une méthode `update` pour mettre à jour la logique de l'écran de jeu en cours.

```java
public void update(float deltaTime) {
   gameStates.peek().update(dt);
}
```

**Remarque :** La méthode `peek` prend l'objet sur la pile et le remet au dessus.

Créez une méthode `render` pour afficher l'écran de jeu en cours.

```java
public void render(SpriteBatch spriteBatch) {
   gameStates.peek().render(spriteBatch);
}
```

**Remarque :** La méthode `dispose` du `GameState` courant est appelée une seule fois lorsqu'on retire définitivement le `GameState` de la pile.

La classe complète :

```java
import java.utils.Stack;

public class GameStateManager {

   private Stack<GameState> gameStates;

   public GameStateManager() {
      gameStates = new Stack<GameState>();
   }

   public void push(GameState gameState) {
      gameStates.push(gameState);
   }

   public void set(GameState gameState) {
      gameStates.pop().dispose();
      gameStates.push(gameState);
   }

   public void update(float deltaTime) {
      gameStates.peek().update(dt);
   }

   public void render(SpriteBatch spriteBatch) {
      gameStates.peek().render(spriteBatch);
   }

}
```

### La classe `GameState`

Créez une classe abstraite `GameState`. Tous les écrans de jeux hériteront de cette classe.

```java
public abstract class GameState {}
```

Créez un membre `protected` de type `OrthographicCamera`.

```java
protected OrthographicCamera orthographicCamera;
```

Créez un membre `protected` de type `GameStateManager`.

```java
protected GameStateManager gameStateManager;
```

Créez un constructeur prenant un `GameStateManager`. Dans le constructeur, affectez le paramètre au membre et instancier le membre `orthographicCamera`.

```java
public GameState() {
   orthographicCamera = new OrthographicCamera();
   this.gameStateManager = gameStateManager;
}
```

Créez une méthode abstraite `handleInput` pour gérer les contrôles. Elle ne prend pas de paramètre et ne renvoie rien.

```java
protected abstract void handleInput();
```

Créez une méthode abstraite `update` pour mettre à jour la logique de l'écran de jeu. Elle prend un `float` en paramètre et ne renvoie rien.

```java
public abstract void update(float deltaTime);
```

Créez une méthode abstraite `render` pour afficher l'écran de jeu. Elle prend un `SpriteBatch` en paramètre et ne renvoie rien.

```java
public abstract void render(SpriteBatch spriteBatch);
```

Créez une méthode abstraite `dispose` pour libérer la mémoire des ressources utilisées par l'écran de jeu. Elle ne prend pas de paramètre et ne renvoie rien.

```java
public abstract void dispose();
```

La classe complète :

```java
public abstract class GameState {

   protected OrthographicCamera orthographicCamera;
   protected GameStateManager gameStateManager;

   public GameState() {
      orthographicCamera = new OrthographicCamera();
      this.gameStateManager = gameStateManager;
   }

   protected abstract void handleInput();
   public abstract void update(float deltaTime);
   public abstract void render(SpriteBatch spriteBatch);
   public abstract void dispose();

}
```

### Tester les classes `GameStateManager` et `GameState`

#### Créer un `GameState` concret

Créez une classe `TestGameState` qui hérite de `GameState`. Définissez un constructeur publique et implémentez les méthodes abstraites de la classe `GameState`.

```java
public class TestGameState extends GameState {

   public TestGameState(GameStateManager gameStateManager) {
      super(gameStateManager);
   }

   @Override
   protected void handleInput() {

   }

   @Override
   public void update(float deltaTime) {

   }

   @Override
   public void render(SpriteBatch spriteBatch) {

   }

   @Override
   public void dispose() {

   }

}
```

Créez un membre `Texture`.

```java
private Texture texture;
```

Dans le constructeur, instanciez une nouvelle `texture` en chargeant une image stockée dans le dossier `assets`. Ici, le fichier image s'appelle `image.png`.

```java
texture = new Texture("image.png");
```

Dans la méthode `render`, affichez l'image avec la méthode `draw` de l'objet `spriteBatch`. Le premier paramètre est la texture. Le deuxième est la position X. Le troisième est la position Y.

**Attention !** Pensez bien à encadrer cet appel avec les méthodes `begin` et `end` de l'objet `spriteBatch`.

```java
spriteBatch.begin();
spriteBatch.draw(texture, 0, 0);
spriteBatch.end();
```

Dans la méthode `dispose`, libérez les ressources de la texture.

```java
texture.dispose();
```

La classe complète :

```java
public class TestGameState extends GameState {

   private Texture texture;

   public TestGameState(GameStateManager gameStateManager) {
      super(gameStateManager);
      texture = new Texture("image.png");
   }

   @Override
   protected void handleInput() {

   }

   @Override
   public void update(float deltaTime) {

   }

   @Override
   public void render(SpriteBatch spriteBatch) {
      spriteBatch.begin();
      spriteBatch.draw(texture, 0, 0);
      spriteBatch.end();
   }

   @Override
   public void dispose() {
      texture.dispose();
   }

}
```

#### Exécuter le projet

Ouvrez la classe principale héritant d'`ApplicationListener`.

Créez un membre `GameStateManager`.

```java
private GameStateManager gameStateManager;
```

Créez un membre `SpriteBatch`.

```java
private SpriteBatch spriteBatch;
```

Dans la méthode `create`, instanciez le membre `GameStateManager` et le membre `SpriteBatch`.

```java
gameStateManager = new GameStateManager();
spriteBatch = new SpriteBatch();
```

Toujours dans la méthode `create`, ajoutez au `GameStateManager` un nouveau `GameState`, instance de la classe concrète `TestGameState`.

**Remarque :** Pensez à passer au constructeur l'objet `gameStateManager`.

```java
gameStateManager.push(new TestGameState(gameStateManager));
```

Dans la méthode `render`, appelez la méthode `update` de l'objet membre `gameStateManager` et en lui passant le delta time que vous pouvez obtenir par la méthode `Gdx.graphics.getDeltaTime`. Ensuite, appelez la méthode `render` de l'objet `gameStateManager` en passant l'objet membre `spriteBatch`.

```java
gameStateManager.update(Gdx.graphics.getDeltaTime());
gameStateManager.render(spriteBatch);
```

Dans la méthode `dispose`, libérez la mémoire allouée pour l'objet membre `spriteBatch`.

```java
spriteBatch.dispose();
```

La classe complète :

```java
public class Game implements ApplicationListener {

   private GameStateManager gameStateManager;
   private SpriteBatch spriteBatch;

   @Override
   public void create () {
      gameStateManager = new GameStateManager();
      spriteBatch = new SpriteBatch();
      gameStateManager.push(new TestGameState(gameStateManager));
   }

   @Override
   public void render () {
      gameStateManager.update(Gdx.graphics.getDeltaTime());
      gameStateManager.render(spriteBatch);      
   }

   @Override
   public void resize (int width, int height) {
   }

   @Override
   public void pause () {
   }

   @Override
   public void resume () {
   }

   @Override
   public void dispose () {
      spriteBatch.dispose();
   }

}
```

Exécutez le projet pour afficher l'image. Si tout fonctionne bien, vous pouvez supprimez la classe `TestGameState`.

### Créer un écran de menu principal

Dans le package `states`, créez une classe `MainMenu` qui hérite de la classe `GameState`.

```java
public class MainMenu extends GameState {}
```

Ajoutez le constructeur et les méthodes abstraites de la classe `GameState`.

```java
public MainMenu(GameStateManager gameStateManager) {
   super(gameStateManager);
}

@Override
protected void handleInput() {}

@Override
public void update(float deltaTime) {}

@Override
public void render(SpriteBatch spriteBatch) {}

@Override
public void dispose() {}
```

Créez un membre `Texture` pour chaque fichier image que vous souhaitez utiliser.

```java
private Texture background;
private Texture foreGround;
```

Dans le constructeur, instanciez ces membres `Texture`.

```java
background = new Texture("background.png");
foreground = new Texture("foreground.png");
```

Créez un membre `BitmapFont` pour chaque police bitmap que vous souhaitez utiliser.

```java
private BitmapFont titleText;
private BitmapFont touchScreenText;
```

Pour générer des polices bitmap à partir d'un fichier de police `.ttf`, vous aurez besoin d'un générateur de police. Créez un membre `FreeTypeFontGenerator`.

```java
private FreeTypeFontGenerator freeTypeFontGenerator;
```

Pour modifier la taille du texte généré, créez un membre `FreeTypeFontGenerator.FreeTypeFontParameter`.

```java
private FreeTypeFontGenerator.FreeTypeFontParameter freeTypeFontParameter;
```

**Attention !** Ces classes sont dans une extension de libGDX. Pour les utiliser, vous devez avoir inclut l'extension `FreeTypeFont` lors de la création du projet ou vous devrez ajouter manuellement la dépendance à cette extension.

Créez des membres `GlyphLayout` pour récupérer la taille du texte.

```java
private GlyphLayout gameTitleGlyphLayout;
private GlyphLayout touchScreenGlyphLayout;
```

Dans le constructeur, instanciez le membre `FreeTypeFontGenerator` en lui passant le fichier d'une police `.ttf` à utiliser pour générer une police bitmap.

```java
freeTypeFontGenerator = new FreeTypeFontGenerator(Gdx.files.internals("title.ttf"));
```

**Attention !** Contrairement au type `Texture`, vous devez utiliser la méthode `Gdx.files.internals` pour indiquer que la ressource se trouve dans le dossier `assets` du projet (le dossier définit en tant que `working directory`).

Instanciez également le membre `FreeTypeFontParameter`.

```java
freeTypeFontParameter = new FreeTypeFontGenerator.FreeTypeFontParameter();
```

Définissez la taille actuelle du générateur de police avec le membre `size` de l'objet `freeTypeFontParameter`.

```java
freeTypeFontParameter.size = 128;
```

Vous n'avez plus qu'à générer une police bitmap à partir du générateur et du paramétreur.

```java
titleText = freeTypeFontGenerator.generateFont(freeTypeFontParameter);
```

Si besoin, modifiez à nouveau la taille actuelle du générateur de police avec le membre `size` de l'objet `freeTypeFontParameter`.

```java
freeTypeFontParameter.size = 64;
```

Et générez une nouvelle police bitmap à partir du générateur et du paramétreur.

```java
touchScreenText = freeTypeFontGenerator.generateFont(freeTypeFontParameter);
```

Instanciez les `glyphLayout`.

```java
gameTitleGlyphLayout = new GlyphLayout();
touchScreenGlyphLayout = new GlyphLayout();
```

Définissez le texte à afficher avec la méthode `setText`.

```java
gameTitleGlyphLayout.setText(titleText, GAME_TITLE);
touchScreenGlyphLayout.setText(touchScreenText, "TOUCH SCREEN");
```

Définissez le système de coordonnées avec la méthode `setToOrtho` de l'objet membre `orthographicCamera` (provenant de la classe abstraite `GameState`). Le premier paramètre indique l'orientation de l'axe Y. S'il vaut `false`, les Y augmentent vers le haut. Les deux autres paramètres indiquent la taille du champ de vision.

```java
orthographicCamera.setToOrth(false, Constants.VIEWPORT_WIDTH, Constants.VIEWPORT_HEIGHT);
```

Le constructeur est terminé. Vous pouvez désormais utiliser la méthode `render` pour afficher le contenu de l'écran de menu principal. Dans la méthode `render`, commencez par définir la matrice de projection.

```java
spriteBatch.setProjectionMatrix(orthographicCamera.combined);
```

Placez ensuite les méthodes `begin` et `end` de l'objet `spriteBatch` pour encadrer les affichages.

```java
spriteBatch.begin();
spriteBatch.end();
```

Entre ces deux méthodes, affichez d'abord le fond.

```java
spriteBatch.draw(background, 0, 0);
```

Puis le premier plan.

```java
spriteBatch.draw(foreground, 0, 0);
```

Ensuite, affichez les textes. Cela fonctionne un petit peu à l'envers des textures. Vous appelez la méthode `draw` des objet `BitmapFont` et vous passez le `SpriteBatch`, le `GlyphLayout` du texte, et la position.

```java
titleText.draw(
   spriteBatch,
   gameTitleGlyphLayout,
   orthographicCamera.viewportWidth / 2 - gameTitleGlyphLayout.width / 2,
   orthographicCamera.height * 2 / 3);
touchScreenText.draw(
   spriteBatch,
   touchScreenGlyphLayout,
   orthographicCamera.width / 2 - touchScreenGlyphLayout.width / 2,
   orthographicCamera.height / 3);
```

Pour finir, n'oubliez pas, dans la méthode `dispose`, de libérer la mémoire prise par les ressources de cet écran de jeu.

```java
background.dispose();
foreground.dispose();
titleText.dispose();
touchScreenText.dispose();
freeTypeFontGenerator.dispose();
```

Passez à la gestion des contrôles du joueur. Appelez la méthode `handleInput` dans la méthode `update`.

```java
handleInput();
```

Pour passer à un autre écran de jeu lorsque le joueur touche l'écran, commencez par vérifier si l'utilisateur a touché l'écran. Dans la méthode `handleInput` appelez la méthode `Gdx.input.istouched`. Cette méthode renvoie `true` si le joueur touche l'écran. Appelez alors la méthode `set` du membre `gameStateManager` en passant une nouvelle instance d'un autre écran de jeu (ici un objet `PlayState` que vous implémenterez plus loin).

```java
if (Gdx.input.isTouched()) {
   gameStateManager.set(new Playstate(gameStateManager));
}
```

La classe complète :

```java
public class MainMenu extends GameState {

   private Texture background;
   private Texture foreGround;
   private BitmapFont titleText;
   private BitmapFont touchScreenText;
   private FreeTypeFontGenerator freeTypeFontGenerator;
   private FreeTypeFontGenerator.FreeTypeFontParameter freeTypeFontParameter;
   private GlyphLayout gameTitleGlyphLayout;
   private GlyphLayout touchScreenGlyphLayout;

   public TestGameState(GameStateManager gameStateManager) {
      super(gameStateManager);
      background = new Texture("background.png");
      foreground = new Texture("foreground.png");
      freeTypeFontGenerator = new FreeTypeFontGenerator(Gdx.files.internals("title.ttf"));
      freeTypeFontParameter = new FreeTypeFontGenerator.FreeTypeFontParameter();
      freeTypeFontParameter.size = 128;
      titleText = freeTypeFontGenerator.generateFont(freeTypeFontParameter);
      freeTypeFontParameter.size = 64;
      touchScreenText = freeTypeFontGenerator.generateFont(freeTypeFontParameter);
      gameTitleGlyphLayout = new GlyphLayout();
      touchScreenGlyphLayout = new GlyphLayout();
      gameTitleGlyphLayout.setText(titleText, GAME_TITLE);
      touchScreenGlyphLayout.setText(touchScreenText, "TOUCH SCREEN");
      orthographicCamera.setToOrth(false, Constants.VIEWPORT_WIDTH, Constants.VIEWPORT_HEIGHT);
   }

   @Override
   protected void handleInput() {
      if (Gdx.input.isTouched()) {
         gameStateManager.set(new Playstate(gameStateManager));
      }
   }

   @Override
   public void update(float deltaTime) {
      handleInput();
   }

   @Override
   public void render(SpriteBatch spriteBatch) {
      spriteBatch.setProjectionMatrix(orthographicCamera.combined);
      spriteBatch.begin();
      spriteBatch.draw(background, 0, 0);
      spriteBatch.draw(foreground, 0, 0);
      titleText.draw(
         spriteBatch,
         gameTitleGlyphLayout,
         orthographicCamera.viewportWidth / 2 - gameTitleGlyphLayout.width / 2,
         orthographicCamera.height * 2 / 3);
      touchScreenText.draw(
         spriteBatch,
         touchScreenGlyphLayout,
         orthographicCamera.width / 2 - touchScreenGlyphLayout.width / 2,
         orthographicCamera.height / 3);
      spriteBatch.end();
   }

   @Override
   public void dispose() {
      background.dispose();
      foreground.dispose();
      titleText.dispose();
      touchScreenText.dispose();
      freeTypeFontGenerator.dispose();
   }

}
```

### Créer un écran de jeu principal

Dans le package `states`, créez une classe `PlayState` qui hérite de la classe `GameState`.

```java
public class PlayState extends GameState {}
```

Ajoutez le constructeur et les méthodes abstraites de la classe `GameState`.

```java
public PlayState(GameStateManager gameStateManager) {
   super(gameStateManager);
}

@Override
protected void handleInput() {}

@Override
public void update(float deltaTime) {}

@Override
public void render(SpriteBatch spriteBatch) {}

@Override
public void dispose() {}
```

Créez un membre `Texture` pour chaque fichier image que vous souhaitez utiliser.

```java
private Texture background;
private Texture ground;
```

Dans le constructeur, instanciez ces membres `Texture`.

```java
background = new Texture("background.png");
ground = new Texture("ground.png");
```

Dans la méthode `render`, affichez les images.

```java
spriteBatch.begin();
spriteBatch.draw(background, 0, 0);
spriteBatch.draw(ground, 0, 0);
spriteBatch.end();
```










La classe complète :

```java
public class PlayState extends GameState {

   private Texture background;
   private Texture ground;

   public PlayState(GameStateManager gameStateManager) {
      super(gameStateManager);
      background = new Texture("background.png");
      ground = new Texture("ground.png");
   }

   @Override
   protected void handleInput() {}

   @Override
   public void update(float deltaTime) {}

   @Override
   public void render(SpriteBatch spriteBatch) {
      spriteBatch.begin();
      spriteBatch.draw(background, 0, 0);
      spriteBatch.draw(ground, 0, 0);
      spriteBatch.end();
   }

   @Override
   public void dispose() {}

}
```

## Rajouter une extension à un projet

Vous aurez parfois besoin de rajouter une extension que vous n'aviez pas incluse lors de la création du projet. Recherchez sur internet `libgdx add dependency`. Vous devriez trouver le [lien suivant](https://github.com/libgdx/libgdx/wiki/Dependency-management-with-Gradle). Vous devez ajouter certaines lignes au fichier `build.gradle` contenu dans le dossier `Gradle Scripts` de votre projet. Vous devez éditer le fichier `build.gradle (Project: xxxx)`, pas un des nombreux fichiers `build.gradle` associé à chaque plateforme de déploiement. Collez simplement les lignes indiquées dans le lien dans la section `dependencies` de chaque plateforme ainsi que celle de la section `core`. Cliquez ensuite sur le bouton `Sync Now` dans le nouveau message en haut à droite de la fenêtre pour mettre à jour le projet.

## Obtenir la taille d'une image

Utilisez les méthodes `getWidth` et `getHeight` d'un objet `Texture`.

```java
Texture image = new Texture("badlogic.jpg");
int imageWidth = image.getWidth();
int imageHeight = image.getHeight();
```

## Obtenir le delta time

Utilisez la méthode `getDeltaTime` de l'objet `Gdx.graphics`.

```java
float deltaTime = Gdx.graphics.getDeltaTime();
```

## SpriteBatch

**Attention !** Un seul objet de type `SpriteBatch` suffit en général pour tout le jeu. Instanciez de préférence une seule fois cette classe.









```java
import com.badlogic.gdx.ApplicationAdapter;
import com.badlogic.gdx.Gdx;
import com.badlogic.gdx.graphics.GL20;
import com.badlogic.gdx.graphics.Texture;
import com.badlogic.gdx.graphics.g2d.SpriteBatch;
import com.badlogic.gdx.math.Vector2;

public class Game extends ApplicationAdapter {
	SpriteBatch batch;
	Texture img;
	Vector2 position;
	Vector2 direction;
	final float SPEED = 500;
	
	@Override
	public void create () {
		batch = new SpriteBatch();
		img = new Texture("badlogic.jpg");
		position = new Vector2(0, 0);
		double startAngle = Math.toRadians(Math.random() * 360);
		direction = new Vector2((float)Math.cos(startAngle), (float)Math.sin(startAngle));
	}

	@Override
	public void render () {
		position.mulAdd(direction, SPEED * Gdx.graphics.getDeltaTime());
		if (position.x < 0) {
			direction.x *= -1;
			position.x = 0;
		}
		if (position.x + img.getWidth() > Gdx.graphics.getWidth()) {
			direction.x *= -1;
			position.x = Gdx.graphics.getWidth() - img.getWidth();
		}
		if (position.y < 0) {
			direction.y *= -1;
			position.y = 0;
		}
		if (position.y + img.getHeight() > Gdx.graphics.getHeight()) {
			direction.y *= -1;
			position.y = Gdx.graphics.getHeight() - img.getHeight();
		}

		Gdx.gl.glClearColor(1, 0, 0, 1);
		Gdx.gl.glClear(GL20.GL_COLOR_BUFFER_BIT);
		batch.begin();
		batch.draw(img, position.x, position.y);
		batch.end();
	}
	
	@Override
	public void dispose () {
		batch.dispose();
		img.dispose();
	}
}
```
