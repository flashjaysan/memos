# Mémo FNA

Par *flashjaysan* avec l'aide d'*IronPowerLNA*

## Présentation

[FNA](https://fna-xna.github.io/) est une bibliothèque [FOSS](https://itsfoss.com/what-is-foss/) (libre et open source) destinée à la programmation de jeux vidéos en langage C#. Dans un but de préservation, elle est conçue pour répliquer à l'identique la bibliothèque [Microsoft XNA Game Studio 4.0 Refresh](https://en.wikipedia.org/wiki/Microsoft_XNA) qui n'est désormais plus maintenue.

## Ressources

Comme FNA est une réimplémentation libre d'XNA, la [documentation pour XNA](http://msdn.microsoft.com/en-us/library/bb200104.aspx) ainsi que toutes les ressources disponibles concernant XNA sont totalement compatibles avec FNA. De nombreux ouvrages ont été publiés pour apprendre XNA et on trouve en ligne de nombreuses ressources.

## Installation

### Installer Visual Studio

Commencez par installer [Visual Studio](https://visualstudio.microsoft.com/). Pensez bien à installer dans l'onglet `Charges de travail`, section `Bureau et mobile`, les outils pour le `Développement .NET Desktop`.

### Générer la DLL de FNA

- Téléchargez l'archive la plus récente de FNA ainsi que l'archive des bibliothèques natives à l'adresse [https://fna-xna.github.io/download/](https://fna-xna.github.io/download/).
- Dézippez ces deux fichiers archives à l'emplacement de votre choix.
- Ouvrez le projet `FNA.csproj` dans Visual Studio.
- En haut de la fenêtre de Visual Studio, dans la barre d'outils, sélectionnez l'option `Release` dans le menu déroulant `Configurations de solutions`.
- Dans l'explorateur de solutions, faites un clic droit sur la solution et sélectionnez `Générer la solution`. Un message doit afficher que la génération a réussi. Un fichier `FNA.dll` vient d'être créé.
- Toujours dans l'explorateur de solutions, faites un clic droit sur le projet et sélectionnez `Ouvrir le dossier dans l'Explorateur de fichiers`. Un explorateur de fichiers s'ouvre à l'emplacement du projet.
- Allez dans le sous-dossier `bin/release` et récupérez le fichier `FNA.dll`.
- Vous pouvez fermer le projet.

### Créer un projet

Dans Visual Studio, créer un projet `Application Console .NET Framework`.

#### Ajouter FNA

Vous devez préciser au compilateur que le projet a une dépendance à FNA. Cela lui permet de reconnaître la bibliothèque (et de vous donner accès à Intellisense pour FNA), et de configurer l'éditeur de liens.

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
using (Game g = new Game())
{
    new GraphicsDeviceManager(g);
    g.Run();
}
```

Le code minimal est le suivant :

```csharp
using Microsoft.Xna.Framework;

static class Program
{
	static void Main(string[] args)
	{
		using (Game g = new Game())
		{
			new GraphicsDeviceManager(g);
			g.Run();
		}
	}
}
```

En haut de la fenêtre de Visual Studio, dans la barre d'outils, cliquez sur le bouton `Demarrer` pour compiler et exécuter le projet. L'exécution provoque une erreur mais le but de cette manipulation était de créer un dossier avec les fichiers exécutables.

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
using (FNAGame g = new FNAGame())
{
    g.Run();
}
```

Cliquez sur le bouton `Demarrer` pour exécuter le projet. Pour l'instant, vous avez les mêmes fonctionnalités que précédemment. Ajoutez maintenant les méthodes suivantes à la classe `FNAGame` :

```csharp
using Microsoft.Xna.Framework;

class FNAGame : Game
{
	public FNAGame()
	{
		GraphicsDeviceManager gdm = new GraphicsDeviceManager(this);

		gdm.PreferredBackBufferWidth = 1280;
		gdm.PreferredBackBufferHeight = 720;
		gdm.IsFullScreen = false;
		gdm.SynchronizeWithVerticalRetrace = true;
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
		GraphicsDevice.Clear(Color.CornflowerBlue);
		base.Draw(gameTime);
	}
}
```

Cliquez sur le bouton `Demarrer` pour exécuter le projet. Une jolie fenêtre bleue s'affiche. Vous avez maintenant des méthodes à votre disposition pour créer votre jeu.
