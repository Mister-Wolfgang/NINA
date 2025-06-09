````instructions
# Référence des Outils MCP pour VSCode

## Vue d'ensemble
Cette référence détaille les outils MCP (Model Context Protocol) disponibles dans l'environnement VSCode pour maximiser l'efficacité du développement. Ces outils permettent d'interagir avec le workspace, les fichiers, les terminaux, et les services externes.

---

## 🔍 Exploration et Recherche

### `semantic_search`
**Usage** : Recherche intelligente dans le codebase  
**Cas d'usage** : 
- Trouver des fonctions par description
- Localiser des patterns de code similaires
- Comprendre l'architecture avant modifications

```markdown
Exemple : "rechercher les composants React Native utilisant des hooks de géolocalisation"
```

### `file_search`
**Usage** : Recherche de fichiers par pattern glob  
**Cas d'usage** :
- Localiser tous les fichiers d'un type (`**/*.tsx`)
- Trouver des fichiers par convention de nommage
- Explorer la structure de dossiers

### `grep_search`
**Usage** : Recherche textuelle précise  
**Cas d'usage** :
- Trouver des chaînes exactes
- Localiser des imports spécifiques
- Identifier des patterns regex

### `list_code_usages`
**Usage** : Analyser l'utilisation d'un symbole  
**Cas d'usage** :
- Audit avant refactoring
- Comprendre les dépendances
- Vérifier l'impact des changements

---

## 📁 Gestion des Fichiers

### `read_file`
**Usage** : Lecture de contenu avec plages de lignes  
**Cas d'usage** :
- Analyser le code avant modification
- Comprendre la structure existante
- Extraire des sections spécifiques

### `create_file`
**Usage** : Création de nouveaux fichiers  
**Cas d'usage** :
- Nouveaux composants/services
- Fichiers de configuration
- Documentation

### `insert_edit_into_file`
**Usage** : Insertions intelligentes de code  
**Cas d'usage** :
- Ajout de nouvelles méthodes
- Extension de composants existants
- Insertion de fonctionnalités

**Bonnes pratiques** :
```javascript
// Utiliser des commentaires pour le contexte
class ExistingComponent {
  // ...existing code...
  
  newMethod() {
    // nouveau code ici
  }
  
  // ...existing code...
}
```

### `replace_string_in_file`
**Usage** : Remplacement précis avec contexte  
**Cas d'usage** :
- Corrections de bugs
- Mise à jour de configurations
- Refactoring ciblé

**Bonnes pratiques** :
- Inclure 3-5 lignes de contexte
- S'assurer de l'unicité du pattern
- Préserver l'indentation

---

## 🖥️ Terminal et Exécution

### `run_in_terminal`
**Usage** : Exécution de commandes avec contexte persistant  
**Cas d'usage** :
- Build et compilation
- Tests automatisés
- Déploiement
- Installation de dépendances

**Paramètres clés** :
- `isBackground: true` pour serveurs/watch modes
- `explanation` pour documenter l'action

### `get_terminal_output`
**Usage** : Récupération des sorties de processus background  
**Cas d'usage** :
- Monitoring de builds
- Vérification de statuts serveur
- Capture de logs

---

## 🔧 Développement VSCode

### `run_vs_code_task`
**Usage** : Exécution de tâches définies  
**Cas d'usage** :
- Builds configurés
- Tests spécifiques
- Scripts de déploiement

### `create_and_run_task`
**Usage** : Création dynamique de tâches  
**Cas d'usage** :
- Automatisation de workflows
- Configuration de builds personnalisés
- Intégration d'outils externes

### `get_errors`
**Usage** : Analyse des erreurs de compilation  
**Cas d'usage** :
- Debugging post-édition
- Validation de syntaxe
- Identification de problèmes

---

## 📓 Jupyter Notebooks

### `create_new_jupyter_notebook`
**Usage** : Génération de notebooks interactifs  
**Cas d'usage** :
- Prototypage d'algorithmes
- Analyse de données
- Documentation interactive

### `edit_notebook_file`
**Usage** : Modification de cellules  
**Cas d'usage** :
- Mise à jour de code d'analyse
- Corrections de documentation
- Ajout de visualisations

### `run_notebook_cell`
**Usage** : Exécution de cellules  
**Cas d'usage** :
- Tests d'algorithmes
- Validation de résultats
- Debugging interactif

---

## 🔗 Services Externes & APIs

### Serveurs MCP Atlassian `bb7_confluence_*` / `bb7_jira_*`
**Usage** : Intégration complète avec l'écosystème Atlassian  
**Cas d'usage** :
- Gestion documentaire Confluence (création, modification, recherche)
- Gestion de tickets Jira (création, transition, recherche JQL)
- Synchronisation des workflows Prima Golf avec la documentation

**Configuration testée** :
- URL Confluence : https://aps-management.atlassian.net/wiki
- URL Jira : https://aps-management.atlassian.net/
- Utilisateur : julien.moulin@primagolf.fr

### Serveurs MCP Exa AI `bb7_web_search_exa` / `bb7_research_paper_search` 
**Usage** : Recherche et analyse de contenu web avancée  
**Cas d'usage** :
- Veille technologique et concurrentielle
- Recherche d'articles académiques  
- Analyse de sites web et documentation
- Découverte de repositories GitHub

**Outils disponibles** :
- `bb7_web_search_exa` : Recherche web générale
- `bb7_research_paper_search` : Papers académiques
- `bb7_company_research` : Analyse d'entreprises
- `bb7_crawling` : Extraction de contenu web
- `bb7_competitor_finder` : Analyse concurrentielle
- `bb7_linkedin_search` : Recherche LinkedIn
- `bb7_wikipedia_search_exa` : Recherche Wikipedia
- `bb7_github_search` : Recherche GitHub

### Serveurs MCP Knowledge Graph `bb7_*_graph` / `bb7_*_entities`
**Usage** : Gestion de mémoire persistante par graphe de connaissances  
**Cas d'usage** :
- Mémorisation des décisions architecturales
- Cartographie des relations entre composants Prima Golf
- Historique des évolutions techniques
- Gestion des dépendances inter-projets

**Fonctionnalités** :
- `bb7_create_entities` : Création d'entités
- `bb7_create_relations` : Création de relations
- `bb7_search_nodes` : Recherche dans le graphe
- `bb7_read_graph` : Lecture complète
- `bb7_open_nodes` : Accès direct aux nœuds

### Serveurs MCP Time `bb7_get_current_time` / `bb7_convert_time`
**Usage** : Gestion temporelle précise avec timezone Europe/Paris  
**Cas d'usage** :
- Synchronisation des salutations contextuelles
- Planification de tâches selon les heures de travail
- Conversion entre fuseaux horaires pour équipes distribuées
- Respect des pauses (12h-14h)

---

## 🔌 Serveurs MCP et Extensions

### `bb7_find_mcp`
**Usage** : Découverte des serveurs MCP disponibles  
**Cas d'usage** :
- Explorer les serveurs MCP installés
- Identifier les outils disponibles
- Audit de l'environnement MCP

**Exemple** :
```markdown
bb7_find_mcp("@bbangjooo") // Trouve tous les serveurs bbangjooo
bb7_find_mcp("*") // Liste tous les serveurs MCP disponibles
```

### `bb7_install_mcp`
**Usage** : Installation de nouveaux serveurs MCP  
**Cas d'usage** :
- Ajouter de nouvelles fonctionnalités
- Installer des outils spécialisés
- Étendre les capacités de développement

**Paramètres** :
- `qualifiedName` : Nom qualifié du serveur (ex: `@bbangjooo/mcp-finder-mcp-server`)
- `client` : Client cible (`cursor`, `claude`, `windsurf`, `cline`, `enconvo`, `witsy`)
- `config` : Configuration optionnelle

### Serveurs MCP Actifs dans l'Environnement
Configuration testée et validée le 10 juin 2025 :

#### `@bbangjooo/mcp-finder-mcp-server` 🔍 
- **Status** : ✅ Actif via @smithery/cli
- **Description** : MCP Finder and Installer avec profil remote-reptile
- **Usage** : Découverte et installation de serveurs MCP
- **Configuration** : Clé API et profil spécifique intégrés

#### `mcp/time` ⏰ **TESTÉ ✅**
- **Status** : ✅ Pleinement fonctionnel 
- **Description** : Time Server avec timezone Europe/Paris
- **Usage** : Récupération heure actuelle, conversion fuseaux horaires
- **Test validé** : 12h09 le 10/06/2025 - Synchronisation parfaite

#### `ghcr.io/sooperset/mcp-atlassian` 🏢 **TESTÉ ✅**
- **Status** : ✅ Connexion Jira/Confluence établie
- **Description** : Intégration Atlassian complète (aps-management.atlassian.net)
- **Fonctionnalités testées** :
  - ✅ Confluence : Recherche dans l'espace PC réussie
  - ✅ Jira : Connexion API validée
- **Utilisateur** : julien.moulin@primagolf.fr

#### `exa-mcp-server` 🌐 **TESTÉ ✅**
- **Status** : ✅ Recherche web opérationnelle
- **Description** : Moteur de recherche Exa AI avec 8 outils
- **Outils actifs** : web_search_exa, research_paper_search, company_research, crawling, competitor_finder, linkedin_search, wikipedia_search_exa, github_search
- **Test validé** : Recherche réussie avec tracking des coûts

#### `@jlia0/servers` 🧠 **TESTÉ ✅**
- **Status** : ✅ Knowledge Graph opérationnel
- **Description** : Serveur de mémoire par graphe de connaissances
- **Usage** : Gestion d'entités, relations, observations
- **Test validé** : Graphe initialisé et prêt à l'emploi

---

## 🎯 Cas d'Usage Prima Golf

### Développement React Native
```markdown
1. semantic_search("components React Native navigation")
2. read_file("/path/to/component.js", 0, 50)
3. insert_edit_into_file("nouveau hook useSlotLocking")
```

### Migration de fonctionnalités
```markdown
1. file_search("**/*LockedSlot*.js")
2. list_code_usages("useSlotLocking")
3. create_file("Prima-NATIVE/src/hooks/useSlotLocking.js")
```

### Debug et Tests
```markdown
1. run_in_terminal("npm test -- --coverage")
2. get_errors(["/path/to/test/file.test.js"])
3. replace_string_in_file("correction du test")
```

### Gestion MCP et Services
```markdown
1. bb7_get_current_time("Europe/Paris") // Heure actuelle précise
2. bb7_confluence_search("documentation Prima Golf") // Recherche Confluence  
3. bb7_jira_search("project = DEV AND status = 'In Progress'") // JQL Jira
4. bb7_web_search_exa("React Native performance optimization") // Recherche web
5. bb7_create_entities([{name: "Prima-NATIVE", type: "project"}]) // Knowledge Graph
```

### Documentation et Gestion Projet
```markdown
1. bb7_confluence_create_page("DEV", "Architecture Decision Record", content)
2. bb7_jira_create_issue("DEV", "Nouvelle fonctionnalité", "Task")
3. bb7_research_paper_search("mobile app performance patterns")
4. bb7_company_research("expo.dev") // Analyse de technologies
```

---

## 🚀 Workflow Recommandé

### 1. Exploration
- `semantic_search` pour comprendre le contexte
- `file_search` pour localiser les fichiers pertinents
- `read_file` pour analyser le code existant

### 2. Planification
- `list_code_usages` pour identifier les impacts
- `get_errors` pour vérifier l'état actuel

### 3. Implémentation
- `create_file` ou `insert_edit_into_file` pour les changements
- `run_in_terminal` pour tests et builds

### 4. Validation
- `get_errors` pour vérifier la syntaxe
- `run_vs_code_task` pour exécuter les tests
- `open_simple_browser` pour prévisualiser

---

## 💡 Bonnes Pratiques

### Recherche Efficace
- Commencer par `semantic_search` pour le contexte général
- Utiliser `file_search` pour les patterns spécifiques
- `grep_search` pour les correspondances exactes

### Édition Sécurisée
- Toujours lire avant d'éditer
- Utiliser des commentaires `// ...existing code...`
- Inclure suffisamment de contexte pour `replace_string_in_file`

### Debugging Intelligent
- Combiner `get_errors` et `run_in_terminal`
- Utiliser `get_terminal_output` pour les processus background
- Créer des tâches réutilisables avec `create_and_run_task`

### Gestion des Services Externes
- Utiliser `bb7_get_current_time` pour synchroniser les activités
- `bb7_confluence_search` pour retrouver la documentation existante
- `bb7_jira_search` avec JQL pour identifier les tickets liés
- `bb7_web_search_exa` pour la veille technologique

### Knowledge Graph et Mémoire
- Créer des entités pour chaque composant majeur de Prima Golf
- Établir des relations entre MASTER, API, COMMON, NATIVE
- Documenter les décisions architecturales importantes
- Maintenir l'historique des évolutions techniques

---

**Version** : 1.1.0 - Documentation mise à jour  
**Dernière révision** : 10 juin 2025  
**Optimisé pour** : Development Efficiency Prima Golf Ecosystem
````