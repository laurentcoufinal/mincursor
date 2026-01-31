# Commandes Maven principales

## Cycle de vie et phases

### clean
Supprime le répertoire `target` (artefacts de compilation).

```bash
mvn clean
```

### validate
Vérifie que le projet est correct et que toutes les informations nécessaires sont présentes.

```bash
mvn validate
```

### compile
Compile le code source du projet.

```bash
mvn compile
```

### test
Exécute les tests unitaires (ne compile ni package).

```bash
mvn test
```

### package
Crée le JAR ou WAR dans `target/` (compile + tests + packaging).

```bash
mvn package
```

### verify
Lance les vérifications pour valider que le package est valide.

```bash
mvn verify
```

### install
Installe l’artefact dans le dépôt local (`~/.m2/repository`).

```bash
mvn install
```

### deploy
Copie l’artefact vers un dépôt distant (release).

```bash
mvn deploy
```

---

## Combinaisons courantes

### Nettoyer et compiler

```bash
mvn clean compile
```

### Nettoyer, compiler et exécuter les tests

```bash
mvn clean test
```

### Nettoyer et créer le package (sans tests)

```bash
mvn clean package -DskipTests
```

### Nettoyer, packager et installer en local

```bash
mvn clean install
```

---

## Création de projet

### Projet à partir d’un archétype (quickstart Java)

```bash
mvn archetype:generate -DgroupId=com.example -DartifactId=mon-app -DarchetypeArtifactId=maven-archetype-quickstart -DinteractiveMode=false
```

### Projet web (servlet)

```bash
mvn archetype:generate -DgroupId=com.example -DartifactId=mon-webapp -DarchetypeArtifactId=maven-archetype-webapp -DinteractiveMode=false
```

---

## Dépendances et dépôts

### Télécharger les sources des dépendances

```bash
mvn dependency:sources
```

### Afficher l’arbre des dépendances

```bash
mvn dependency:tree
```

### Copier les dépendances dans un répertoire

```bash
mvn dependency:copy-dependencies -DoutputDirectory=lib
```

### Mettre à jour les plugins/dépendances (versions)

```bash
mvn versions:display-dependency-updates
```

---

## Exécution

### Exécuter la classe principale

```bash
mvn exec:java -Dexec.mainClass="com.example.Main"
```

### Exécuter l’application packagée (JAR exécutable)

```bash
java -jar target/mon-app-1.0-SNAPSHOT.jar
```

### Lancer le serveur embarqué (Jetty)

```bash
mvn jetty:run
```

### Lancer Tomcat embarqué

```bash
mvn tomcat7:run
```

---

## Utilitaires

### Nettoyer le cache local (répertoire `.m2`)

```bash
mvn dependency:purge-local-repository -DactTransitively=false -DreResolve=false
```

### Générer le site du projet

```bash
mvn site
```

### Compiler avec un profil actif

```bash
mvn clean package -Pprod
```

### Forcer la mise à jour des snapshots

```bash
mvn clean install -U
```

### Spécifier un fichier POM

```bash
mvn -f mon-pom.xml clean package
```

### Mode hors ligne (sans réseau)

```bash
mvn -o package
```
