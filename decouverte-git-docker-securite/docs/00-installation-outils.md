# Installation des outils

## 🎯 Objectif

Installer les outils nécessaires pour réaliser le projet :

- GitHub Desktop (interface graphique pour Git)
- Visual Studio Code (éditeur de code)
- Docker

**Livrable**  
Environnement prêt

---

## 🧰 1. Installer GitHub Desktop

Télécharger et installer :

[https://desktop.github.com/](https://desktop.github.com/)

1. Lancer l'application
2. Se connecter avec son compte GitHub
3. Vérifier que l'application est opérationnelle

---

## 🧰 2. Installer Visual Studio Code

Télécharger :

[Visual Studio Code](https://code.visualstudio.com/)

1. Installer le logiciel
2. Lancer Visual Studio Code
3. Vérifier que l'application s'ouvre correctement

---

## 📁 3. Ouvrir un projet avec VS Code

1. Ouvrir Visual Studio Code
2. Cliquer sur **Fichier > Ouvrir Dossier**
3. Sélectionner un dossier

---

## ✅ Résultat attendu

- GitHub Desktop est installé et connecté
- Visual Studio Code fonctionne
- Vous savez ouvrir un dossier

---

## 📁 4. Installation de Docker

## 🎯 Objectif : Installer Docker sur votre poste pour pouvoir lancer des conteneurs et l’application DVWA.

---

## 🧰 Télécharger Docker

Aller sur le site officiel :

- Windows / Mac : [https://www.docker.com/get-started](https://www.docker.com/get-started)
- Linux : utiliser le gestionnaire de paquets (exemple Ubuntu) :

```bash
sudo apt update
sudo apt install docker.io
````

## 🔧 Installer Docker

* Windows / Mac : suivre l’assistant d’installation
* Linux : vérifier l’installation :

```bash
docker --version
```

---

## 👥 Ajouter votre utilisateur au groupe Docker (Linux uniquement)

```bash
sudo usermod -aG docker $USER
```

* puis **se déconnecter et reconnecter** pour que la modification soit prise en compte

---

## ✅ Vérifier le fonctionnement de Docker

Tester la commande de démonstration :

```bash
docker run hello-world
```

* Résultat attendu : message confirmant que Docker fonctionne

---

## ⚠️ Problèmes fréquents

* Docker non lancé → ouvrir Docker Desktop ou démarrer le service Linux :

```bash
sudo systemctl start docker
```

* Port utilisé → choisir un autre port lors de `docker run`

---

## 📌 À retenir

* Docker est nécessaire pour lancer DVWA
* La commande `docker run hello-world` teste l’installation
* Les commandes de base seront vues dans la partie suivante
* GitHub Desktop permet d'utiliser Git sans ligne de commande
* Visual Studio Code permet de modifier les fichiers
* Docker permet de lancer des conteneurs et l’application DVWA

---

## ➡️ Prochaine étape

Cloner un projet avec git ou  GitHub Desktop