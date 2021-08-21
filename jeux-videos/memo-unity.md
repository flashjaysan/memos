# Mémo Unity

*par flashjaysan*

## Bases

Un projet Unity est constitué de scènes (au minimum une scène contenant une caméra (2D ou 3D)). Chaque scène est constitué d'une arborescence de game objects. Chaque game object contient des composants et au minimum un composant Transform avec des informations de position, de rotation et d'échelle.

La programmation des game objects se fait en leur attachant des scripts en C#. Ces scripts sont généralement des classes héritant de la classe MonoBehavior.

Cette classe définit les méthodes `Start` et `Update` associées à l'initialisation de la classe et son comportement à chaque affichage.

## Afficher un message dans la console

Utilisez la méthode `Debug.Log` pour afficher un message dans la console.

```csharp
Debug.Log("Message");
```

**Remarque :** Vous pouvez également utiliser la méthode `print` fournie par la classe `MonoBehavior`.

```csharp
// depuis une méthode d'une sous classe de MonoBehavior
print("Message");
```

## Créer un script

Faites un clic droit sur un emplacement vide de la vue  `Assets` située dans le panneau `Project` puis choisissez l'option `Create -> C# Script`.

## Attacher un script à un objet

Pour attacher un script à un objet, faites glisser le script depuis la vue `Assets` sur l'objet dans le panneau `Hierarchy` ou après avoir sélectionné l'objet, dans le panneau `Inspector`. 

## Déterminer si une touche du clavier est enfoncée

Utilisez la méthode `Imput.GetKeyDown` pour savoir si une touche du clavier est enfoncée. Passez à cette fonction la touche à surveiller via la classe `KeyCode`.


```csharp
if (Input.GetKeyDown(KeyCode.UpArrow)) {}
```



