# Projet et dépot GitHub en groupe

## 1. Un étudiant (responsaable projet) crée le dépôt groupe

## 1. Créer en local le dossier du projet

Exemple :

```text
C:\Users\Jean\Documents\Projet-GroupeN
```

Le dossier peut déjà contenir des fichiers (`README.md`, scripts Python, Texte du Projet, scripts en C, etc.)

---

## 2. Le responsable ajoute le projet dans GitHub Desktop

Dans GitHub Desktop :

```text
File → Add Local Repository
```

Puis :

* sélectionner le dossier du projet
* cliquer sur **Add Repository**

Si le dossier n’est pas encore un dépôt Git, GitHub Desktop proposera :

```text
Create a repository
```

Cliquer dessus.

---

## 3. Le Responsable initialise le dépôt

Remplir :

* **Name** : nom du projet (exemple Projet-GroupeN)
* éventuellement une description
* laisser Git Ignore si besoin

Puis :

```text
Create Repository
```

Git est alors initialisé localement.

---

## 4. Le REsponsable fait le premier commit

GitHub Desktop détecte les fichiers.

Dans la zone de gauche :

* vérifier les fichiers
* écrire un message dans :

```text
Summary
```

Exemple :

```text
Initial commit
```

Puis cliquer :

```text
Commit to main
```

---

## 5. Le Responsable publie sur GitHub

En haut :

```text
Publish repository
```

Choisir :

* nom du dépôt GitHub
* public ou private

Puis :

```text
Publish Repository
```

Le projet est alors envoyé sur GitHub.

---

## 6. Vérification

Le dépôt apparaît sur :

[GitHub](https://github.com/utilisateur/mon-projet)

Exemple :

```text
https://github.com/utilisateur/Projet-GroupeN
```

---
---

## 2. Il ajoute les autres membres

Dans GitHub :

```text
Repository → Settings → Collaborators
```

Puis ajout des membres du groupe :

```text
Add people
```

---

## 3. Les autres étudiants clonent le dépôt

Dans GitHub Desktop :

```text
File → Clone Repository
```

Ils clonent :

```text
Projet-Groupe1
```

---

## 4. Chaque étudiant travaille localement

Exemple :

```text
Documents\GitHub\Projet-Groupe1
```

---

## 5. Workflow MAJ

## Avant de commencer

Toujours :

```text
Pull origin
```

pour récupérer les modifications des autres.

---

## Après modification

### Commit local

```text
Commit to main
```

---

### Envoi GitHub

```text
Push origin
```

---

## Très important pour éviter les conflits

### Règle simple

Éviter que deux étudiants modifient :

* le même fichier au même moment.

---

## Bonne organisation

Exemple :

| Étudiant | Fichier            |
| -------- | ------------------ |
| Alice    | README.md          |
| Bob      | script.py          |
| Chloé    | docker-compose.yml |

---

## Structure locale typique

```text id="t8m4qy"
Documents\GitHub\
├── Cybersec-projets
├── Monprojet
└── Projet-GroupeN
```

---

## Ce qu’il faut retenir

## Un seul étudiant (responsable du projet)

* crée le dépôt
* fait le premier push.

## Les autres

* sont collaborateurs
* clonent ensuite le dépôt.

C’est le workflow GitHub collaboratif le plus simple.
