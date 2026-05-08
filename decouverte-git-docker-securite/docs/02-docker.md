
# 📄 docs/02-docker.md

```md
# Introduction à Docker

## Objectif

Lancer une application sans installation complexe.

# Introduction à Docker

## 🎯 Objectif

Comprendre ce qu’est Docker et savoir lancer une application simplement.

---

## 🧱 Qu’est-ce que Docker ?

Docker est un outil qui permet de lancer des applications dans des environnements isolés appelés **conteneurs**.

👉 Un conteneur contient :
- une application
- ses dépendances
- sa configuration

---

## 📦 Pourquoi utiliser Docker ?

Sans Docker :
- installation complexe
- problèmes de compatibilité

Avec Docker :
- application prête à l’emploi
- même fonctionnement sur tous les postes

---

## 🖼️ Image vs Conteneur

- **Image** : modèle (comme un modèle prêt à l’emploi)
- **Conteneur** : instance en cours d’exécution

👉 Exemple :
- image = recette
- conteneur = plat préparé

---

## ⚙️ Commandes principales

Tester que Docker fonctionne :

```bash
docker run hello-world
```

👉 Résultat attendu :

* un message de confirmation s’affiche

---

## ⚙️ Commandes principales

### ▶️ Lancer une application

```bash
docker run -d -p 8080:80 vulnerables/web-dvwa
```

---

### 📋 Voir les conteneurs actifs

```bash
docker ps
```

---

### 📋 Voir tous les conteneurs (même arrêtés)

```bash
docker ps -a
```

---

### ⛔ Arrêter un conteneur

```bash
docker stop <ID>
```

---

### ▶️ Redémarrer un conteneur

```bash
docker start <ID>
```

---

### 🧹 Supprimer un conteneur

```bash
docker rm <ID>
```

---

## 🌐 Accéder à l’application

Ouvrir un navigateur :

[http://localhost:8080](http://localhost:8080)

---

## ✅ Résultat attendu

* L’application DVWA est accessible
* Vous pouvez interagir avec

---

## ⚠️ Problèmes fréquents

* Docker non lancé
* Port déjà utilisé
* erreur de commande

---

## 📌 À retenir

* `docker run` lance une application
* `docker ps` permet de voir ce qui fonctionne
* un conteneur peut être arrêté et relancé
* Docker simplifie le déploiement

---

## ➡️ Prochaine étape

Tester une vulnérabilité sur l’application


Voir ressources/commandes-docker.git