# Guide d'utilisation (Mis à jour)

Ce guide explique comment utiliser efficacement le système Enhanced Memory Bank System (EMBS) pour Cursor.

## Concepts de base

Le système Enhanced Memory Bank System fournit des capacités de mémoire à court et long terme pour Cursor :

- **Mémoire à court terme** : Contexte spécifique à la session actif pendant la session de développement en cours
- **Mémoire à long terme** : Connaissances persistantes maintenues à travers toutes les sessions

Le système fonctionne en différents modes, chacun avec des comportements mémoire spécialisés :

- **THINK** : Mode d'exploration pour comprendre les problèmes
- **PLAN** : Mode de planification pour concevoir les solutions
- **IMPLEMENT** : Mode d'implémentation pour écrire du code
- **REVIEW** : Mode de révision pour analyser le code
- **DOCUMENT** : Mode de documentation pour mettre à jour la documentation

## Comprendre l'approche du système

Le système Enhanced Memory Bank System fonctionne avec les capacités de Cursor :

1. **L'IA lit et suit les règles** dans les fichiers .mdc
2. **L'IA demande à voir les fichiers de mémoire** lorsqu'ils sont pertinents
3. **Vous fournissez l'accès aux fichiers de mémoire** lorsque demandé
4. **Vous signalez les événements significatifs** pour déclencher les mises à jour de mémoire
5. **L'IA suggère des mises à jour de mémoire** que vous pouvez implémenter

Cette approche garantit que la mémoire persiste entre les sessions tout en travaillant dans l'environnement Cursor.

## Démarrage

### Vérifier l'état du système

Pour voir l'état actuel du système de mémoire :

```
/memory status
```

Cela affichera :
- État d'initialisation
- Mode opérationnel actuel
- Fichiers de mémoire disponibles
- Activités récentes

### Mettre à jour le résumé de votre projet

Commencez par définir votre projet :

```
/memory update long_term/project_brief.md "Your project description..."
```

Cela crée une fondation pour tout travail futur.

## Travailler avec les modes

### Changement de mode

Le changement de mode nécessite deux étapes :

1. **D'abord, sélectionnez le mode dans le menu déroulant de l'interface Cursor** :
   - Cliquez sur le sélecteur de mode dans l'interface de chat Cursor
   - Sélectionnez le mode désiré (THINK, PLAN, IMPLEMENT, REVIEW, DOCUMENT)

2. **Ensuite, confirmez le mode à l'IA** :
   ```
   /mode <mode_name>
   ```

Exemples :
- Sélectionnez "THINK" dans l'interface, puis tapez `/mode think`
- Sélectionnez "PLAN" dans l'interface, puis tapez `/mode plan`

L'IA vérifiera que le mode actuellement sélectionné correspond à votre commande avant de continuer.

### Workflows spécifiques aux modes

#### Mode THINK

À utiliser lors de l'exploration de problèmes et de la recherche de solutions :

```
# Après avoir sélectionné THINK dans l'interface
/mode think

# Explorer un sujet
/think explore authentication

# Comparer des approches
/think compare "JWT vs session auth"

# Rechercher un sujet spécifique
/think research "modern auth best practices"
```

#### Mode PLAN

À utiliser lors de la conception de plans d'implémentation :

```
# Après avoir sélectionné PLAN dans l'interface
/mode plan

# Créer un plan d'implémentation
/plan create user-authentication

# Valider par rapport à l'architecture
/plan validate

# Marquer le plan comme approuvé
/plan approve
```

#### Mode IMPLEMENT

À utiliser lors de l'écriture du code réel :

```
# Après avoir sélectionné IMPLEMENT dans l'interface
/mode implement

# Démarrer l'implémentation
/implement start user-authentication

# Enregistrer un point de contrôle
/implement checkpoint

# Marquer comme terminé
/implement complete
```

#### Mode REVIEW

À utiliser lors de l'analyse du code existant :

```
# Après avoir sélectionné REVIEW dans l'interface
/mode review

# Réviser un fichier spécifique
/review code src/auth/login.ts

# Générer des suggestions
/review suggest

# Marquer comme approuvé
/review approve
```

#### Mode DOCUMENT

À utiliser lors de la création de documentation :

```
# Après avoir sélectionné DOCUMENT dans l'interface
/mode document

# Mettre à jour la documentation
/document update api-docs

# Promouvoir la documentation temporaire
/document promote session_notes.md

# Valider la documentation
/document validate
```

## Commandes mémoire

### Commandes principales

- `/memory status` - Afficher l'état actuel du système de mémoire
- `/memory help` - Afficher les commandes mémoire disponibles

### Récupération de mémoire

- `/memory recall <context>` - Demander à voir un contexte mémoire spécifique
  ```
  /memory recall architecture
  /memory recall patterns
  /memory recall current_context
  ```
  L'IA vous demandera d'ouvrir le fichier pertinent.

### Mises à jour de mémoire

- `/memory update <file> <content>` - Suggérer des mises à jour pour un fichier mémoire spécifique
  ```
  /memory update decisions.md "Decision: We will use TypeScript"
  ```
  L'IA fournira du contenu formaté à ajouter au fichier.

- `/memory save <context>` - Sauvegarder les informations actuelles dans le contexte mémoire spécifié
  ```
  /memory save architecture
  /memory save patterns -t  # Save as temporary (short-term)
  ```
  L'IA suggérera du contenu à ajouter au fichier approprié.

### Organisation de la mémoire

- `/memory promote <source>` - Promouvoir la mémoire à court terme en mémoire à long terme
  ```
  /memory promote working_decisions.md
  ```
  L'IA suggérera quel contenu déplacer de la mémoire à court terme vers la mémoire à long terme.

- `/memory archive <file>` - Archiver une mémoire qui n'est plus pertinente
  ```
  /memory archive old_patterns.md
  ```
  L'IA fournira des instructions pour l'archivage.

- `/memory consolidate <files>` - Combiner des mémoires liées
  ```
  /memory consolidate auth_*.md authentication.md
  ```
  L'IA demandera à voir les fichiers sources, puis fournira le contenu consolidé.

### Recherche de mémoire

- `/memory search <query>` - Rechercher des informations dans la mémoire
  ```
  /memory search authentication
  /memory search -c architecture database  # Search in specific context
  ```
  L'IA demandera à voir les fichiers pertinents pour la recherche.

## Signalement d'événements

Étant donné que le système ne peut pas détecter automatiquement les événements, vous devez signaler les événements significatifs :

```
/memory event <event_type> <details>
```

Par exemple :
```
/memory event commit "Implemented user authentication"
```

Types d'événements courants :
- `commit` - Code commité dans le dépôt
- `build_success` - Build terminé avec succès
- `build_failure` - Build échoué
- `test_success` - Tests réussis
- `test_failure` - Tests échoués
- `create` - Nouveau fichier créé
- `modify` - Fichier modifié
- `branch` - Branche Git changée
- `session_start` - Début de session de développement
- `session_end` - Fin de session de développement

Lorsque vous signalez un événement, l'IA suggérera des mises à jour de mémoire appropriées basées sur le type d'événement.

## Annotations mémoire

Vous pouvez créer des annotations de code que l'IA reconnaît lorsqu'elle les voit :

```javascript
// @memory:note This approach handles edge cases better
function handleAuth() {
  // ...
}

// @memory:decision We're using JWT for authentication
const authType = 'jwt';

// @memory:pattern This pattern should be followed for all API routes
router.get('/api/:resource', authMiddleware, (req, res) => {
  // ...
});
```

Annotations disponibles :
- `@memory:note` - Pour session_notes.md
- `@memory:decision` - Pour decisions.md
- `@memory:pattern` - Pour patterns.md
- `@memory:architecture` - Pour architecture.md
- `@memory:todo` - Pour current_context.md
- `@memory:progress` - Pour progress.md

Lorsque l'IA voit ces annotations, elle suggérera des mises à jour de mémoire appropriées.

## Workflow orienté mémoire

Pour de meilleurs résultats, suivez ce workflow :

1. Commencez en **mode THINK** pour explorer les problèmes
2. Passez au **mode PLAN** pour concevoir les solutions
3. Passez au **mode IMPLEMENT** pour les changements de code
4. Utilisez le **mode REVIEW** pour analyser l'implémentation
5. Terminez avec le **mode DOCUMENT** pour mettre à jour la documentation

Tout au long de ce processus, signalez les événements significatifs et implémentez les mises à jour de mémoire suggérées pour maintenir la continuité entre les sessions.

## Bonnes pratiques

1. **Gardez les fichiers de mémoire focalisés** : N'essayez pas de tout mettre dans un seul fichier
2. **Utilisez une terminologie cohérente** : Soyez cohérent dans les noms et descriptions
3. **Révisez régulièrement la mémoire** : Vérifiez périodiquement les informations obsolètes
4. **Signalez les événements significatifs** : Utilisez le système de signalement d'événements de manière cohérente
5. **Implémentez les mises à jour suggérées** : Lorsque l'IA suggère des mises à jour de mémoire, implémentez-les
6. **Promouvez la mémoire à court terme importante** : Ne laissez pas les insights précieux rester temporaires
7. **Changez de mode délibérément** : Chaque mode a des forces spécifiques pour différentes tâches

## Dépannage

Si l'IA semble manquer de contexte :

1. Vérifiez si le fichier de mémoire existe :
   ```
   ls -la .cursor/memory/long_term/
   ```

2. Ouvrez le fichier pertinent lorsque demandé :
   ```
   cat .cursor/memory/long_term/patterns.md
   ```

3. Fournissez manuellement le contexte :
   ```
   /memory recall patterns
   ```

Si le système n'utilise pas le bon mode :

1. Vérifiez le mode actuel :
   ```
   /memory status
   ```

2. Réinitialisez le mode si nécessaire (n'oubliez pas de sélectionner dans l'interface d'abord) :
   ```
   /mode think
   ```
   
## Prochaines étapes

Explorez ces ressources supplémentaires :

- [COMMANDS.md](COMMANDS.md) - Référence complète des commandes
- [CUSTOM_MODES.md](CUSTOM_MODES.md) - Configuration des modes personnalisés
- [MEMORY_STRUCTURE.md](MEMORY_STRUCTURE.md) - Détails de la structure des fichiers de mémoire
- [EVENTS.md](EVENTS.md) - Documentation du système d'événements
