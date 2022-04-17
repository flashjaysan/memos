# Mémo Wildfly

## Terminologie

*Java EE* (dernièrement renommé *Jakarta EE* pour des raisons de droit d'utilisation du terme *Java*) est un ensemble de *spécifications* *standardisées* d'*API*, d'*architecture distribuée* et de méthodes de *packaging* et de *déploiement* des *composants*.
Java EE fournit un ensemble de *services* s'exécutant sur un *serveur d'application* qui implémente les *spécifications*. Pour qu'un serveur d'application soit reconnu compatible Java EE, il doit implémenter la totalité des spécifications.
Java EE fournit des *services* s'exécutant sur des *composants* placés dans des *conteneurs*.

## Définitions

- J2EE : Nom de la spécification Java EE de Java 1.2 à Java 1.4. 1999 - 2006.
- Java EE : Nom de la spécification Java EE de Java 5 à la migration du projet d'Oracle à Eclispe Foundation. 2006 - 2017.
- Jakarta EE : Depuis la migration vers Eclipse Foundation (depuis 2017).
- Java Community Process (JCP) : Système de propositions d'améliorations de Java.
- Java Specification Request (JSR) : né d'un JCP, c'est un ensemble de spécifications d'une technologie particulière.
- Glassfish : Implémentation de référence (serveur d'application) de la spécification Java EE.
- Technology Compatibility Kit (TCK) : Ensemble de tests visant à éprouver la validité d'un serveur d'application compatible Java EE. Un serveur d'application compatible doit passer tous les tests de validation.
- Un serveur d'application certifié Java EE fournit toutes les implémentations des diverses spécifications de Java EE.
  - IBM propose Websphere.
  - Sun puis Oracle proposent Glassfish (qui est également l'implémentation de référence des spécifications).
  - Redhat propose JBOSS et Wildfly.
- Une servlet est une application qui s'exécute sur un serveur HTTP. Tomcat et Apache font partie de cette catégorie.
- Les API de la spécification Java EE se groupent en trois catégories :
  - Les composants : EJB, servletes, JSP.
  - Les services : JDBC, JTA/JTS, JNDI, JCA, JAAS.
  - La communication : RMI-IIOP, JMS, Java mail.
- Un EJB (ou Entreprise Java Bean) est un composant de conteneur JEE qui permet soit de gérer des services, soit de gérer des entités.
- Un EJB entité manage les données. Relation à la base de données.
- Un EJB de session est l'exposition d'un service en local ou en remote. Son implémentation est une interface et/ou une classe concrète qui présente des services qui peuvent être consommés localement (avec l'annotation `@Local`) ou à distance (avec l'annotation `@Remote`). Les services sont sans état (avec l'annotation `@Stateless`) ou avec sauvegarde de l'état (avec l'annotation `@Statefull`).
- L'annotation `@Local` indique que le service est appelé depuis la même instance de JVM. Elle se met sur la classe ou l'interface de l'implémentation du service.
- L'annotation `@Remote` indique que le service est appelé en dehors de la JVM.  Elle se met sur la classe ou l'interface de l'implémentation du service. C'est ce qui est exposé à l'extérieur du système. Le service exposé à l'extérieur ne doit pas exposer de données internes.
- L'annotation `@Stateless` est la plus utilisée car elle est moins couteuses sur la machine. Le service est partagé par tous les consommateurs. Elle se met sur la classe ou l'interface qui expose le service.
- L'annotation `@Statefull` stocke toutes les informations en mémoire. Il y a une notion d'état tant que le client est connecté. Elle se met sur la classe ou l'interface qui expose le service.
- Une classe peut à la fois porter l'annotation `@Stateless` ou `@Statefull` et l'annotation `@Local` ou `@Remote`.
- L'annotation `@EJB` se met sur un membre d'une classe service. Cela indique au serveur d'application de générer automatiquement une instance. Inutile de l'instancier manuellement avec `new`. Il n'y a pas besoin de faire de lookup gràce à cette annotation.
- DTO (ou Data Transfer Object) est également appelé POJO (ou Plain Old Java Object). C'est une classe utilisée pour le transfert d'objet. Un DTO est un POJO mais tous les POJO ne sont pas des DTO.
- Un Manager est une classe qui manipule les données. Il doit être mis en local.
- DAO ou Data Access Object est une classe qui est la représentation objet d'une table située dans une base de donnée. Elle est utilisée localement contrairement au DTO qui est destiné à être exposé à l'extérieur.
- ORM ou Object Relational Model est la technique de mapping entre le modèle d'une base de donnée et le modèle objet. L'objectif est d'utiliser un médiateur entre les deux modèles pour gérer automatiquement cette transformation de l'un vers l'autre.

**Quelques principes :**

- On ne fournit jamais la structure des entités aux utilisateurs.
- Il faut laisser un maximum la main au serveur. 
- Il faut préférer la gestion automatique des transactions.

## Liens

[Evolution de Java EE](https://www.baeldung.com/java-enterprise-evolution)

[Les changements apportés par Jakarta EE](https://developers.redhat.com/blog/2019/09/12/jakarta-ee-8-the-new-era-of-java-ee-explained/)

## Wildfly

### Principe de déploiement de Java EE

- Un JAR (ou Java ARchive) est une bibliothèque de classes ou EJB.
- Un WAR (ou Web ARchive) est destiné au web et peut contenir des JAR dans la partie lib.
- Un EAR (Entreprise ARchive) est le modèle entreprise et peut contenir des JAR et des WAR.

Dans un Tomcat, les JAR ne sont pas exécutés en tant que web application mais ils sont exécutés pour rendre service à autre chose.

Pour déployer un projet, il faut déposer l'EAR sur le serveur d'application.

Pour JBOSS, pour le démarrage, on peut être en mode *domain* ou en mode *standalone*.

- Le mode *domain* indique qu'il y a un serveur maître et deux esclaves. En mode *cluster*.
- Le mode *standalone* indique qu'il n'y a qu'un serveur. En mode *farm*.

### Installer et démarrer Wildfly directement

- Téléchargez la version 18 de Wildfly sur [le site officiel](https://wildfly.org/downloads/).
- Décompressez l'archive à l'emplacement de votre choix. Prenez soin de noter cet emplacement.
- Pour lancer le serveur d'application sur Windows, exécutez le fichier `standalone.bat` situé dans le dossier `bin`.
- Pour fermer le serveur, appuyez sur `CTRL+C` puis saisissez `O` et validez.

### Créer un compte administrateur pour Wildfly

- Sur Windows, placez-vous dans le dossier `bin` de Wildfly puis dans la barre d'adresse de l'explorateur de fichiers, saisissez `cmd` puis validez. Cela ouvre une console à cet emplacement. Exécutez le fichier `add-user.bat`.
- Saisissez `a` pour ajouter un compte administrateur (*Management User*) puis validez.
- Saisissez le nom d'utilisateur du compte puis validez.
- Saisissez un mode de passe pour ce compte puis validez.
- Si besoin confirmez ou recommencez en suivant les recommendations.
- Saisissez un nom de groupe à associer au compte ou laissez le champ vide puis validez.
- Saisissez `yes` pour finaliser la création du compte.
- Saisissez `yes` à la dernière question (je ne sais pas trop ce que ça fait).

### Se connecter à l'administration du serveur via navigateur

- Démarrez Wildfly.
- Utilisez votre navigateur pour vous rendre à l'adresse `localhost:9990/console`.
- Saisissez l'identifiant et le mot de passe du compte administrateur puis validez.
- Vous êtes désormais connecté à Wildfly. La section `Deployments` indique quels projets sont déployés dans Wildfly.

### Installer le plugin Wildfly dans Eclipse

- Cliquez sur le menu `Help -> Eclipse Marketplace...`.
- Dans l'onglet `Search`, dans le champ `Find`, Saisissez `` puis cliquez sur le bouton `Go`.
- Cliquez sur le bouton `Install` du plugin `JBoss Tools 4.13.0.Final`.
- Une fois l'installation terminée, fermez la fenêtre.

### Configurer Eclipse pour Wildfly

- Cliquez sur le menu `Window -> Preferences`.
- Dans le menu `Web Services -> Server and Runtime`, sélectionnez `Wildfly 18` dans le menu déroulant `Server runtime`.
- Sélectionnez `JBossWS` dans le menu déroulant `Web service runtime`.

### Ouvrir la perspective JBOSS

- Cliquez sur le menu `Window -> Perspective -> Other Perspective -> Other...`.
- Sélectionnez `JBoss` puis cliquez sur le bouton `Open`.

### Sélectionner le serveur d'application Wildfly

- Dans l'onglet `Servers`, cliquez sur le texte `No servers are available.Click this link to create a new server...` ou faites un clic droit dans la fenêtre et choisissez `New -> Server` pour associer un nouveau serveur d'application à Eclipse.
- Sélectionnez `Wildfly 18` puis cliquez sur le bouton `Next`.
- cliquez sur le bouton `Next`.
- Si la fenêtre vous demande de sélectionner un runtime, cliquez sur le bouton `Browse` de la section `Home Directory` et sélectionnez l'emplacement (le dossier racine) où vous avez décompressé l'archive Wildfly.
- Cliquez sur le bouton `Finish`.

### Démarrer Wildfly depuis Eclipse

- Dans l'onglet `Servers` de la perspective `JBoss`, faites un clic droit sur le serveur Wildfly et sélectionnez `Start` ou cliquez sur le bouton en forme de flèche verte dans la fenêtre.
- Pour stopper le serveur, faites un clic droit sur le serveur et sélectionnez `Stop` ou cliquez sur le bouton en forme de carré rouge dans la fenêtre.

### Télécharger un modèle de projet vide pour Wildfly

Parfois vous ne pourrez pas générer automatique de projet Wildfly. Vous pouvez télécharger un modèle tout prêt sur Internet. Un modèle de projet Wildfly est appelé un archétype.

- Allez à l'adresse suivante : [https://github.com/wildfly/wildfly-archetypes/](https://github.com/wildfly/wildfly-archetypes/).
- Dans la page, cliquez sur le menu déroulant `Branch: master`. Cliquez sur l'onglet `Tags` puis sélectionnez `18.0.0.Final`.
- Cliquez sur le bouton `Clone or download` et copiez l'[URI fournie](https://github.com/wildfly/wildfly-archetypes.git).

### Importer l'archétype de projet Wildfly dans Eclipse 

- Dans Eclipse, cliquez sur le menu `File -> Import...`.
- Sélectionnez l'option `Git -> Projects from Git` puis cliquez sur `Next`.
- Sélectionnez l'option `Clone URI` puis cliquez sur `Next`.
- Dans le champ `URI`, collez l'URI récupéré dans la section précédente puis cliquez sur `Next`.
- Laissez les options par défaut et cliquez sur `Next`.
- Dans le champ `Directory`, sélectionnez un emplacement vide puis cliquez sur `Next`.
- A la fin du téléchargement du projet, vérifiez que le sélecteur `Import as general project` est sélectionné puis cliquez sur `Next`.
- Dans le champ `Project name`, définissez un nom de projet puis cliquez sur `Finish`.

Le projet apparait dans le panneau `Project Explorer`.

### Définir la version de Wildfly et la nature du projet

- Faites un clic droit sur le projet et choisissez l'option `Team -> Switch To -> Other...`.
- Sélectionnez l'option `Tags -> 18.0.0.Final` puis cliquez sur le bouton `Check Out`.
- Cliquez sur le bouton `Close`.
- Faites un clic droit sur le projet et choisissez l'option `Configure -> Convert to Maven Project`.

### Tester l'archétype

- Faites un clic droit sur le projet et choisissez l'option `Run As -> Maven build...`.
- Dans le champ `Goals`, saisissez `clean install` puis cliquez sur `Run`.
- Vous pouvez désormais utiliser cet archétype en tant que squelette de base de votre projet Java EE.

### Créer un projet de base avec Eclipse

Vous pouvez créer un squelette de base pour votre projet Java EE directement depuis Eclipse.

- Cliquez sur le menu `File -> New -> Other...`.
- Sélectionnez l'option `Maven -> Maven Project` puis cliquez sur `Next`.
- Laissez les options par défaut et cliquez sur `Next`.
- Dans le champ `Filter` saisissez `wildfly`.
- Dans la colonne `ArtifactId` sélectionnez `wildfly-jakartaee-ear-archetype` et de version `18.0.0.Final` puis cliquez sur `Next`.
- Dans le champ `GroupId`, saisissez le nom du package de votre projet.
- Dans le champ `ArtifactId`, saisissez le nom de votre projet.
- Cliquez sur le bouton `Finish`.
- Quatre nouveaux projets apparaissent dans le panneau `Project Explorer`. Les projets `-ear`, `-ejb` et `-web` sont des projets virtuels qui font référence au projet principal (le projet sans extension). Ces projets contiennent chacun un fichier `pom.xml` qui hérite du fichier `pom.xml` du projet général.

**Remarque :** Si `wildfly-jakartaee-ear-archetype` n'apparait pas dans la liste, suivez la procédure suivante :
- Cliquez sur le bouton `Add archetype`.
- Dans le champ `GroupId`, saisissez `org.wildfly.archetype`.
- Dans le champ `ArtifactId`, saisissez `wildfly-jakartaee-ear-archetype`.
- Dans le champ `Archetype Version`, saisissez `18.0.0.Final`.
- cliquez sur `Next`.

### Déployer un projet sur Wildfly

- Dans l'onglet `Servers` de la perspective `JBoss`, faites un clic droit sur le serveur et sélectionnez `Add and Remove...`.
- Sléectionnez le projet `-ear` à gauche que vous souhaitez ajouter au serveur et cliquez sur le bouton `Add` pour le faire passer à droite. Cliquez ensuite sur le bouton `Finish`.
- Dans le dossier `standalone` où vous avez décompressé Wildfly, le projet doit apparaitre.

**Attention !** Lorsque vous faites une modification du projet à déployer, vous devez à nouveau le déployer sur le serveur. Dans le panneau `Servers`, dépliez le serveur et faites un clic droit sur le projet déployé dans la liste. Choisissez l'option `Full Publish`.

## Services, EJB de session et DTO

### Créer deux packages pour séparer les accès

Dans le dossier `src/main/java`, créez un package `pub` (le mot clé `public` étant déjà réservé) où vous placerez vos interfaces accessibles de l'extérieur (en *remote*).

Créez également un package `internal` (le mot clé `private` étant déjà réservé) où vous placerez vos classes et interfaces dont vous souhaitez limiter l'accès à la même instance de JVM (en *local*).

### Exposer un service de type `Remote`

Dans le package `pub`, créez une interface `ServiceRemote` avec l'annotation `@Remote` et ajoutez-lui une méthode abstraite publique.

```java
import javax.ejb.Remote;

@Remote
public interface ServiceRemote {
	
	public String ping();

}
```

Dans le package `internal`, créez une classe `Service` avec l'annotation `@Stateless` qui implémente l'interface `ServiceRemote` et implémentez les méthodes de cette interface.

```java
import javax.ejb.Stateless;
import monpackage.pub.ServiceRemote;

@Stateless
public class Service implements ServiceRemote {

	@Override
	public String ping() {
		return "pong";
	}
	
}
```

### Tester le service de type `Remote`

Dans le dossier `src/test/java`, créez une classe de test qui appelle la méthode de l'interface `Service`.

```java
import monpackage.pub.ServiceRemote;

public class PingTester {
	
	@Test
	public void testPing() {
		ServiceRemote service = new Service();
		assertEquals("pong", service.ping());
	}

}
```

### Exposer un service de type `Local`

Dans l'interface `ServiceRemote` du package `pub`, ajoutez une nouvelle méthode abstraite publique.

```java
import javax.ejb.Remote;

@Remote
public interface ServiceRemote {
	
	public String ping();
  public String hello();

}
```

Dans le package `internal`, créez une nouvelle classe `ServiceLocal` avec les annotation `@Stateless` et `@Local`. Ajoutez-lui une méthode
qui renvoie un objet du type de la méthode que vous avez ajoutée à l'étape précédente.

```java
import javax.ejb.Local;
import javax.ejb.Stateless;

@Local
@Stateless
public class ServiceLocal {
	
	public String greeting() {
		return "hello";
	}

}
```

Dans la classe `Service` du package `internal`, créez un membre privé de type `ServiceLocal` avec l'annotation `@EJB` puis implémentez la méthode manquante de l'interface `ServiceRemote` en appelant la méthode du membre `ServiceLocal`.

```java
import javax.ejb.Stateless;
import monpackage.pub.ServiceRemote;

@Stateless
public class Service implements ServiceRemote {
  
	@EJB
	private ServiceLocal serviceLocal;

	@Override
	public String ping() {
		return "pong";
	}

  public String hello() {
    return serviceLocal.greeting();
  }
	
}
```

### Tester le service de type `Local`

Dans le dossier `src/test/java`, dans la classe de test, accédez à la méthode précédente.

```java
import monpackage.pub.ServiceRemote;

public class PingTester {
	
	@Test
	public void testPing() {
		ServiceRemote service = new Service();
		assertEquals("pong", service.ping());
    assertEquals("hello", service.hello());
	}

}
```

## Java Persistence API (JPA)

Une application devrait être conçue autour de classes et pas de la représentation des données dans une base de données.

La JPA permet de se simplifier la vie pour éviter de tout faire à la main. Il est cependant préférable de connaître le fonctionnement classique pour l'utiliser à bon escient.



L'annotation `@Entity` sur une classe indique qu'elle doit être sauvegardée par le gestionnaire de sauvegarde de données (l'`EntityManager`).

```java
import javax.persistence.Entity;

@Entity
public class SomeClass {

}
```

Par défaut, l'entité crée porte le nom de la classe mais vous pouvez également la redéfinir via l'attribut `name`.

```java
@Entity(name="entityName")
public class SomeClass {

}
```

En plus de l'annotation `@Entity` sur une classe, vous pouvez utiliser l'annotation `@Table(name="nom_de_table")` pour définir le nom de la table associée dans la base de données.

- `@Entity(name="entityName")` indique que `entityName` sera utilisé pour nommer l'entité.
- `@Table(name="table_name")`  indique que `table_name` sera utilisé pour nommer le nom de la table associée dans la base de données. Sans cette annotation, la table prend le nom défini dans l'annotation `@Entity` ou le nom de la classe.

```java
import javax.persistence.Table;

@Entity(name="entityName")
@Table(name="table_name")
public class SomeClass {

}
```

L'annotation `@Id` sur un membre indique que ce dernier est une clé primaire de la table associée à la classe.

```java
import javax.persistence.Id;

@Entity
public class SomeClass {

    ...
    @Id
    private int id;
    ...

}
```

L'annotation `@OneToOne` sur un membre indique que ce dernier à une relation un pour un avec cette classe.

```java
import javax.persistence.OneToOne;

@Entity
public class Personne {

    ...
    @OneToOne
    private Adresse adresse;
    ...

}
```
Toutes les relations en Java et JPA sont unidirectionnelles. Vous devez ajouter un attribut `mappedBy` sur un des liens pour préciser à JPA qu'il y a un retour de lien à faire. 

Sur le membre de l'autre classe de la relation un pour un, comme vous avez déjà défini cette relation dans la première classe, vous devez définir le membre associé avec l'attribut `mappedBy`.

```java
@Entity
public class Adresse {

    ...
    @OneToOne(mappedBy="adresse")
    private Personne personne;
    ...

}
```

L'annotation `@ManyToOne` sur un membre indique que ce dernier a une relation plusieurs pour un avec cette classe.

L'annotation `@OneToMany` sur un membre indique que ce dernier a une relation un pour plusieurs avec cette classe.

Vous devez définir le membre avec l'annotation `@ManyToOne` avec l'attribut `inversedBy` et le membre avec l'annotation `OneToMany` avec l'attribut `mappedBy`.

```java
import javax.persistence.ManyToOne;

@Entity
public class Adresse {

    ...
    @ManyToOne(inversedBy="adresse")
    private Pays pays;
    ...

}

@Entity
public class Pays {

    ...
    @OneToMany(mappedBy="pays")
    private Adresse adresse;
    ...

}
```

L'annotation `@JoinColumn(name="ADRESSEID", insertable=false, updatable=false)` sur un membre indique que ??????.

```java
import javax.persistence.JoinColumn;

@Entity
public class SomeClass {

    ...
    @JoinColumn(name="ADRESSEID", insertable=false, updatable=false)
    private String rue;
    ...

}
```

L'annotation `@PersistenceContext(unitName="miniprojetPersistenceUnit")` sur un membre de type `EntityManager` indique que le serveur d'application doit injecter automatiquement un gestionnaire de sauvegarde de donnée (`EntityManager`).

L'attribut `unitName` doit avoir la valeur indiquée dans la ligne `<persistence-unit name="miniprojetPersistenceUnit">` située dans le fichier `src/main/resources/META-INF/persistence.xml`.

```java
import javax.ejb.Local;
import javax.ejb.Stateless;
import javax.persistence.EntityManager;
import javax.persistence.PersistenceContext;

@Local
@Stateless
public class PersonneDAO {
	
	// persistence = sauvegarde de données
	// injection d'un gestionnaire de persistence dans cette classe
	@PersistenceContext(unitName="miniprojetPersistenceUnit")
	private EntityManager entityManager;
	
	public void creerPersonne(int id, String prenom, String nom) {
		Personne p = new Personne();
		p.setId(id);
		p.setPrenom(prenom);
		p.setNom(nom);
	}
	
	public Personne getPersonneById(int id) {
		return (Personne) entityManager
				.createQuery("SELECT p FROM Personne p WHERE p.id=:id")
				.setParameter("id", id)
				.getSingleResult();
	}
	
	public Personne getPersonneByAdresse(Adresse adresse) {
		return (Personne) entityManager
				.createQuery("SELECT p FROM Personne p WHERE p.adresse=:adresse")
				.setParameter("adresse", adresse)
				.getSingleResult();
	}

}
```

L'annotation `@WebService` indique que ????????.
L'annotation `@SOAPBinding` indique que ?????.

```java
import javax.ejb.EJB;
import javax.ejb.Stateless;
import javax.jws.WebService;
import javax.jws.SOAPBinding;
import fr.aliptic.wildfly.miniprojet.pub.MonServiceRemoteA;

@Stateless(name="ServiceMetier")
@WebService
@SOAPBinding(style=SOAPBinding.Style.RPC)
public class MonServiceA implements MonServiceRemoteA {
	
	@EJB
	private MonServiceB serviceB;
	
	@EJB
	private PersonneDAO manager;

	@Override
	public String ping() {
		return "pong";
	}
	
	public String date() {
		return serviceB.donnerDate();
	}
	
	public void creerPersonne() {
		manager.creerPersonne(007, "Jacques", "Le gentil");
	}
	
}
```
