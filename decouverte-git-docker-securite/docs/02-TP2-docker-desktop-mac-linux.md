# TP Étudiants — Docker Desktop + DVWA (macOS & Linux) — 100% GUI

## Objectif

Installer Docker, vérifier WSL/équivalent Linux runtime, puis déployer **DVWA** uniquement via interface graphique (ou outils natifs Docker Desktop quand disponibles).

---

# 1. Pré-requis communs

* macOS 11+ ou Linux (Ubuntu recommandé)
* Droits administrateur
* CPU avec virtualisation activée
* Connexion Internet

---

# 2. Installation Docker Desktop

## A. macOS

### Étape 1 — Téléchargement

* Aller sur :
  [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)

* Télécharger version **Mac (Apple Silicon ou Intel selon machine)**

---

### Étape 2 — Installation

1. Ouvrir `.dmg`
2. Glisser **Docker.app** dans Applications
3. Lancer Docker Desktop
4. Autoriser permissions système si demandé

---

### Étape 3 — Vérification GUI

* Icône Docker (baleine) en haut de l’écran
* Statut :

  * 🟢 Docker Desktop running

---

### Erreurs courantes macOS

| Problème              | Cause               | Solution                                    |
| --------------------- | ------------------- | ------------------------------------------- |
| Docker ne démarre pas | sécurité macOS      | autoriser dans “Sécurité & confidentialité” |
| lenteur               | manque RAM          | augmenter mémoire Docker                    |
| CPU élevé             | mauvais paramétrage | limiter ressources                          |

---

## B. Linux (Ubuntu recommandé)

⚠️ Sur Linux, Docker Desktop existe mais nécessite souvent **KVM / systemd**

---

### Étape 1 — Installation Docker Desktop

1. Télécharger `.deb` depuis Docker
2. Installer via GUI :

   * clic droit → “Open with Software Install”
   * ou double clic

---

### Étape 2 — Lancement

* Ouvrir “Docker Desktop” depuis menu applications
* Vérifier statut :

  * 🟢 Engine running

---

### Alternative Linux (important pédagogique)

Si Docker Desktop non utilisé :

* Docker Engine + CLI (mais ici TP demandé GUI → donc Desktop obligatoire)

---

### Erreurs courantes Linux

| Problème              | Cause                  | Solution                    |
| --------------------- | ---------------------- | --------------------------- |
| Docker ne démarre pas | KVM absent             | activer virtualisation BIOS |
| permissions           | utilisateur non docker | `usermod -aG docker`        |
| service inactive      | systemd                | redémarrer service docker   |

---

# 3. Configuration Docker Desktop (macOS + Linux)

Dans **Settings / Preferences (GUI)** :

## Ressources

* RAM : 4 Go minimum
* CPU : 2 cœurs minimum

## Storage

* vérifier espace disque disponible

## Containers

* activer auto-start si besoin

---

# 4. Installation DVWA (GUI uniquement)

## Étape 1 — Recherche image

Dans Docker Desktop :

* onglet **Images**
* cliquer **Search**
* rechercher :

```
vulnerables/web-dvwa
```

---

## Étape 2 — Pull image

* cliquer **Pull**
* attendre téléchargement

---

## Étape 3 — Lancement conteneur

1. Cliquer image DVWA
2. Cliquer **Run**

Configurer :

* Port mapping :

```
8080 → 80
```

---

## Étape 4 — Accès DVWA

Dans navigateur :

```id="dvwa-url"
http://localhost:8080
```

Identifiants :

* Login : `admin`
* Password : `password`

---

# 5. Vérification via GUI

Dans Docker Desktop :

## Onglet Containers

* DVWA = 🟢 running

Actions disponibles :

* Start / Stop
* Logs
* Restart
* Delete

---

# 6. Erreurs courantes DVWA (tous OS)

| Problème          | Cause                | Solution                         |
| ----------------- | -------------------- | -------------------------------- |
| page inaccessible | port non mappé       | vérifier 8080:80                 |
| container restart | dépendances absentes | relancer image propre            |
| lenteur           | ressources faibles   | augmenter RAM Docker             |
| reset DVWA        | container supprimé   | ajouter volumes (option avancée) |

---

# 7. Nettoyage TP

Dans Docker Desktop :

* Stop container
* Remove container
* Remove image (si demandé)

---

# 8. Synthèse pédagogique

### Docker Desktop sur macOS / Linux

* Interface graphique identique
* Gestion des conteneurs unifiée
* DVWA fonctionne sans terminal

### Concepts travaillés

* Image Docker
* Conteneur
* Port mapping
* Logs
* Cycle de vie d’un service

---

# 9. Résultat attendu

À la fin du TP :

* Docker Desktop installé
* DVWA fonctionnel
* Accès via navigateur :

```
http://localhost:8080
```

---

