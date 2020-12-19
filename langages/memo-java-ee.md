# Mémo Java EE

par *flashjaysan*

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

## Liens

[Evolution de Java EE](https://www.baeldung.com/java-enterprise-evolution)

[Les changements apportés par Jakarta EE](https://developers.redhat.com/blog/2019/09/12/jakarta-ee-8-the-new-era-of-java-ee-explained/)

## Java Persistence API (JPA)

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


































