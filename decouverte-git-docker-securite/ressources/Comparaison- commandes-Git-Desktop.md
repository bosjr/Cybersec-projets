# Comparaison commandes Git (CLI) avec Menu GitHut Desktop

Ce que fait réellement GitHub Desktop

| Action | Fonction |
| -------- | ---------- |
| Create Repository | Initialise Git |
| Commit | Sauvegarde locale |
| Publish Repository | Création du dépôt GitHub + premier push |
| Push origin | Envoi des commits |
| Pull origin | Récupération des modifications |

| Outil          | Rôle                         |
| -------------- | ---------------------------- |
| Git            | Gestion des versions locale  |
| GitHub         | Hébergement distant          |
| GitHub Desktop | Interface graphique pour Git |

---

| Action Git                      | Commande Git locale                                     | GitHub Desktop                                                   |
| ------------------------------- | ------------------------------------------------------- | ---------------------------------------------------------------- |
| Initialiser un dépôt            | `git init`                                              | `File → New Repository`                                          |
| Cloner un dépôt                 | `git clone URL`                                         | `File → Clone Repository`                                        |
| Ajouter un dépôt local existant | —                                                       | `File → Add Local Repository`                                    |
| Vérifier l’état des fichiers    | `git status`                                            | Liste des changements dans la colonne de gauche                  |
| Ajouter les fichiers au suivi   | `git add .`                                             | Automatique via cases cochées                                    |
| Créer un commit                 | `git commit -m "message"`                               | `Commit to main`                                                 |
| Envoyer vers GitHub             | `git push`                                              | `Push origin`                                                    |
| Récupérer les changements       | `git pull`                                              | `Pull origin`                                                    |
| Synchroniser pull + push        | `git pull && git push`                                  | `Fetch origin` / `Pull origin` / `Push origin` selon le contexte |
| Voir l’historique               | `git log`                                               | Onglet `History`                                                 |
| Voir les différences            | `git diff`                                              | Onglet modifications                                             |
| Créer une branche               | `git branch nom`                                        | `Current Branch → New Branch`                                    |
| Changer de branche              | `git checkout nom`                                      | Sélection de branche                                             |
| Fusionner une branche           | `git merge nom`                                         | `Branch → Merge into current branch`                             |
| Supprimer une branche           | `git branch -d nom`                                     | Clic droit sur branche → `Delete`                                |
| Publier un dépôt sur GitHub     | `git remote add origin URL` + `git push -u origin main` | `Publish Repository`                                             |
| Voir les remotes                | `git remote -v`                                         | `Repository → Repository Settings`                               |
| Changer l’URL du remote         | `git remote set-url origin URL`                         | `Repository Settings`                                            |
| Récupérer les infos distantes   | `git fetch`                                             | `Fetch origin`                                                   |
| Annuler modifications locales   | `git restore fichier`                                   | Clic droit → `Discard Changes`                                   |
| Retirer un fichier du suivi     | `git rm --cached fichier`                               | Via suppression + commit                                         |
| Ajouter un `.gitignore`         | création fichier `.gitignore`                           | Choix lors de `New Repository`                                   |
| Résoudre des conflits           | édition manuelle + commit                               | Interface de résolution de conflits                              |
| Ouvrir le dépôt sur GitHub      | —                                                       | `Repository → View on GitHub`                                    |
| Ouvrir dans VS Code             | —                                                       | `Repository → Open in Visual Studio Code`                        |
