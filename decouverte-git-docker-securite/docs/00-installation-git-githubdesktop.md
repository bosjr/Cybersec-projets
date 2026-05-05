# installation Git et/ou GitHub Desktop

## Installation sur Windows

Git for Windows est un exécutable autonome téléchargeable sur [git-scm.com/download/win](https://git-scm.com/download/win).  
L'installateur inclut Git Bash (terminal Unix-like), Git GUI et intègre Git au menu contextuel de l'Explorateur.  
Après installation, vérifiez avec `git --version` dans l'invite de commandes ou PowerShell.

## Installation sur Linux

Sur Ubuntu/Debian : `sudo apt update && sudo apt install git`.  
Sur Fedora : `sudo dnf install git`.  
Sur Arch : `sudo pacman -S git`. Vérifiez aussi avec `git --version`.
Kali Linux (basé Debian), `sudo apt install git`

## Différences pratiques

| Système   | Méthode principale          | Avantages étudiants                  |
|-----------|-----------------------------|-------------------------------------|
| **Windows** | Installateur .exe 64-bit   | Interface graphique (Git Bash), facile pour débutants
| **Linux**   | Paquet système (apt/dnf)   | Préinstallé souvent, natif CLI, plus léger

Vous pouvez parfaitement installer GitHub Desktop **après** avoir installé Git sur Windows. GitHub Desktop utilise l'installation Git existante et ne la remplace pas.

## Compatibilité confirmée

GitHub Desktop détecte automatiquement Git s'il est déjà installé sur votre système Windows (version 2.30+ recommandée).  
L'application s'appuie sur le binaire Git pour toutes ses opérations en arrière-plan, sans conflit ni réinstallation forcée.
Vous gagnez une interface graphique au-dessus de votre Git CLI déjà fonctionnel.

## Étapes d'installation

1. **Téléchargez GitHub Desktop** depuis [desktop.github.com](https://desktop.github.com) (version Windows 64-bit).
2. **Lancez l'installateur .exe** – il s'exécute normalement même avec Git présent.
3. **Connectez votre compte GitHub** lors du premier lancement.
4. **Vérifiez** : Ouvrez Git Bash ou PowerShell, tapez `git --version` (votre Git reste intact) puis lancez GitHub Desktop.

## Procédure d’installation **pas à pas en français** pour **Windows** et **macOS**. Installez d’abord **Git** (CLI), puis **GitHub Desktop** (GUI), qui les détecte automatiquement. Prise en charge : Windows 10 64-bit+ et macOS 12+.

## Windows : Installation Git

1. Allez sur [git-scm.com/download/win](https://git-scm.com/download/win) et téléchargez l’installateur 64-bit (détecté auto).
2. Double-cliquez sur le fichier `.exe` téléchargé (dans Téléchargements).
3. Laissez les options par défaut (Git Bash, intégration Explorateur) et cliquez **Suivant** jusqu’à **Installer**.
4. Vérifiez : Ouvrez **Git Bash** (menu Démarrer), tapez `git --version` (doit afficher la version, ex. 2.45+).

## Windows : Installation GitHub Desktop

1. Allez sur [desktop.github.com](https://desktop.github.com) et cliquez **Download for Windows**.
2. Double-cliquez sur le `.exe` dans Téléchargements ; l’installation démarre auto.
3. Lancez GitHub Desktop, connectez-vous à GitHub.com (autorisez l’app).
4. Cliquez **Finish** ; il détecte Git et est prêt (testez en clonant un repo). 

## macOS : Installation Git

1. Allez sur [git-scm.com/download/mac](https://git-scm.com/download/mac) et téléchargez l’installateur (Intel ou Apple Silicon).
2. Ouvrez le `.dmg`, glissez Git dans **Applications**.
3. Ouvrez **Terminal** (Spotlight : Cmd+Space), tapez `git --version` pour vérifier. 

## macOS : Installation GitHub Desktop

1. Allez sur [desktop.github.com](https://desktop.github.com) et cliquez **Download for macOS** (ou Apple Silicon).
2. Ouvrez le `.zip` dans Téléchargements, puis double-cliquez sur **GitHub Desktop.app**.
3. Glissez-le dans **Applications** si demandé (cliquez **Déplacer et redémarrer**).
4. Lancez-le, connectez-vous à GitHub et cliquez **Finish**.

## Vérification finale

- Ouvrez GitHub Desktop, clonez un repo test (ex. votre DVWA GitHub).
- Dans terminal/CLI : `git status` confirme tout.

## Cloner un repos avec GitHub Dsektop

Voici les **commandes et étapes précises** pour **ouvrir GitHub Desktop et cloner un repo test**

## Ouvrir GitHub Desktop

- **Windows** : Menu Démarrer > tapez "GitHub Desktop" > Ouvrir (ou raccourci bureau).
- **macOS** : Applications > GitHub Desktop (Spotlight : Cmd+Space "GitHub").
- **CLI (optionnel)** : Dans Git Bash/Terminal : `github .` (ouvre le dernier repo) ou `github /chemin/vers/repo`.

## Cloner via GitHub Desktop (GUI recommandée)

1. Ouvrez GitHub Desktop.
2. Cliquez **File > Clone Repository** (Fichier > Cloner un dépôt).
3. Sélectionner ou tapez URL.
4. Cliquez le repo > **Choose...** pour dossier local
5. **Clone** – il télécharge et ouvre. 

## Alternative CLI (Git seul)

``` bash
mkdir test
cd test
git clone "url""
git status  # Vérifie clonage OK
```

Puis ouvrez le dossier dans GitHub Desktop via **File > Add Local Repository**. 

## Test rapide

Après clonage, modifiez un fichier > **Commit to main** > **Push origin** dans Desktop. Vérifiez sur GitHub.com. 