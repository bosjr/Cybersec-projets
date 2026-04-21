# TP Étudiants — Installation Docker Desktop + DVWA (100% GUI + WSL2)

## Objectif

Installer **Docker Desktop sur Windows 11**, activer **WSL2**, puis déployer une application vulnérable (**DVWA**) uniquement via l’interface graphique.

---

# 1. Pré-requis

* Windows 11 64 bits
* Droits administrateur
* Virtualisation activée (BIOS)
* Connexion Internet

---

# 2. Activation WSL2 (obligatoire pour Docker Desktop)

## Étape 1 — Activer WSL via interface Windows

1. Ouvrir :

   ```
   Panneau de configuration → Programmes → Activer ou désactiver des fonctionnalités Windows
   ```
2. Cocher :

   * ✔ Windows Subsystem for Linux
   * ✔ Virtual Machine Platform
   * ✔ Hyper-V (si présent)
3. Redémarrer le PC

---

## Étape 2 — Installer WSL2 (GUI + simple commande)

Après redémarrage :

1. Ouvrir **PowerShell (Admin)**
2. Lancer :

```powershell
wsl --install
```

3. Redémarrer si demandé

---

## Erreurs courantes WSL2

| Problème                | Cause                        | Solution                      |
| ----------------------- | ---------------------------- | ----------------------------- |
| WSL non reconnu         | Fonction Windows non activée | Activer WSL + reboot          |
| Erreur kernel           | WSL1 au lieu de WSL2         | `wsl --set-default-version 2` |
| Virtualisation inactive | BIOS désactivé               | Activer Intel VT-x / AMD-V    |

---

# 3. Installation Docker Desktop (GUI)

## Étape 1 — Téléchargement

* Aller sur :
  [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)

* Télécharger **Docker Desktop for Windows**

---

## Étape 2 — Installation

1. Lancer l’installeur
2. Cocher :

   * ✔ Use WSL2 instead of Hyper-V (si proposé)
3. Installer
4. Redémarrer

---

## Étape 3 — Vérification GUI

Ouvrir Docker Desktop :

* Statut attendu :

  * 🟢 Engine running
  * 🟢 WSL integration enabled

---

## Erreurs courantes Docker Desktop

| Problème                | Cause                | Solution                             |
| ----------------------- | -------------------- | ------------------------------------ |
| Docker ne démarre pas   | WSL2 absent          | Installer WSL2                       |
| “WSL integration error” | distro Linux absente | installer Ubuntu via Microsoft Store |
| Docker lent             | Hyper-V forcé        | vérifier WSL2 backend                |
| CPU 100%                | mauvaise config      | limiter ressources Docker            |

---

# 4. Vérification via interface Docker Desktop

Dans Docker Desktop :

## Onglet Settings → Resources

* RAM : 4 Go minimum recommandé
* CPU : 2 cœurs minimum

## Onglet WSL Integration

* Activer Ubuntu (ou distro installée)

---

# 5. Installation DVWA (via GUI uniquement)

## Étape 1 — Recherche image

1. Aller dans **Docker Desktop**
2. Onglet **Images**
3. Cliquer **Search**
4. Rechercher :

   ```
   vulnerables/web-dvwa
   ```

---

## Étape 2 — Télécharger (Pull)

* Cliquer sur **Pull**
* Attendre téléchargement

---

## Étape 3 — Lancer DVWA

1. Cliquer sur l’image téléchargée
2. Cliquer **Run**

## Paramètres à configurer :

* Port mapping :

  ```
  8080 → 80
  ```

---

## Étape 4 — Accès DVWA

Dans navigateur Windows :

```
http://localhost:8080
```

Identifiants :

* Login : `admin`
* Password : `password`

---

# 6. Vérification fonctionnement

Dans Docker Desktop :

* Onglet **Containers**

  * DVWA doit être **green (running)**

---

# 7. Erreurs courantes DVWA

| Problème               | Cause              | Solution                          |
| ---------------------- | ------------------ | --------------------------------- |
| Page inaccessible      | mauvais port       | vérifier 8080:80                  |
| Container restart loop | dépendances MySQL  | utiliser image stable             |
| Timeout navigateur     | firewall           | autoriser localhost               |
| DVWA reset             | container supprimé | utiliser volumes (option avancée) |

---

# 8. Nettoyage (important en TP)

Dans Docker Desktop :

* Stop container
* Remove container
* Remove image (optionnel)

---

# 9. Synthèse pédagogique

* WSL2 = moteur Linux intégré Windows
* Docker Desktop = interface + moteur conteneur
* DVWA = application vulnérable locale
* Tout fonctionne **sans terminal**

---

# 10. Résultat attendu

À la fin du TP :

* Docker Desktop installé et fonctionnel
* WSL2 actif
* DVWA accessible sur :

  ```
  http://localhost:8080
  ```
* Étudiants capables de :

  * lancer un conteneur
  * lire état via GUI
  * supprimer / redémarrer un service

---

