# Pousser un projet local vers GitHub

## 1. Créer ou ouvrir le dossier du projet

Exemple :

```text
C:\Users\Jean\Documents\mon-projet
```

Le dossier peut déjà contenir des fichiers (`README.md`, scripts Python, etc.).

---

## 2. Ajouter le projet dans GitHub Desktop

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

## 3. Initialiser le dépôt

Remplir :

* **Name** : nom du projet
* éventuellement une description
* laisser Git Ignore si besoin

Puis :

```text
Create Repository
```

Git est alors initialisé localement.

---

## 4. Faire le premier commit

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

## 5. Publier sur GitHub

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
https://github.com/utilisateur/mon-projet
```

---

## Workflow ensuite

Après modification des fichiers :

1. GitHub Desktop détecte les changements
2. écrire un message de commit
3. cliquer :

```text
Commit to main
```

4. puis :

```text
Push origin
```

---

## Différence importante

| Action | Rôle                                     |
| ------ | ---------------------------------------- |
| Commit | Sauvegarde locale                        |
| Push   | Envoi vers GitHub                        |
| Pull   | Récupération des modifications distantes |

---

## Cas fréquent chez les étudiants

### “Publish repository” n’apparaît pas

Causes possibles :

* non connecté à GitHub
* dépôt déjà lié
* aucun commit effectué

---

### Erreur d’authentification

Souvent liée à :

* compte GitHub non connecté
* problème navigateur/SSO
* GitHub Desktop bloqué par proxy/antivirus

Vérifier :

```text
File → Options → Accounts
```

---

## Lorsque le dépôt GitHub est mis à jour

Exemple :

ajout d’un TP
correction d’un README
nouveaux fichiers.

### récupérer les modifications.

Avec GitHub Desktop
Méthode simple

Dans le dépôt ouvert :

```text
Fetch origin
```

Puis :

```text
Pull origin
```

Les nouveaux fichiers apparaissent automatiquement localement
