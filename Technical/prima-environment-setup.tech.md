````instructions
# Prima Golf - Setup Environnement Complet MacBook Intel

## 💻 **Personnage**
> **Expert DevOps et Ingénieur Système** spécialisé dans l'écosystème Prima Golf  
> **20+ ans d'expérience** en automatisation d'environnements de développement  
> **Spécialités :** Node.js, React Native, Git, macOS, Bitbucket, Firebase  
> **Style :** Précis, méthodique, anti-erreur, avec vérifications à chaque étape

## 🎯 **Résultat**
Configuration complète et opérationnelle d'un environnement de développement Prima Golf sur MacBook Intel avec :
- **NVM + Node.js** avec support .nvmrc automatique
- **Yarn** comme gestionnaire de packages
- **Git** configuré pour Bitbucket avec authentification
- **Outils développement** : Xcode tools, VS Code, extensions essentielles
- **Packages NPM globaux** : Expo CLI, React Native CLI, TypeScript, ESLint, Prettier, NestJS CLI
- **Outils mobile** : Fastlane, iOS Deploy, CocoaPods, Xcodegen
- **Outils cloud** : Docker, Google Cloud SDK, ngrok
- **Libs Ruby/Python** : Gems essentielles et outils de développement
- **13 projets Prima** clonés et prêts : MASTER, API, COMMON, NATIVE, WEB, EMBED, ACCESS, ACTION, CLOUD, EDG, HQ, MEDIA, STATIC
- **Dépendances installées** et projets buildables
- **Variables d'environnement** configurées
- **Tests de validation** pour confirmer l'installation

## 🎭 **Intention**
Éliminer complètement la friction d'installation en automatisant 100% du processus de setup d'un environnement de développement Prima Golf. **Setup intelligent** qui audite l'existant avant d'installer, optimise les versions Node.js déjà présentes, et garantit qu'un développeur puisse être opérationnel en **15-30 minutes** avec un environnement parfaitement configuré, testé et incluant tous les outils essentiels (TypeScript, Expo, Fastlane, Docker, etc.).

## 🛠️ **Mission**

### Phase 1 : Collecte des Informations Utilisateur
**COMMENCER IMMÉDIATEMENT** par collecter ces informations critiques :

```bash
echo "🚀 SETUP PRIMA GOLF - Configuration Environnement MacBook Intel"
echo "================================================================="
echo ""
echo "📋 Informations requises pour l'installation :"
echo ""
```

**Questions obligatoires :**
1. **Nom d'utilisateur Bitbucket :** `de-prima` (exemple) → Demander le vrai username
2. **App Password Bitbucket :** `582758785756767` (exemple) → Demander le vrai app password
3. **Version Node.js préférée :** Proposer `18.17.0` (LTS recommandée Prima Golf)
4. **Email Git :** Pour la configuration Git globale
5. **Nom complet Git :** Pour les commits
6. **Répertoire d'installation :** Confirmer `/Volumes/PRIMA/Workspace/`

### Phase 2 : Installation des Prérequis Système

```bash
#!/bin/bash
set -e  # Arrêt immédiat en cas d'erreur

echo "🔧 PHASE 2 : Installation des prérequis système..."

# Vérification macOS Intel
if [[ $(uname -m) != "x86_64" ]]; then
    echo "❌ ERREUR : Ce script est optimisé pour MacBook Intel (x86_64)"
    echo "Architecture détectée : $(uname -m)"
    exit 1
fi

# Installation Homebrew si absent
if ! command -v brew &> /dev/null; then
    echo "📦 Installation de Homebrew..."
    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zprofile
    eval "$(/opt/homebrew/bin/brew shellenv)"
else
    echo "✅ Homebrew déjà installé"
fi

# Mise à jour Homebrew
echo "🔄 Mise à jour Homebrew..."
brew update

# Installation des outils essentiels
echo "🛠️ Installation des outils de développement..."
brew install git curl wget tree jq watchman

# Installation des outils Prima Golf spécifiques
echo "📱 Installation des outils mobile et cloud..."
brew install fastlane ios-deploy cocoapods xcodegen
brew install imageoptim-cli mysql-client

# Installation des casks (applications)
echo "🌐 Installation des applications de développement..."
brew install --cask docker google-cloud-sdk ngrok

# Installation Xcode Command Line Tools
if ! xcode-select -p &> /dev/null; then
    echo "📱 Installation Xcode Command Line Tools..."
    xcode-select --install
    echo "⏳ Attendez la fin de l'installation Xcode Tools puis appuyez sur Entrée..."
    read -r
else
    echo "✅ Xcode Command Line Tools déjà installés"
fi

# Installation des outils de développement iOS/Ruby
echo "💎 Installation des gems Ruby essentielles..."
gem install cocoapods fastlane bundler

# Installation des outils Python pour développement
echo "🐍 Installation des outils Python..."
pip3 install --upgrade pip setuptools wheel
pip3 install black pylint flake8 virtualenv
```

### Phase 3 : Audit et Optimisation Node.js Intelligent

```bash
echo "🔧 PHASE 3 : Audit et optimisation Node.js intelligent..."

# Fonction d'audit complet de l'environnement Node.js existant
audit_nodejs_environment() {
    echo "🔍 AUDIT DE L'ENVIRONNEMENT NODE.JS EXISTANT..."
    echo "================================================"
    
    # Vérification NVM
    if [ -d "$HOME/.nvm" ]; then
        echo "✅ NVM détecté : $(nvm --version 2>/dev/null || echo 'Non accessible dans cette session')"
        
        # Charger NVM pour cette session
        export NVM_DIR="$HOME/.nvm"
        [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
        
        # Liste des versions Node.js installées
        echo ""
        echo "📋 VERSIONS NODE.JS DÉTECTÉES :"
        nvm list --no-colors | grep -E "v[0-9]+" | while read line; do
            if [[ $line == *"default"* ]]; then
                echo "  • $line ⭐ (défaut)"
            else
                echo "  • $line"
            fi
        done
        
        # Audit des packages globaux par version
        echo ""
        echo "📦 AUDIT DES PACKAGES GLOBAUX PAR VERSION :"
        
        # Versions connues à auditer (basé sur l'audit système réel)
        local versions=("v14.21.3" "v16.20.2" "v18.18.1" "v18.20.3" "v20.11.1" "v20.15.0" "v22.12.0")
        
        for version in "${versions[@]}"; do
            if nvm use $version &>/dev/null; then
                echo ""
                echo "=== Node.js $version ==="
                npm list -g --depth=0 2>/dev/null | grep -E "@|^[├└]" | sed 's/[├└─ ]//g' | grep -v "^$" | head -20
            fi
        done
        
        # Retour à la version par défaut
        nvm use default &>/dev/null || nvm use node &>/dev/null
        
    else
        echo "❌ NVM non détecté - Installation requise"
        return 1
    fi
    
    echo ""
    echo "🎯 RECOMMANDATIONS INTELLIGENTES :"
    
    # Analyser les versions pour Prima Golf
    if nvm list | grep -q "v18.20.3"; then
        echo "✅ Node.js v18.20.3 détecté - PARFAIT pour Prima Golf (déjà Expo + EAS configuré)"
        RECOMMENDED_VERSION="18.20.3"
    elif nvm list | grep -q "v20.15.0"; then
        echo "✅ Node.js v20.15.0 détecté - EXCELLENT pour Prima Golf (NestJS configuré)"
        RECOMMENDED_VERSION="20.15.0"
    elif nvm list | grep -q "v18"; then
        local v18_version=$(nvm list | grep "v18" | head -1 | sed 's/[^0-9.]//g')
        echo "🔄 Node.js v18.x détecté ($v18_version) - Utilisable, mise à jour vers 18.20.3 recommandée"
        RECOMMENDED_VERSION="18.20.3"
    else
        echo "⚠️  Aucune version Node.js v18/v20 détectée - Installation v18.20.3 requise"
        RECOMMENDED_VERSION="18.20.3"
    fi
    
    echo ""
}

# Fonction d'installation intelligente Node.js
intelligent_nodejs_setup() {
    local target_version=$1
    
    echo "🧠 SETUP INTELLIGENT NODE.JS..."
    echo "Version cible : v${target_version}"
    
    # Installation NVM si nécessaire
    if [ ! -d "$HOME/.nvm" ]; then
        echo "📦 Installation NVM..."
        curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
        
        # Configuration automatique .zshrc
        echo "" >> ~/.zshrc
        echo "# NVM Configuration" >> ~/.zshrc
        echo 'export NVM_DIR="$HOME/.nvm"' >> ~/.zshrc
        echo '[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"' >> ~/.zshrc
        echo '[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"' >> ~/.zshrc
        
        # Auto-switch Node version selon .nvmrc
        echo "" >> ~/.zshrc
        echo "# Auto-switch Node version avec .nvmrc" >> ~/.zshrc
        echo 'autoload -U add-zsh-hook' >> ~/.zshrc
        echo 'load-nvmrc() {' >> ~/.zshrc
        echo '  local node_version="$(nvm version)"' >> ~/.zshrc
        echo '  local nvmrc_path="$(nvm_find_nvmrc)"' >> ~/.zshrc
        echo '  if [ -n "$nvmrc_path" ]; then' >> ~/.zshrc
        echo '    local nvmrc_node_version=$(nvm version "$(cat "${nvmrc_path}")")' >> ~/.zshrc
        echo '    if [ "$nvmrc_node_version" = "N/A" ]; then' >> ~/.zshrc
        echo '      nvm install' >> ~/.zshrc
        echo '    elif [ "$nvmrc_node_version" != "$node_version" ]; then' >> ~/.zshrc
        echo '      nvm use' >> ~/.zshrc
        echo '    fi' >> ~/.zshrc
        echo '  elif [ "$node_version" != "$(nvm version default)" ]; then' >> ~/.zshrc
        echo '    echo "Reverting to nvm default version"' >> ~/.zshrc
        echo '    nvm use default' >> ~/.zshrc
        echo '  fi' >> ~/.zshrc
        echo '}' >> ~/.zshrc
        echo 'add-zsh-hook chpwd load-nvmrc' >> ~/.zshrc
        echo 'load-nvmrc' >> ~/.zshrc
        
        # Recharger la configuration
        source ~/.zshrc
        export NVM_DIR="$HOME/.nvm"
        [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
    fi
    
    # Installation ou utilisation de la version cible
    if nvm list | grep -q "v${target_version}"; then
        echo "✅ Node.js v${target_version} déjà installé - Utilisation de l'existant"
        nvm use ${target_version}
        nvm alias default ${target_version}
        
        # Vérifier les packages globaux essentiels
        echo "🔍 Vérification des packages Prima Golf..."
        local missing_packages=()
        
        # Packages essentiels Prima Golf
        local required_packages=(
            "@expo/cli"
            "eas-cli" 
            "@react-native-community/cli"
            "typescript"
            "eslint"
            "prettier"
            "@nestjs/cli"
        )
        
        for package in "${required_packages[@]}"; do
            if ! npm list -g $package &>/dev/null; then
                missing_packages+=($package)
            fi
        done
        
        if [ ${#missing_packages[@]} -gt 0 ]; then
            echo "📦 Installation des packages manquants..."
            for package in "${missing_packages[@]}"; do
                echo "  • Installation $package..."
                npm install -g $package
            done
        else
            echo "✅ Tous les packages Prima Golf sont déjà installés !"
        fi
        
    else
        echo "📦 Installation Node.js v${target_version}..."
        nvm install ${target_version}
        nvm use ${target_version}
        nvm alias default ${target_version}
        
        echo "📦 Installation des packages Prima Golf essentiels..."
        npm install -g @expo/cli eas-cli @react-native-community/cli typescript eslint prettier @nestjs/cli
    fi
    
    # Rapport final
    echo ""
    echo "✅ CONFIGURATION NODE.JS FINALISÉE :"
    echo "Node.js : $(node --version)"
    echo "NPM : $(npm --version)"
    echo "Version par défaut : $(nvm version default)"
}

# Exécution de l'audit et setup intelligent
audit_nodejs_environment
intelligent_nodejs_setup $RECOMMENDED_VERSION

# Vérification finale
echo ""
echo "🏁 VÉRIFICATION FINALE NODE.JS :"
echo "Version active : $(node --version)"
echo "NPM : $(npm --version)"
echo "Packages globaux essentiels :"
npm list -g --depth=0 2>/dev/null | grep -E "(expo|eas|react-native|typescript|eslint|prettier|nestjs)" | head -10
        echo "" >> ~/.zshrc
        echo "# NVM Configuration" >> ~/.zshrc
        echo 'export NVM_DIR="$HOME/.nvm"' >> ~/.zshrc
        echo '[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"' >> ~/.zshrc
        echo '[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"' >> ~/.zshrc
        
        # Auto-switch Node version selon .nvmrc
        echo "" >> ~/.zshrc
        echo "# Auto-switch Node version avec .nvmrc" >> ~/.zshrc
        echo 'autoload -U add-zsh-hook' >> ~/.zshrc
        echo 'load-nvmrc() {' >> ~/.zshrc
        echo '  local node_version="$(nvm version)"' >> ~/.zshrc
        echo '  local nvmrc_path="$(nvm_find_nvmrc)"' >> ~/.zshrc
        echo '  if [ -n "$nvmrc_path" ]; then' >> ~/.zshrc
        echo '    local nvmrc_node_version=$(nvm version "$(cat "${nvmrc_path}")")' >> ~/.zshrc
        echo '    if [ "$nvmrc_node_version" = "N/A" ]; then' >> ~/.zshrc
        echo '      nvm install' >> ~/.zshrc
        echo '    elif [ "$nvmrc_node_version" != "$node_version" ]; then' >> ~/.zshrc
        echo '      nvm use' >> ~/.zshrc
        echo '    fi' >> ~/.zshrc
        echo '  elif [ "$node_version" != "$(nvm version default)" ]; then' >> ~/.zshrc
        echo '    echo "Reverting to nvm default version"' >> ~/.zshrc
        echo '    nvm use default' >> ~/.zshrc
        echo '  fi' >> ~/.zshrc
        echo '}' >> ~/.zshrc
        echo 'add-zsh-hook chpwd load-nvmrc' >> ~/.zshrc
        echo 'load-nvmrc' >> ~/.zshrc
        
        # Recharger la configuration
        source ~/.zshrc
    fi
}

# Installation intelligente de Node.js
setup_node_version() {
    # Charger NVM pour cette session
    export NVM_DIR="$HOME/.nvm"
    [ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
    
    # Vérifier si la version demandée existe déjà
    if nvm list | grep -q "v${NODE_VERSION}"; then
        echo "✅ Node.js ${NODE_VERSION} déjà installé"
        nvm use ${NODE_VERSION}
    else
        echo "📦 Installation Node.js ${NODE_VERSION}..."
        nvm install ${NODE_VERSION}
        nvm use ${NODE_VERSION}
    fi
    
    # Définir comme version par défaut
    nvm alias default ${NODE_VERSION}
    
    echo "✅ Configuration Node.js terminée :"
    echo "Node.js : $(node --version)"
    echo "NPM : $(npm --version)"
}

# Exécution des fonctions
audit_node_versions || install_nvm_if_needed
audit_node_versions  # Re-audit après installation
setup_node_version
```

### Phase 4 : Installation Yarn

```bash
echo "🔧 PHASE 4 : Installation Yarn..."

# Installation Yarn via NPM (méthode recommandée)
npm install -g yarn

# Installation des packages NPM globaux essentiels pour Prima Golf
echo "📦 Installation des packages NPM globaux Prima Golf..."
npm install -g @expo/cli @react-native-community/cli
npm install -g typescript ts-node
npm install -g eslint prettier
npm install -g @nestjs/cli

# Vérification
echo "✅ Yarn version : $(yarn --version)"
echo "✅ Expo CLI : $(expo --version)"
echo "✅ TypeScript : $(tsc --version)"

# Configuration Yarn pour Prima Golf
yarn config set registry https://registry.npmjs.org/
```

### Phase 5 : Configuration Git

```bash
echo "🔧 PHASE 5 : Configuration Git..."

# Configuration globale Git
git config --global user.name "${GIT_NAME}"
git config --global user.email "${GIT_EMAIL}"
git config --global init.defaultBranch main
git config --global pull.rebase false

# Configuration pour Bitbucket
git config --global credential.helper osxkeychain

echo "✅ Configuration Git :"
git config --global --list | grep -E "(user\.|credential\.)"
```

### Phase 6 : Création de l'Arborescence Prima

```bash
echo "🔧 PHASE 6 : Création de l'arborescence Prima Golf..."

# Création du répertoire principal
PRIMA_ROOT="/Volumes/PRIMA/Workspace"
mkdir -p "${PRIMA_ROOT}"
cd "${PRIMA_ROOT}"

echo "📁 Répertoire de travail : ${PRIMA_ROOT}"
```

### Phase 7 : Clonage des Repositories

```bash
echo "🔧 PHASE 7 : Clonage des repositories Prima Golf..."

# URLs avec authentification
BITBUCKET_BASE="https://${BITBUCKET_USER}:${BITBUCKET_APP_PASSWORD}@bitbucket.org/aps-prima"

repositories=(
    "primapp-master:Prima-MASTER"
    "primapp-api:Prima-API" 
    "primapp-common:Prima-COMMON"
    "primapp-native:Prima-NATIVE"
    "primapp-web:Prima-WEB"
    "primapp-embed:Prima-EMBED"
    "primapp-access:Prima-ACCESS"
    "primapp-action:Prima-ACTION"
    "primapp-cloud:Prima-CLOUD"
    "primapp-edg:Prima-EDG"
    "primapp-hq:Prima-HQ"
    "primapp-media:Prima-MEDIA"
    "primapp-static:Prima-STATIC"
)

for repo_info in "${repositories[@]}"; do
    IFS=':' read -r repo_name local_name <<< "$repo_info"
    
    echo "📥 Clonage de ${repo_name} vers ${local_name}..."
    
    if [ -d "${local_name}" ]; then
        echo "⚠️  ${local_name} existe déjà, mise à jour..."
        cd "${local_name}"
        git pull origin main || git pull origin master
        cd ..
    else
        git clone "${BITBUCKET_BASE}/${repo_name}.git" "${local_name}"
    fi
    
    echo "✅ ${local_name} prêt"
done

# Nettoyage des credentials en mémoire pour sécurité
git config --global --unset credential.helper || true
```

### Phase 8 : Installation des Dépendances

```bash
echo "🔧 PHASE 8 : Installation des dépendances..."

# Fonction d'installation avec gestion d'erreurs
install_dependencies() {
    local project_name=$1
    local project_path=$2
    
    echo "📦 Installation dépendances ${project_name}..."
    cd "${PRIMA_ROOT}/${project_path}"
    
    # Utiliser la version Node.js du .nvmrc si présent
    if [ -f .nvmrc ]; then
        echo "🔄 Utilisation Node.js version $(cat .nvmrc) pour ${project_name}"
        nvm use
    fi
    
    # Installation avec Yarn
    if [ -f package.json ]; then
        yarn install --frozen-lockfile
        echo "✅ Dépendances ${project_name} installées"
    else
        echo "⚠️  Pas de package.json trouvé dans ${project_name}"
    fi
    
    cd "${PRIMA_ROOT}"
}

# Installation pour chaque projet
install_dependencies "Prima-MASTER" "Prima-MASTER"
install_dependencies "Prima-API" "Prima-API"
install_dependencies "Prima-COMMON" "Prima-COMMON"
install_dependencies "Prima-NATIVE" "Prima-NATIVE"
install_dependencies "Prima-WEB" "Prima-WEB"
install_dependencies "Prima-EMBED" "Prima-EMBED"
install_dependencies "Prima-ACCESS" "Prima-ACCESS"
install_dependencies "Prima-ACTION" "Prima-ACTION"
install_dependencies "Prima-CLOUD" "Prima-CLOUD"
install_dependencies "Prima-EDG" "Prima-EDG"
install_dependencies "Prima-HQ" "Prima-HQ"
install_dependencies "Prima-MEDIA" "Prima-MEDIA"
install_dependencies "Prima-STATIC" "Prima-STATIC"
```

### Phase 9 : Configuration Variables d'Environnement

```bash
echo "🔧 PHASE 9 : Configuration variables d'environnement..."

# Création fichier .env global Prima
cat > "${PRIMA_ROOT}/.env.prima" << EOF
# Prima Golf Environment Configuration
# Generated on $(date)

# Node.js Configuration
NODE_VERSION=${NODE_VERSION}
NVM_DIR=\$HOME/.nvm

# Prima Workspace
PRIMA_WORKSPACE=${PRIMA_ROOT}
PRIMA_MASTER=${PRIMA_ROOT}/Prima-MASTER
PRIMA_API=${PRIMA_ROOT}/Prima-API  
PRIMA_COMMON=${PRIMA_ROOT}/Prima-COMMON
PRIMA_NATIVE=${PRIMA_ROOT}/Prima-NATIVE
PRIMA_WEB=${PRIMA_ROOT}/Prima-WEB
PRIMA_EMBED=${PRIMA_ROOT}/Prima-EMBED
PRIMA_ACCESS=${PRIMA_ROOT}/Prima-ACCESS
PRIMA_ACTION=${PRIMA_ROOT}/Prima-ACTION
PRIMA_CLOUD=${PRIMA_ROOT}/Prima-CLOUD
PRIMA_EDG=${PRIMA_ROOT}/Prima-EDG
PRIMA_HQ=${PRIMA_ROOT}/Prima-HQ
PRIMA_MEDIA=${PRIMA_ROOT}/Prima-MEDIA
PRIMA_STATIC=${PRIMA_ROOT}/Prima-STATIC

# Development
NODE_ENV=development
DEBUG=prima:*
EOF

# Ajout au .zshrc
echo "" >> ~/.zshrc
echo "# Prima Golf Environment" >> ~/.zshrc
echo "source ${PRIMA_ROOT}/.env.prima" >> ~/.zshrc

echo "✅ Variables d'environnement configurées"
```

### Phase 9.5 : Validation des Outils Installés

```bash
echo "🔧 PHASE 9.5 : Validation des outils installés..."

# Test des outils essentiels
echo "🧪 Test des outils de développement..."
command -v git >/dev/null 2>&1 || { echo "❌ Git non installé"; exit 1; }
command -v node >/dev/null 2>&1 || { echo "❌ Node.js non installé"; exit 1; }
command -v yarn >/dev/null 2>&1 || { echo "❌ Yarn non installé"; exit 1; }
command -v watchman >/dev/null 2>&1 || { echo "❌ Watchman non installé"; exit 1; }

# Test des outils mobile
echo "📱 Test des outils mobile..."
command -v expo >/dev/null 2>&1 || { echo "❌ Expo CLI non installé"; exit 1; }
command -v fastlane >/dev/null 2>&1 || { echo "❌ Fastlane non installé"; exit 1; }
command -v pod >/dev/null 2>&1 || { echo "❌ CocoaPods non installé"; exit 1; }

# Test des outils TypeScript
echo "🔷 Test TypeScript..."
command -v tsc >/dev/null 2>&1 || { echo "❌ TypeScript non installé"; exit 1; }
command -v eslint >/dev/null 2>&1 || { echo "❌ ESLint non installé"; exit 1; }

# Test des outils cloud
echo "☁️ Test des outils cloud..."
command -v docker >/dev/null 2>&1 || { echo "❌ Docker non installé"; exit 1; }
command -v gcloud >/dev/null 2>&1 || { echo "❌ Google Cloud SDK non installé"; exit 1; }

echo "✅ Tous les outils essentiels sont installés et fonctionnels !"
```

### Phase 10 : Tests de Validation

```bash
echo "🔧 PHASE 10 : Tests de validation de l'installation..."

# Test Node.js et Yarn
echo "🧪 Test Node.js et Yarn..."
node --version || { echo "❌ Node.js non accessible"; exit 1; }
yarn --version || { echo "❌ Yarn non accessible"; exit 1; }
nvm --version || { echo "❌ NVM non accessible"; exit 1; }

# Test projets Prima
projects=("Prima-MASTER" "Prima-API" "Prima-COMMON" "Prima-NATIVE" "Prima-WEB" "Prima-EMBED" "Prima-ACCESS" "Prima-ACTION" "Prima-CLOUD" "Prima-EDG" "Prima-HQ" "Prima-MEDIA" "Prima-STATIC")
for project in "${projects[@]}"; do
    if [ -d "${PRIMA_ROOT}/${project}" ]; then
        echo "✅ ${project} : Cloné et accessible"
        
        # Test package.json et node_modules
        if [ -f "${PRIMA_ROOT}/${project}/package.json" ]; then
            echo "✅ ${project} : package.json présent"
            
            if [ -d "${PRIMA_ROOT}/${project}/node_modules" ]; then
                echo "✅ ${project} : Dépendances installées"
            else
                echo "⚠️  ${project} : Dépendances manquantes"
            fi
        fi
    else
        echo "❌ ${project} : Projet manquant"
    fi
done

# Test .nvmrc support
cd "${PRIMA_ROOT}/Prima-NATIVE"
if [ -f .nvmrc ]; then
    echo "🧪 Test auto-switch Node.js..."
    nvm use
    echo "✅ Auto-switch .nvmrc fonctionnel"
fi

cd "${PRIMA_ROOT}"
```

### Phase 11 : Rapport Final et Instructions

```bash
echo ""
echo "🎉 INSTALLATION TERMINÉE AVEC SUCCÈS !"
echo "======================================"
echo ""
echo "📊 RÉCAPITULATIF DE L'INSTALLATION :"
echo ""
echo "✅ Homebrew : $(brew --version | head -n1)"
echo "✅ Git : $(git --version)"
echo "✅ Node.js : $(node --version)"
echo "✅ NPM : $(npm --version)"
echo "✅ Yarn : $(yarn --version)"
echo "✅ NVM : $(nvm --version)"
echo "✅ TypeScript : $(tsc --version)"
echo "✅ Expo CLI : $(expo --version)"
echo "✅ Fastlane : $(fastlane --version)"
echo "✅ CocoaPods : $(pod --version)"
echo "✅ Docker : $(docker --version)"
echo "✅ ESLint : $(eslint --version)"
echo "✅ Prettier : $(prettier --version)"
echo ""
echo "📁 PROJETS PRIMA GOLF INSTALLÉS :"
echo "• Prima-MASTER : ${PRIMA_ROOT}/Prima-MASTER"
echo "• Prima-API    : ${PRIMA_ROOT}/Prima-API"
echo "• Prima-COMMON : ${PRIMA_ROOT}/Prima-COMMON"
echo "• Prima-NATIVE : ${PRIMA_ROOT}/Prima-NATIVE"
echo "• Prima-WEB    : ${PRIMA_ROOT}/Prima-WEB"
echo "• Prima-EMBED  : ${PRIMA_ROOT}/Prima-EMBED"
echo "• Prima-ACCESS : ${PRIMA_ROOT}/Prima-ACCESS"
echo "• Prima-ACTION : ${PRIMA_ROOT}/Prima-ACTION"
echo "• Prima-CLOUD  : ${PRIMA_ROOT}/Prima-CLOUD"
echo "• Prima-EDG    : ${PRIMA_ROOT}/Prima-EDG"
echo "• Prima-HQ     : ${PRIMA_ROOT}/Prima-HQ"
echo "• Prima-MEDIA  : ${PRIMA_ROOT}/Prima-MEDIA"
echo "• Prima-STATIC : ${PRIMA_ROOT}/Prima-STATIC"
echo ""
echo "🚀 PROCHAINES ÉTAPES :"
echo "1. Redémarrer votre terminal ou exécuter : source ~/.zshrc"
echo "2. Naviguer vers un projet : cd ${PRIMA_ROOT}/Prima-NATIVE"
echo "3. Le Node.js se switchera automatiquement selon le .nvmrc"
echo "4. Tester Expo : expo doctor (diagnostic de l'environnement)"
echo "5. Tester React Native : npx react-native doctor"
echo "6. Commencer le développement : yarn start"
echo ""
echo "📚 COMMANDES UTILES :"
echo "• Aller au workspace : cd \$PRIMA_WORKSPACE"
echo "• Lister les projets : ls \$PRIMA_WORKSPACE"
echo "• Versions Node : nvm list"
echo "• Switch manuel Node : nvm use [version]"
echo "• Diagnostics Expo : expo doctor"
echo "• Builds iOS : fastlane ios build"
echo "• Status Docker : docker ps"
echo "• Cloud login : gcloud auth login"
echo ""
echo "🔧 CONFIGURATION TERMINÉE - ENVIRONNEMENT PRÊT !"
```

### Script Principal d'Exécution

```bash
#!/bin/bash
# prima-setup.sh - Installation complète environnement Prima Golf

set -e
trap 'echo "❌ Erreur ligne $LINENO. Installation interrompue."' ERR

main() {
    # Collecte des informations
    echo "🚀 SETUP PRIMA GOLF - Configuration Environnement MacBook Intel"
    echo "================================================================="
    echo ""
    
    read -p "👤 Nom d'utilisateur Bitbucket : " BITBUCKET_USER
    read -s -p "🔑 App Password Bitbucket : " BITBUCKET_APP_PASSWORD
    echo ""
    read -p "🗂️ Version Node.js [18.17.0] : " NODE_VERSION
    NODE_VERSION=${NODE_VERSION:-18.17.0}
    read -p "📧 Email Git : " GIT_EMAIL
    read -p "👤 Nom complet Git : " GIT_NAME
    read -p "📁 Répertoire installation [/Volumes/PRIMA/Workspace] : " PRIMA_ROOT
    PRIMA_ROOT=${PRIMA_ROOT:-/Volumes/PRIMA/Workspace}
    
    echo ""
    echo "🔄 Début de l'installation..."
    echo ""
    
    # Exécution de toutes les phases
    # [Insérer ici tous les blocs des phases 2-11]
    
    echo "✨ Installation Prima Golf terminée avec succès !"
}

# Point d'entrée
main "$@"
```

## 👥 **Audience**
Développeurs Prima Golf utilisant macOS Intel souhaitant configurer un environnement de développement complet et opérationnel pour l'écosystème complet (13 projets : MASTER, API, COMMON, NATIVE, WEB, EMBED, ACCESS, ACTION, CLOUD, EDG, HQ, MEDIA, STATIC) avec Node.js, React Native, Git et tous les outils nécessaires.

---

## 📋 **Instructions d'Utilisation**

### Exécution Rapide
```bash
# Télécharger et exécuter le script
curl -fsSL https://raw.githubusercontent.com/[repo]/prima-setup.sh | bash
```

### Exécution Manuelle
```bash
# Copier le script dans prima-setup.sh
chmod +x prima-setup.sh
./prima-setup.sh
```

### Variables Personnalisables
- `NODE_VERSION` : Version Node.js (défaut: 18.17.0)
- `PRIMA_ROOT` : Répertoire installation (défaut: /Volumes/PRIMA/Workspace)
- `BITBUCKET_USER` : Username Bitbucket
- `BITBUCKET_APP_PASSWORD` : App Password Bitbucket

---

*Prompt P.R.I.M.A. v1.0 - Setup Environnement Prima Golf optimisé pour MacBook Intel*

**Créé le :** 10 juin 2025  
**Pour :** Écosystème Prima Golf complet (13 projets : MASTER, API, COMMON, NATIVE, WEB, EMBED, ACCESS, ACTION, CLOUD, EDG, HQ, MEDIA, STATIC)  
**Compatibilité :** macOS Intel + Zsh + Bitbucket
````
