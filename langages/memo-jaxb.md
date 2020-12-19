# Memo JAXB

par *flashjaysan*

## Terminologie

- *marshall* : Conversion d'une classe Java vers un document *XML*.
- *unmarshall* : Conversion d'un document *XML* vers une classe Java.
- *DTD (Document Type Definition)* : Définit la structure d'un document SGML. Utilisé pour vérifier la validité d'un document.
- *Schema* : Définit la structure d"un document *XML*. Utilisé pour vérifier la validité d'un document *XML*. Equivalent *XML* d'un *DTD*.

## XML

- Sensible à la casse.
- Une balise doit toujours être fermée. `<balise>contenu</balise>` ou `<balise />`.
- Une valeur d'attribut est toujours entre guillemets. `<balise attribut="valeur" />`.
- Un attribut doit toujours avoir une valeur.
- Il est conseillé de commencer un document *XML* par une en-tête. `<?xml version="1.0" encoding="UTF-8" ?>`.
- L'en-tête peut être suivi d'une définition de type de document (*DTD*). `<!DOCTYPE web-app PUBLIC "-//Sun Microsystems, Inc.//DTD Web Application 2.2//EN" "HTTP://java.sun.com/j2ee/dtds/web-app_2_2.dtd">`. Un DTD définit la structure du document *XML*.
- L'élément racine contient tous les autres éléments.
- `<!-- commentaire -->` est un commentaire. Il ne doit pas y avoir deux tirets consécutifs dans le commentaire.

## Attribut ou élément ?

Une bonne idée de départ est de définir des attributs pour modifier l'interprétation d'une valeur, pas pour spécifier une valeur. Par défaut, utlisez des éléments.

## convertir un fichier XML en document

Un document est une représentation en mémoire d'un arbre du document *XML*. Il est composé de classes qui implémentent l'interface `Node`.

Vous aurez besoin d'un `DocumentBuilder` que vous pouvez obtenir avec un `DocumentBuilderFactory`.

```java
DocumentBuilderFactory factory = DocumentBuilderFactory.newInstance();
documentBuilder builder = factory.newDocumentBuilder();
```

Vous pouvez alors lire un document à partir d'un fichier :

```java
File file = ...;
Document document = builder.parse(file);
```

Vous pouvez aussi utiliser une URL :

```java
URL url = ...;
Document document = builder.parse(url);
```

Vous pouvez aussi utiliser un flux d'entrée :

```java
InputStream inputStream = ...;
Document document = builder.parse(inputStream);
```

Commencez par analyser le contenu du document :

```java
Element root = document.getDocumentElement();
```

Cela renvoie l'élément racine du document.

La méthode `getTagName` renvoie le nom de la balise de l'élément sous forme de chaîne.

```java
String rootName = root.getTagName();
```

La méthode `getChildNodes` renvoie une `NodeList` des éléments enfants du noeud.

```java
NodeList children = root.getChildNodes();
for (int i = 0; i < children.getLength(); ++i) {
    Node child = children.item(i);
    ...
}
```

**Attention !** Les espaces du document *XML* sont interprétés comme des noeuds enfants. Pour éviter cela, vérifiez que les enfants sont bien des sous-éléments de l'élément parent.

```java
for (int i = 0; children.getLength(); ++i) {
    Node child = children.item(i);
    if (child instanceof Element) {
        var childElement = (Element) child;
        ...
    }
}
```

Si le document possède un *DTD*, le parseur supprime automatiquement les espaces.

Pour les éléments sans enfants, vous pouvez utiliser la méthode `getFirstChild`. Si ces éléments encadrent un texte, ils sont du type `Text`. Vous pouvez utiliser la méthode `getData` de ce type pour récupérer la donnée. Utilisez la méthode `trim` pour supprimer les espaces autour de la donnée.

```java
for (int i = 0; children.getLength(); ++i) {
    Node child = children.item(i);
    if (child instanceof Element) {
        var childElement = (Element) child;
        var textnode = (Text) childElement.getFirstChild();
        String text = textNode.getData().trim();
        if (childElement.getTagName().equals("name"))
            name = text;
        else if (childElement.getTagName().equals("size"))
            size = Integer.parseInt(text);
    }
}
```

La méthode `getLastChild` renvoie le dernier noeud enfant. La méthode `getNextSibling` renvoie le noeud suivant d'un noeud enfant.

Le code suivant permet de parcourir tous les noeuds enfants d'un même niveau.

```java
for (Node childNode = element.getFirstChild(); childNode != null; childNode = childNode.getNextSibling()) {
    ...
}
```










## JAXB

Les *Marshallers* et les *Unmarshallers* sont créés au travers d'une instance `JAXBContext`.




