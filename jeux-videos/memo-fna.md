# Mémo FNA

Par *flashjaysan* avec l'aide d'*IronPowerLNA*

## Présentation

[FNA](https://fna-xna.github.io/) est une bibliothèque [FOSS](https://itsfoss.com/what-is-foss/) (libre et open source) destinée à la programmation de jeux vidéos en langage C#. Dans un but de préservation, elle est conçue pour répliquer à l'identique la bibliothèque [Microsoft XNA Game Studio 4.0 Refresh](https://en.wikipedia.org/wiki/Microsoft_XNA) qui n'est désormais plus maintenue.

## Ressources

Comme FNA est une réimplémentation libre d'XNA, la [documentation pour XNA](http://msdn.microsoft.com/en-us/library/bb200104.aspx) ainsi que toutes les ressources disponibles concernant XNA sont totalement compatibles avec FNA. De nombreux ouvrages ont été publiés pour apprendre XNA et on trouve en ligne de nombreuses ressources.

FNA propose un [wiki](https://github.com/FNA-XNA/FNA/wiki) mais également un [petit tutoriel pour débuter](https://gist.github.com/flibitijibibo/1ce4b7899b3cf1805a420330f0d2faf3) avec cette bibliothèque.

## Installation

### Installer Visual Studio

Commencez par installer [Visual Studio](https://visualstudio.microsoft.com/). Pensez bien à installer dans l'onglet `Charges de travail`, section `Bureau et mobile`, les outils pour le `Développement .NET Desktop`.

**Remarque :** Si vous avez déjà installé Visual Studio sans ces outils, cliquez sur le menu `Outils` et sélectionnez l'option `Obtenir les outils et fonctionnalités...`.

### Générer la DLL de FNA

- Téléchargez l'archive la plus récente de FNA ainsi que l'archive des bibliothèques natives à l'adresse [https://fna-xna.github.io/download/](https://fna-xna.github.io/download/).
- Dézippez ces deux fichiers archives à l'emplacement de votre choix.
- Ouvrez le projet `FNA.csproj` de l'archive de FNA dans Visual Studio.
- En haut de la fenêtre de Visual Studio, dans la barre d'outils, sélectionnez l'option `Release` dans le menu déroulant `Configurations de solutions`.
- Dans l'explorateur de solutions, faites un clic droit sur la solution et sélectionnez `Générer la solution`. Un message doit afficher que la génération a réussi. Un fichier `FNA.dll` vient d'être créé.
- Toujours dans l'explorateur de solutions, faites un clic droit sur le projet et sélectionnez `Ouvrir le dossier dans l'Explorateur de fichiers`. Un explorateur de fichiers s'ouvre à l'emplacement du projet.
- Allez dans le sous-dossier `bin/release` et récupérez le fichier `FNA.dll`.
- Vous pouvez fermer le projet.

### Créer un projet

Dans Visual Studio, créer un projet `Application Console .NET Framework`.

#### Ajouter FNA

Vous devez préciser au compilateur que le projet a une dépendance à FNA. Cela lui permet de reconnaître la bibliothèque (et par la même occasion de vous donner accès à Intellisense pour la bibliothèque de classes de FNA), et de configurer l'éditeur de liens.

- Placez le fichier `FNA.dll` dans le dossier de votre projet.
- Dans l'explorateur de solutions, faites un clic droit sur `Références` et sélectionnez l'option `Ajouter une référence...`. La fenêtre `Gestionnaire de références` s'affiche.
- Sélectionnez la section `Parcourir` puis cliquez sur le bouton `Parcourir...`.
- Recherchez et sélectionner le fichier `FNA.dll` puis cliquez sur le bouton `Ajouter`. Fermez la fenêtre en cliquant sur le bouton `OK`.

#### Premier programme

Dans le fichier `Program.cs`, ajoutez la clause suivante :

```csharp
using Microsoft.Xna.Framework;
```

Dans le fichier `Program.cs`, dans la méthode `Main`, ajoutez le code suivant :

```csharp
using (Game game = new Game())
{
    new GraphicsDeviceManager(game);
    game.Run();
}
```

Le code minimal est le suivant :

```csharp
using Microsoft.Xna.Framework;

static class Program
{
	static void Main(string[] args)
	{
		using (Game game = new Game())
		{
			new GraphicsDeviceManager(game);
			game.Run();
		}
	}
}
```

En haut de la fenêtre de Visual Studio, dans la barre d'outils, cliquez sur le bouton `Demarrer` pour compiler et exécuter le projet. L'exécution provoque une erreur mais le but de cette manipulation était de générer un dossier avec les fichiers exécutables.

#### Ajouter les bibliothèques natives

Avant de pouvoir exécuter votre projet, vous devez ajouter les bibliothèques natives.

- Dans l'explorateur de solutions, faites un clic droit sur le projet et sélectionnez `Ouvrir le dossier dans l'Explorateur de fichiers`. Un explorateur de fichiers s'ouvre à l'emplacement du projet.
- Allez dans le sous-dossier `bin/debug`.
- Placez tous les fichiers DLL situés dans le dossier `x86` de l'archive des bibliothèques natives dans le sous-dossier `bin/debug`.

**Remarque :** Il est possible que vous deviez utiliser le dossier `x64` plutôt que le dossier `x86`. La [page ayant servi de référence](https://gist.github.com/flibitijibibo/1ce4b7899b3cf1805a420330f0d2faf3) utilise le dossier `x64` avec la configuration `AnyCPU` mais cela n'a pas fonctionné chez moi.

Cliquez sur le bouton `Demarrer` pour exécuter le projet. L'exécution ne provoque plus d'erreur. Vous avez un premier projet FNA mais il n'est pas très fonctionnel.

### Améliorer le programme

Au lieu d'instancier directement la classe `Game` dans la méthode `Main`, vous allez hériter de cette classe.

- Dans votre projet, créez une nouvelle classe (`CTRL+SHIFT+A`) appelée `FNAGame`. Voici son code :

```csharp
using Microsoft.Xna.Framework;

class FNAGame : Game
{
	public FNAGame()
	{
		new GraphicsDeviceManager(this);
	}
}
```

Modifier le code de la méthode `Main` dans la classe `Program` :

```csharp
using (FNAGame game = new FNAGame())
{
    game.Run();
}
```

Cliquez sur le bouton `Demarrer` pour exécuter le projet. Pour l'instant, vous avez les mêmes fonctionnalités que précédemment. Ajoutez maintenant les méthodes héritées de la classe `Game` :

```csharp
using Microsoft.Xna.Framework;

class FNAGame : Game
{
	public FNAGame()
	{
		new GraphicsDeviceManager(this);
	}

	protected override void Initialize()
	{
		base.Initialize();
	}

	protected override void LoadContent()
	{
		base.LoadContent();
	}

	protected override void UnloadContent()
	{
		base.UnloadContent();
	}

	protected override void Update(GameTime gameTime)
	{
		base.Update(gameTime);
	}

	protected override void Draw(GameTime gameTime)
	{
		base.Draw(gameTime);
	}
}
```

Vous avez maintenant des méthodes à votre disposition pour créer votre jeu.

- La méthode `Initialize` vous permet d'initialiser toute variable nécessaire à votre jeu mais ne dépendant pas des ressources externes.
- La méthode `LoadContent` vous permet de charger des ressources externes nécessaires à votre jeu.
- La méthode `UnloadContent` vous permet de libérer la mémoire réservée par les ressources externes.
- La méthode `Update` vous permet de programmer la logique de votre jeu.
- La méthode `Draw` vous permet de gérer l'affichage des éléments de votre jeu.

Lorsque le constructeur de la classe `Game` est appelé, le gestionnaire de matériel graphique (`GraphicsDeviceManager`) est initialisé et ses services sont ajoutés à la classe `Game`.

Lorsque la méthode `Run` de la classe `Game` est appelée, les étapes suivantes se déroulent : 

- La méthode `Initialize` est appelée.
- La méthode `LoadContent` est appelée. Cette dernière est également appelée si l'affichage est reconfiguré (par exemple, lors d'un redimensionnement du jeu).
- La boucle de jeu démarre, appelant successivement les méthode `Update` et `Draw`.

Lorsque le jeu se termine, la boucle de jeu prend fin puis la méthode `UnloadContent` est appelée.

Ajoutez la ligne suivante à la méthode `Draw` pour remplir la fenêtre avec une couleur bleue :

```csharp
GraphicsDevice.Clear(Color.CornflowerBlue);
```

Cliquez sur le bouton `Demarrer` pour exécuter le projet.

## Définir la résolution

Lorsque vous instanciez la classe `GraphicsDeviceManager` dans le constructeur de la classe `FNAGame`, utilisez les propriétés `PreferredBackBufferWidth` pour définir la largeur et `PreferredBackBufferHeight` pour définir la hauteur de votre jeu.

```csharp
GraphicsDeviceManager graphicsDeviceManager = new GraphicsDeviceManager(this);
graphicsDeviceManager.PreferredBackBufferWidth = 1280;
graphicsDeviceManager.PreferredBackBufferHeight = 720;
```

## Forcer en plein écran

**[déconseillé]**

Lorsque vous instanciez la classe `GraphicsDeviceManager` dans le constructeur de la classe `FNAGame`, utilisez la propriété `IsFullScreen` pour forcer l'affichage en plein écran de votre jeu.

```csharp
GraphicsDeviceManager graphicsDeviceManager = new GraphicsDeviceManager(this);
graphicsDeviceManager.IsFullScreen = true;
```

## Activer la synchronisation verticale

Lorsque vous instanciez la classe `GraphicsDeviceManager` dans le constructeur de la classe `FNAGame`, utilisez la propriété `SynchronizeWithVerticalRetrace` pour activer la synchronisation verticale de l'affichage de votre jeu. Le moteur de rendu attendra que l'écran ait terminé son affichage précédent avant d'afficher une nouvelle image.

```csharp
GraphicsDeviceManager graphicsDeviceManager = new GraphicsDeviceManager(this);
graphicsDeviceManager.SynchronizeWithVerticalRetrace = true;
```

## Couleurs

La structure `Color` définie dans l'espace de nom `Microsoft.Xna.Framework` représente une couleur *RGBA*. Il y a six constructeurs possible :

- `Color(Int32, Int32, Int32)`
- `Color(Int32, Int32, Int32, Int32)`
- `Color(Single, Single, Single)`
- `Color(Single, Single, Single, Single)`
- `Color(Vector3)`
- `Color(Vector4)`

Une fois une couleur créée, vous pouvez accéder à ses différentes composantes via les propriétés suivantes :

- `R` : composante rouge.
- `G` : composante verte.
- `B` : composante bleue.
- `A` : composante opacité (*alpha*).

La structure `Color` fournit également les couleurs prédéfinies suivantes sous forme de propriétés statiques (inutile d'instancier la structure pour vous en servir) :

- `AliceBlue` : R:240 G:248 B:255 A:255.
- `AntiqueWhite` : R:250 G:235 B:215 A:255.
- `Aqua` : R:0 G:255 B:255 A:255.
- `Aquamarine` : R:127 G:255 B:212 A:255.
- `Azure` : R:240 G:255 B:255 A:255.
- `Beige` : R:245 G:245 B:220 A:255.
- `Bisque` : R:255 G:228 B:196 A:255.
- `Black` : R:0 G:0 B:0 A:255.
- `BlanchedAlmond` : R:255 G:235 B:205 A:255.
- `Blue` : R:0 G:0 B:255 A:255.
- `BlueViolet` : R:138 G:43 B:226 A:255.
- `Brown` : R:165 G:42 B:42 A:255.
- `BurlyWood` : R:222 G:184 B:135 A:255.
- `CadetBlue` : R:95 G:158 B:160 A:255.
- `Chartreuse` : R:127 G:255 B:0 A:255.
- `Chocolate` : R:210 G:105 B:30 A:255.
- `Coral` : R:255 G:127 B:80 A:255.
- `CornflowerBlue` : R:100 G:149 B:237 A:255.
- `Cornsilk` : R:255 G:248 B:220 A:255.
- `Crimson` : R:220 G:20 B:60 A:255.
- `Cyan` : R:0 G:255 B:255 A:255.
- `DarkBlue` : R:0 G:0 B:139 A:255.
- `DarkCyan` : R:0 G:139 B:139 A:255.
- `DarkGoldenrod` : R:184 G:134 B:11 A:255.
- `DarkGray` : R:169 G:169 B:169 A:255.
- `DarkGreen` : R:0 G:100 B:0 A:255.
- `DarkKhaki` : R:189 G:183 B:107 A:255.
- `DarkMagenta` : R:139 G:0 B:139 A:255.
- `DarkOliveGreen` : R:85 G:107 B:47 A:255.
- `DarkOrange` : R:255 G:140 B:0 A:255.
- `DarkOrchid` : R:153 G:50 B:204 A:255.
- `DarkRed` : R:139 G:0 B:0 A:255.
- `DarkSalmon` : R:233 G:150 B:122 A:255.
- `DarkSeaGreen` : R:143 G:188 B:139 A:255.
- `DarkSlateBlue` : R:72 G:61 B:139 A:255.
- `DarkSlateGray` : R:47 G:79 B:79 A:255.
- `DarkTurquoise` : R:0 G:206 B:209 A:255.
- `DarkViolet` : R:148 G:0 B:211 A:255.
- `DeepPink` : R:255 G:20 B:147 A:255.
- `DeepSkyBlue` : R:0 G:191 B:255 A:255.
- `DimGray` : R:105 G:105 B:105 A:255.
- `DodgerBlue` : R:30 G:144 B:255 A:255.
- `Firebrick` : R:178 G:34 B:34 A:255.
- `FloralWhite` : R:255 G:250 B:240 A:255.
- `ForestGreen` : R:34 G:139 B:34 A:255.
- `Fuchsia` : R:255 G:0 B:255 A:255.
- `Gainsboro` : R:220 G:220 B:220 A:255.
- `GhostWhite` : R:248 G:248 B:255 A:255.
- `Gold` : R:255 G:215 B:0 A:255.
- `Goldenrod` : R:218 G:165 B:32 A:255.
- `Gray` : R:128 G:128 B:128 A:255.
- `Green` : R:0 G:128 B:0 A:255.
- `GreenYellow` : R:173 G:255 B:47 A:255.
- `Honeydew` : R:240 G:255 B:240 A:255.
- `HotPink` : R:255 G:105 B:180 A:255.
- `IndianRed` : R:205 G:92 B:92 A:255.
- `Indigo` : R:75 G:0 B:130 A:255.
- `Ivory` : R:255 G:255 B:240 A:255.
- `Khaki` : R:240 G:230 B:140 A:255.
- `Lavender` : R:230 G:230 B:250 A:255.
- `LavenderBlush` : R:255 G:240 B:245 A:255.
- `LawnGreen` : R:124 G:252 B:0 A:255.
- `LemonChiffon` : R:255 G:250 B:205 A:255.
- `LightBlue` : R:173 G:216 B:230 A:255.
- `LightCoral` : R:240 G:128 B:128 A:255.
- `LightCyan` : R:224 G:255 B:255 A:255.
- `LightGoldenrodYellow` : R:250 G:250 B:210 A:255.
- `LightGray` : R:211 G:211 B:211 A:255.
- `LightGreen` : R:144 G:238 B:144 A:255.
- `LightPink` : R:255 G:182 B:193 A:255.
- `LightSalmon` : R:255 G:160 B:122 A:255.
- `LightSeaGreen` : R:32 G:178 B:170 A:255.
- `LightSkyBlue` : R:135 G:206 B:250 A:255.
- `LightSlateGray` : R:119 G:136 B:153 A:255.
- `LightSteelBlue` : R:176 G:196 B:222 A:255.
- `LightYellow` : R:255 G:255 B:224 A:255.
- `Lime` : R:0 G:255 B:0 A:255.
- `LimeGreen` : R:50 G:205 B:50 A:255.
- `Linen` : R:250 G:240 B:230 A:255.
- `Magenta` : R:255 G:0 B:255 A:255.
- `Maroon` : R:128 G:0 B:0 A:255.
- `MediumAquamarine` : R:102 G:205 B:170 A:255.
- `MediumBlue` : R:0 G:0 B:205 A:255.
- `MediumOrchid` : R:186 G:85 B:211 A:255.
- `MediumPurple` : R:147 G:112 B:219 A:255.
- `MediumSeaGreen` : R:60 G:179 B:113 A:255.
- `MediumSlateBlue` : R:123 G:104 B:238 A:255.
- `MediumSpringGreen` : R:0 G:250 B:154 A:255.
- `MediumTurquoise` : R:72 G:209 B:204 A:255.
- `MediumVioletRed` : R:199 G:21 B:133 A:255.
- `MidnightBlue` : R:25 G:25 B:112 A:255.
- `MintCream` : R:245 G:255 B:250 A:255.
- `MistyRose` : R:255 G:228 B:225 A:255.
- `Moccasin` : R:255 G:228 B:181 A:255.
- `NavajoWhite` : R:255 G:222 B:173 A:255.
- `Navy`: R:0 G:0 B:128 A:255.
- `OldLace` : R:253 G:245 B:230 A:255.
- `Olive` : R:128 G:128 B:0 A:255.
- `OliveDrab` : R:107 G:142 B:35 A:255.
- `Orange` : R:255 G:165 B:0 A:255.
- `OrangeRed` : R:255 G:69 B:0 A:255.
- `Orchid` : R:218 G:112 B:214 A:255.
- `PaleGoldenrod` : R:238 G:232 B:170 A:255.
- `PaleGreen` : R:152 G:251 B:152 A:255.
- `PaleTurquoise` : R:175 G:238 B:238 A:255.
- `PaleVioletRed` : R:219 G:112 B:147 A:255.
- `PapayaWhip` : R:255 G:239 B:213 A:255.
- `PeachPuff` : R:255 G:218 B:185 A:255.
- `Peru` : R:205 G:133 B:63 A:255.
- `Pink` : R:255 G:192 B:203 A:255.
- `Plum` : R:221 G:160 B:221 A:255.
- `PowderBlue` : R:176 G:224 B:230 A:255.
- `Purple` : R:128 G:0 B:128 A:255.
- `Red` : R:255 G:0 B:0 A:255.
- `RosyBrown` : R:188 G:143 B:143 A:255.
- `RoyalBlue` : R:65 G:105 B:225 A:255.
- `SaddleBrown` : R:139 G:69 B:19 A:255.
- `Salmon` : R:250 G:128 B:114 A:255.
- `SandyBrown` : R:244 G:164 B:96 A:255.
- `SeaGreen` : R:46 G:139 B:87 A:255.
- `SeaShell` : R:255 G:245 B:238 A:255.
- `Sienna` : R:160 G:82 B:45 A:255.
- `Silver` : R:192 G:192 B:192 A:255.
- `SkyBlue` : R:135 G:206 B:235 A:255.
- `SlateBlue` : R:106 G:90 B:205 A:255.
- `SlateGray` : R:112 G:128 B:144 A:255.
- `Snow` : R:255 G:250 B:250 A:255.
- `SpringGreen` : R:0 G:255 B:127 A:255.
- `SteelBlue` : R:70 G:130 B:180 A:255.
- `Tan` : R:210 G:180 B:140 A:255.
- `Teal` : R:0 G:128 B:128 A:255.
- `Thistle` : R:216 G:191 B:216 A:255.
- `Tomato` : R:255 G:99 B:71 A:255.
- `Transparent` : R:0 G:0 B:0 A:0.
- `Turquoise` : R:64 G:224 B:208 A:255.
- `Violet` : R:238 G:130 B:238 A:255.
- `Wheat` : R:245 G:222 B:179 A:255.
- `White` : R:255 G:255 B:255 A:255.
- `WhiteSmoke` : R:245 G:245 B:245 A:255.
- `Yellow` : R:255 G:255 B:0 A:255.
- `YellowGreen` : R:154 G:205 B:50 A:255.

## Remplir la fenêtre avec une couleur

Utilisez la méthode `Clear` du membre `GraphicsDevice` de la classe `Game` en passant la couleur en argument.

```csharp
GraphicsDevice.Clear(couleur);
```

## Afficher une image

Commencez par ajouter l'espace de nom `Microsoft.Xna.Framework.Graphics` pour pouvoir accéder aux classes `SpriteBatch` et `Texture2D` :

```csharp
using Microsoft.Xna.Framework.Graphics;
```

Dans votre projet, créez un dossier `Content` au même emplacement que vos fichiers sources. Copiez un fichier image dans ce dossier.

Dans le constructeur de la classe `FNAGame` après avoir instancié le gestionnaire de matériel graphique (`GraphicsDeviceManager`), utilisez la propriété `Content` pour définir le dossier contenant vos ressources.

```csharp
Content.RootDirectory = "Content";
```

Dans la classe `FNAGame`, ajoutez les membres suivants :

```csharp
private SpriteBatch spriteBatch;
private Texture2D image;
```

- La classe `SpriteBatch` permet d'afficher des sprites par lot pour économiser des appels de dessin (*draw calls*). Cela permet d'améliorer les performances de votre jeu.
- La classe `Texture2D` représente une ressource graphique (une image).

Dans la méthode `LoadContent` de la classe `FNAGame`, instanciez le `SpriteBatch` et chargez l'image :

```csharp
spriteBatch = new SpriteBatch(GraphicsDevice);
image = Content.Load<Texture2D>("image.png");
```

Dans la méthode `UnloadContent` de la classe `FNAGame`, libérez le `SpriteBatch` et la `Texture2D` :

```csharp
spriteBatch.Dispose();
image.Dispose();
```

**Attention !** Pensez bien à libérer la mémoire. D'une manière générale, si vous utilisez la méthode `LoadContent` pour charger des ressources, vous devrez probablement utiliser la méthode `UnloadContent` pour libérer la mémoire.

Dans la méthode `Draw` de la classe `FNAGame`, utiliser le `SpriteBatch` pour afficher l'image :

```csharp
base.Draw(gameTime);
GraphicsDevice.Clear(Color.CornflowerBlue);

spriteBatch.Begin();
spriteBatch.Draw(image, Vector2.Zero, Color.White);
spriteBatch.End();
```

**Remarque :** Le `SpriteBatch` vous permet de dessiner plusieurs textures (images) en un seul appel de dessin (*draw call*). C'est pourquoi vous devez placer un maximum de vos méthodes `Draw` entre les méthodes `Begin` et `End`.

La méthode `Draw` de la classe `SpriteBatch` a la signature suivante :

```csharp
spriteBatch.Draw(texture, position, couleur);
```

Les paramètres sont les suivants :

- `texture` : l'image (de type `Texture2D`) à afficher.
- `position` : la position (de type `Vector2`) où afficher l'image à l'écran. L'image est placée sur l'écran en se basant sur le coin supérieur gauche de l'image.
- `couleur` : la couleur (de type `Color`) avec laquelle l'image est fusionnée pour être affichée. Par défaut, utilisez la couleur blanche (`Color.White`) pour éviter de dénaturer l'image. 

**Attention !** Le projet est prêt à être compilé mais une erreur va se produire à l'exécution car le jeu ne trouve pas les ressources. En effet, vous devez dupliquer le dossier de ressources (`Content`) à la racine de l'exécutable de votre jeu.

Copiez votre dossier `Content` dans le sous-dossier `bin/debug`. Vous pouvez maintenant compiler et exécuter votre jeu.

### Code complet

Voici un exemple de code complet affichant une image appelée `sword.png` :

```csharp
using Microsoft.Xna.Framework;
using Microsoft.Xna.Framework.Graphics;

class FNAGame : Game
{
	private SpriteBatch batch;
	private Texture2D texture;

	public FNAGame()
	{
		new GraphicsDeviceManager(this);
		Content.RootDirectory = "Content";
	}

	protected override void Initialize()
	{
		base.Initialize();
	}

	protected override void LoadContent()
	{
		base.LoadContent();
		batch = new SpriteBatch(GraphicsDevice);
		texture = Content.Load<Texture2D>("sword.png");
	}

	protected override void UnloadContent()
	{
		base.UnloadContent();
		batch.Dispose();
		texture.Dispose();
	}

	protected override void Update(GameTime gameTime)
	{
		base.Update(gameTime);
	}

	protected override void Draw(GameTime gameTime)
	{
		base.Draw(gameTime);
		GraphicsDevice.Clear(Color.CornflowerBlue);

		batch.Begin();
		batch.Draw(texture, Vector2.Zero, Color.White);
		batch.End();
	}
}
```

## Déplacer une image



## Contrôles



## Collisions


