# Mémo Unity

*par flashjaysan*

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



