# Mémo développement pour Android

par *flashjaysan*

## Concepts à retenir

Une application Android fournit plusieurs points d'entrée. Une application est composée de plusieurs composants qui peuvent être invoqués individuellement. Toucher l'icône d'une application, toucher une notification, ou même depuis une autre application peut servir à démarrer l'application.

Une application s'adapte à différents appareils. Vous pouvez fournir différentes ressources pour différents appareils. Vous pouvez fournir différents layouts pour différentes résolutions et le système s'adapte automatiquement à la résolution de l'appareil. Vous pouvez vérifier si un appareil possède un certain matériel (comme une caméra) à l'exécution. Vous pouvez même indiquer quels matériels sont nécessaires et faire que Google play bloquer l'installation si un matériel est manquant.

- Une activity est un type de composant qui fournit une interface utilisateur.
- Un service ou un broadcast receiver sont des types de composant qui peut exécuter une tâche en arrière plan.

## Créer un projet

- Installez et exécutez Android Studio.
- Dans l'écran de bienvenue, cliquez sur l'option `Start a new Android Studio project` ou, si vous avez un projet ouvert, cliquez sur le menu `File > New > New Project`.
- Dans la fenêtre `Choose your project`, sélectionnez une activité puis cliquez sur le bouton `Next`.
- Dans la fenêtre `Configure your project` :
  - Dans le champ `Name`, saisissez le nom de votre application.
  - Dans le champ `Package name`, saisissez le nom du package de votre application.
  - Dans le champ `Save location`, saisissez l'emplacement où stocker votre projet ou cliquez sur l'icône dossier à droite pour sélectionner l'emplacement dans un explorateur de fichiers.
  - Dans le menu déroulant `Language`, choisissez `Java` ou `Kotlin`.
  - Cochez la case `Use androidx.* artifacts`.
  - Cliquez sur le bouton `Finish`.

## Structure d'un projet

Commencez par afficher la vue `Android`.

- Pour afficher le panneau `Project`, cliquez sur le menu `View > Tool Windows > Project`.
- Pour sélectionner la vue `Android` dans le panneau `Project`, cliquez sur le menu déroulant en haut du panneau et sélectionnez `Android`.

Voici les fichiers importants :

`app -> java -> com.example.myfirstapp -> MainActivity` : C'est l'activité principale. C'est le point d'entrée de votre application. Lorsque vous construisez et exécutez votre application, le système démarre une instance de cette activité et charge son layout.
`app -> res -> layout -> activity_main.xml` : Ce fichier XML définit le layout pour l'interface utilisateur de l'activité.
`app -> manifests -> AndroidManifest.xml` : Ce fichier manifest décrit les caractéristiques fondamentales de l'application et définit chacun de ses composants.
`Gradle Scripts -> build.gradle` : Deux fichiers portent ce nom. Un pour le projet : "Project: nom d'application" et un pour le module app : "Module: app.". Chaque module a son propre fichier build.gradle associé pour contrôler comment le plugin Gradle construit votre application. Pour plus d'information sur ce fichier, consultez [Configure your build](https://developer.android.com/studio/build/index#module-level). 

## Exécuter votre application

Vous pouvez exécuter votre application sur un émulateur ou sur un appareil connecté.

### Exécuter votre application sur un appareil



### Exécuter votre application sur un émulateur
























