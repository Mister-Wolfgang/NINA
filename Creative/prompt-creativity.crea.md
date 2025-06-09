````instructions
# Référentiel P.R.I.M.A. - Documentation Complète

## Vue d'Ensemble
Ce référentiel centralise l'ensemble des ressources, outils et méthodologies utilisées dans l'écosystème Prima Golf pour optimiser la génération de prompts et l'efficacité du développement. Il suit la méthodologie P.R.I.M.A. (Personnage, Résultat, Intention, Mission, Audience) pour une approche structurée et professionnelle.

---

## 📋 Framework P.R.I.M.A.

### Générateur de Prompts Expert
**Fichier** : [`PRIMA.instructions.md`](./PRIMA.instructions.md)

**Description** : Framework principal pour la création de prompts exceptionnels utilisant la méthodologie P.R.I.M.A.

**Composants** :
- **Personnage** : Expert en ingénierie de prompts LLM (20+ ans d'expérience)
- **Résultat** : Prompts ultra-détaillés et précis
- **Intention** : Éliminer toute ambiguïté dans les instructions IA
- **Mission** : Processus en 4 phases (Collecte → Analyse → Génération → Validation)
- **Audience** : Professionnels cherchant l'excellence en IA

**Workflow** :
1. Collecte des préférences utilisateur
2. Analyse et structuration
3. Génération du prompt P.R.I.M.A.
4. Validation et optimisation

---

## 🔧 Outils MCP VSCode

### Guide de Référence Complet
**Fichier** : [`mcp.references.md`](./mcp.references.md)

**Description** : Documentation exhaustive des outils MCP (Model Context Protocol) disponibles dans l'environnement VSCode pour maximiser l'efficacité du développement.

#### 🔍 Exploration et Recherche
- **`semantic_search`** : Recherche intelligente dans le codebase
- **`file_search`** : Recherche de fichiers par pattern glob
- **`grep_search`** : Recherche textuelle précise
- **`list_code_usages`** : Analyse d'utilisation des symboles

#### 📁 Gestion des Fichiers
- **`read_file`** : Lecture avec plages de lignes
- **`create_file`** : Création de nouveaux fichiers
- **`insert_edit_into_file`** : Insertions intelligentes
- **`replace_string_in_file`** : Remplacements précis avec contexte

#### 🖥️ Terminal et Exécution
- **`run_in_terminal`** : Exécution avec contexte persistant
- **`get_terminal_output`** : Récupération des sorties background

#### 🔧 Développement VSCode
- **`run_vs_code_task`** : Exécution de tâches définies
- **`create_and_run_task`** : Création dynamique de tâches
- **`get_errors`** : Analyse des erreurs de compilation

#### 📓 Jupyter Notebooks
- **`create_new_jupyter_notebook`** : Génération de notebooks
- **`edit_notebook_file`** : Modification de cellules
- **`run_notebook_cell`** : Exécution de cellules

#### 🌐 Web et Navigation
- **`open_simple_browser`** : Prévisualisation web intégrée
- **`fetch_webpage`** : Extraction de contenu web

---

## 🔌 Serveurs MCP Disponibles

### Serveurs Actifs dans l'Environnement

#### `@bbangjooo/mcp-finder-mcp-server` ⭐ **130 utilisations**
- **Description** : MCP Finder and Installer
- **Usage** : Découverte et connexion aux serveurs MCP
- **Outils disponibles** :
  - `bb7_find_mcp` : Découverte des serveurs MCP
  - `bb7_install_mcp` : Installation de nouveaux serveurs
- **Homepage** : https://github.com/bbangjooo/mcp-installer

#### `@chenmingkong/bilibili-mcp-server` - **44 utilisations**
- **Description** : Bilibili API Server
- **Usage** : Accès à l'API Bilibili pour recherche et récupération de données
- **Fonctionnalités** : Recherche utilisateurs, vidéos, streams, articles

### Serveurs Disponibles (Non Installés)

#### `@sergey-fintech/MCP`
- **Description** : File Finder - Recherche de fichiers par fragments de texte
- **Usage** : Recherche avancée de fichiers

#### `@zxfgds/mcp-code-indexer`
- **Description** : 代码索引器 - Améliore les capacités de recherche de code des LLM
- **Usage** : Recherche sémantique et analyse de code

#### `@PowerPrincipal/wxmd`
- **Description** : 微信 Markdown 编辑器 - Éditeur Markdown pour WeChat
- **Usage** : Conversion Markdown vers format WeChat

#### `@ChaplinLittleJenius/eladmin-mp`
- **Description** : ELADMIN后台管理系统 - Système de gestion backend
- **Usage** : Construction rapide de systèmes d'administration

---

## 🎯 Cas d'Usage Prima Golf

### Développement React Native
```markdown
1. semantic_search("components React Native navigation")
2. read_file("/Prima-NATIVE/src/components/Navigation.js", 0, 50)
3. insert_edit_into_file("nouveau hook useSlotLocking")
```

### Migration de Fonctionnalités
```markdown
1. file_search("**/*LockedSlot*.js")
2. list_code_usages("useSlotLocking")
3. create_file("Prima-NATIVE/src/hooks/useSlotLocking.js")
```

### Debug et Tests
```markdown
1. run_in_terminal("npm test -- --coverage")
2. get_errors(["/Prima-NATIVE/src/test/booking.test.js"])
3. replace_string_in_file("correction du test")
```

### Gestion MCP
```markdown
1. bb7_find_mcp("*") // Découvrir tous les serveurs
2. bb7_install_mcp("@zxfgds/mcp-code-indexer", "cursor") // Installation
3. bb7_find_mcp("zxfgds") // Vérifier l'installation
```

---

## 🚀 Workflows Recommandés

### 1. Exploration de Code
```
semantic_search → file_search → read_file → list_code_usages
```

### 2. Développement de Fonctionnalités
```
semantic_search → create_file → insert_edit_into_file → run_in_terminal → get_errors
```

### 3. Debug et Correction
```
get_errors → read_file → replace_string_in_file → run_vs_code_task
```

### 4. Documentation Interactive
```
create_new_jupyter_notebook → edit_notebook_file → run_notebook_cell
```

---

## 💡 Bonnes Pratiques

### Recherche Efficace
- **Commencer par** `semantic_search` pour le contexte général
- **Utiliser** `file_search` pour les patterns spécifiques  
- **Finaliser avec** `grep_search` pour les correspondances exactes

### Édition Sécurisée
- **Toujours lire** avant d'éditer avec `read_file`
- **Utiliser des commentaires** `// ...existing code...` dans `insert_edit_into_file`
- **Inclure 3-5 lignes de contexte** pour `replace_string_in_file`

### Debugging Intelligent
- **Combiner** `get_errors` et `run_in_terminal` pour un diagnostic complet
- **Utiliser** `get_terminal_output` pour les processus background
- **Créer des tâches réutilisables** avec `create_and_run_task`

### Gestion MCP
- **Découvrir régulièrement** avec `bb7_find_mcp("*")`
- **Installer selon les besoins** avec `bb7_install_mcp`
- **Privilégier les serveurs populaires** (ex: @bbangjooo avec 130 utilisations)

---

## 📚 Structure des Instructions

### Framework Principal
```
.github/instructions/frameworks/
├── PRIMA.instructions.md                     # Générateur P.R.I.M.A.
├── PRIMA.references.md                       # Ce fichier de référence
└── mcp.references.md # Guide outils MCP
```

### Instructions Spécialisées
```
.github/instructions/
├── development-workflow/
│   ├── code-review.instructions.md
│   ├── copilot-code-generation.instructions.md
│   ├── git-commit-message.instructions.md
│   ├── jira-ticket-analysis.instructions.md
│   └── pull-request-description.instructions.md
├── audit/
│   └── expo-project-audit-craft-sadique.instructions.md
└── migration/
    └── [fichiers de migration]
```

---

## 🔄 Évolution et Maintenance

### Mise à Jour des Outils MCP
- **Vérification mensuelle** : `bb7_find_mcp("*")` pour découvrir nouveaux serveurs
- **Évaluation d'usage** : Analyser les `useCount` pour identifier les outils populaires
- **Installation ciblée** : Installer uniquement les serveurs pertinents pour Prima Golf

### Amélioration Continue
- **Feedback utilisateur** : Intégrer les retours d'expérience développeurs
- **Patterns émergents** : Documenter les nouveaux workflows efficaces
- **Optimisation** : Réviser régulièrement les bonnes pratiques

---

## 📞 Support et Ressources

### Liens Utiles
- **MCP Finder** : https://github.com/bbangjooo/mcp-installer
- **Documentation VSCode** : Outils natifs intégrés
- **Prima Golf Ecosystem** : Workspace multi-projets (MASTER, API, COMMON, WEB, NATIVE)

### Contact
- **Maintenance** : Julien MOULIN (602a4807ddba8b0070292fdc)
- **Issues** : Via tickets Jira Prima Golf
- **Améliorations** : Pull requests dans .github/instructions/

---

*Ce référentiel suit la méthodologie P.R.I.M.A. pour une efficacité maximale dans l'écosystème Prima Golf.*

**Dernière mise à jour** : 10 juin 2025  
**Version** : 1.1.0 - Documentation référentielle
````
