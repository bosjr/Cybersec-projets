
# – Partie 1 Git / Github Desktop

## Présentation + Prise en main GitHub

````md
# Projet Fil Rouge – Initiation DevSecOps

## 🎯 Objectif du projet

Ce projet a pour objectif de vous faire découvrir plusieurs outils utilisés en développement et en cybersécurité :

- Gestion de version (Git / GitHub)
- Environnement de développement
- Déploiement d’application
- Notions de sécurité web

Aucune connaissance préalable n’est requise. Vous serez guidés étape par étape.

---

## 🧭 Organisation du projet

Le projet se déroule en plusieurs étapes :

1. Prise en main de GitHub
2. Utilisation de Git (versioning)
3. Lancement d’une application avec Docker
4. Découverte d’une vulnérabilité
5. Explication et restitution

---

## 🔎 Qu’est-ce que Git ?

Git est un outil qui permet de :
- sauvegarder différentes versions d’un projet
- suivre les modifications
- revenir en arrière si nécessaire

---

## 🌐 Qu’est-ce que GitHub ?

GitHub est une plateforme en ligne qui permet de :
- stocker du code
- collaborer
- partager des projets

---

## 🛠️ Étape 1 – Créer un compte GitHub

1. Aller sur : https://github.com
2. Cliquer sur "Sign up"
3. Créer un compte

---

## 📥 Étape 2 – Cloner un projet

Le formateur vous fournit un lien de dépôt.

Dans un terminal :

```bash
git clone <URL_DU_REPO>
````

---

## 📁 Étape 3 – Ouvrir le projet

1. Ouvrir Visual Studio Code
2. Cliquer sur "Open Folder"
3. Sélectionner le dossier cloné

---

## ✏️ Étape 4 – Modifier un fichier

1. Ouvrir le fichier README.md
2. Ajouter votre nom :

```md
## Auteur
Votre Nom
```

3. Enregistrer

4. Compléter 01-TP-github.md

---

## 💾 Étape 5 – Enregistrer les modifications (commit)

Dans le terminal :

```bash
git add .
git commit -m "Ajout du nom dans le README"
```

---

## 🚀 Étape 6 – Envoyer sur GitHub (push)

```bash
git push
```

---

## ✅ Résultat attendu

* Votre modification est visible sur GitHub
* Votre nom apparaît dans le README

---

## 📌 À retenir

* `git clone` : récupérer un projet
* `git add` : préparer les fichiers
* `git commit` : enregistrer une version
* `git push` : envoyer sur GitHub

---

## 🎯 Objectif validé

À ce stade, vous savez :

* récupérer un projet
* le modifier
* sauvegarder votre travail
* l’envoyer en ligne

---

# Prise en main de GitHub Desktop

## 🎯 Objectif

Apprendre à récupérer et modifier un projet avec GitHub Desktop.

---

## 📥 1. Cloner un dépôt

1. Ouvrir GitHub Desktop
2. Cliquer sur **File > Clone repository**
3. Onglet **URL**
4. Coller l’URL du dépôt
5. Choisir un dossier local
6. Cliquer sur **Clone**

---

## 📂 2. Ouvrir dans Visual Studio Code

1. Dans GitHub Desktop :
   - Cliquer sur **Open in Visual Studio Code**

---

## ✏️ 3. Modifier un fichier

1. Ouvrir `README.md`
2. Ajouter :

## Auteur  : Votre Nom

Ne pas oublier d'enregistrer

---

## 💾 4. Commit

Dans GitHub Desktop :

1. Vérifier les fichiers modifiés
2. Ajouter un message :  
   `Ajout du nom dans le README`
3. Cliquer sur **Commit to main**

---

## 🚀 5. Push

Cliquer sur **Push origin**

---

## ✅ Résultat attendu

Votre modification est visible sur GitHub.

---

## 📌 À retenir

- Commit = sauvegarde locale
- Push = envoi sur GitHub

---

## ➡️ Prochaine étape

Nous allons maintenant lancer une application avec Docker.

```

---

- **Partie 2 (Docker simplifié)**
- **Partie 3 (DVWA + SQLi guidée)**

```
