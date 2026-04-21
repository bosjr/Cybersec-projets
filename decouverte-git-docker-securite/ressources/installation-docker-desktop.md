
# Installation et utilisation de Docker Desktop avec DVWA

## 1. Pré-requis

* **Système d’exploitation** : Windows 10/11 64-bit, macOS ou Linux (si Linux, Docker Desktop ou Docker Engine + Docker Compose).
* **Virtualisation activée** dans le BIOS.
* **Compte Docker Hub** (optionnel mais recommandé pour pull d’images publiques).

## 2. Installation de Docker Desktop

### Windows / macOS

1. Télécharger Docker Desktop depuis le site officiel :
   [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
2. Lancer l’installeur et suivre les instructions.
3. Vérifier l’installation :

   ```bash
   docker --version
   docker compose version
   ```
4. Optionnel : Se connecter avec un compte Docker Hub :

   ```bash
   docker login
   ```

Oui, ce write-up est **entièrement valable pour Windows 11**, avec quelques précisions spécifiques :

---

### Points spécifiques à Windows 11

1. **Virtualisation** :

   * Assurez-vous que **Hyper-V** et **WSL 2** sont activés.

     * Hyper‑V : `Panneau de configuration → Programmes → Activer ou désactiver des fonctionnalités Windows → Hyper-V`
     * WSL 2 : `wsl --install` (dans PowerShell en admin)
   * Docker Desktop sur Windows 11 utilise généralement **WSL 2 backend**, donc WSL 2 doit être installé.

2. **Installation de Docker Desktop** :

   * Télécharger la version Windows sur [Docker Desktop](https://www.docker.com/products/docker-desktop).
   * L’installateur active Hyper‑V et WSL 2 si nécessaire.
   * Redémarrer la machine après installation.

3. **Exécution des conteneurs DVWA** :

   * La commande `docker pull vulnerables/web-dvwa` fonctionne directement.
   * `docker compose up -d` fonctionne dans PowerShell ou CMD (si Docker Desktop est lancé).
   * Accès à DVWA : [http://localhost:8080](http://localhost:8080) dans un navigateur Windows.

4. **Volumes et persistances** :

   * Docker Desktop gère les volumes automatiquement sous Windows, mais pour les bases de données, tu peux définir un volume explicitement dans `docker-compose.yml` pour éviter toute perte de données après un redémarrage.

---


### Linux (Ubuntu/Debian)

1. Mettre à jour le système :

   ```bash
   sudo apt update
   sudo apt upgrade -y
   ```
2. Installer les dépendances :

   ```bash
   sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
   ```
3. Ajouter le dépôt Docker et installer :

   ```bash
   curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
   echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
   sudo apt update
   sudo apt install docker-ce docker-ce-cli containerd.io docker-compose-plugin -y
   ```
4. Vérifier :

   ```bash
   docker --version
   docker compose version
   ```

---

## 3. Configuration initiale

* Vérifier que Docker Desktop fonctionne via l’interface graphique ou la commande :

  ```bash
  docker info
  ```
* Ajouter votre utilisateur au groupe docker pour exécuter les commandes sans `sudo` :

  ```bash
  sudo usermod -aG docker $USER
  newgrp docker
  ```

---

## 4. Importer et lancer DVWA

### Étape 1 : Pull de l’image DVWA

* Depuis Docker Hub, l’image DVWA officielle est souvent `vulnerables/web-dvwa` :

  ```bash
  docker pull vulnerables/web-dvwa
  ```

### Étape 2 : Lancer DVWA avec Docker Compose

* Créer un fichier `docker-compose.yml` minimal pour DVWA :

```yaml
version: '3.7'
services:
  dvwa:
    image: vulnerables/web-dvwa
    container_name: dvwa
    ports:
      - "8080:80"
    restart: always
    environment:
      MYSQL_PASSWORD: dvwa
      MYSQL_USER: dvwa
      MYSQL_DATABASE: dvwa
      MYSQL_ROOT_PASSWORD: root
```

* Lancer les conteneurs :

  ```bash
  docker compose up -d
  ```

### Étape 3 : Vérifier le fonctionnement

* Accéder à DVWA via un navigateur :

  ```
  http://localhost:8080
  ```
* Les identifiants par défaut :
  **Login** : `admin`
  **Mot de passe** : `password`

---

## 5. Commandes utiles Docker / Docker Compose

| Commande                   | Description                                    |
| -------------------------- | ---------------------------------------------- |
| `docker ps`                | Lister les conteneurs en cours                 |
| `docker stop <container>`  | Arrêter un conteneur                           |
| `docker start <container>` | Démarrer un conteneur arrêté                   |
| `docker logs <container>`  | Afficher les logs d’un conteneur               |
| `docker compose down`      | Arrêter et supprimer les conteneurs et réseaux |

---

## 6. Bonnes pratiques

* Toujours utiliser un volume pour la persistance de la base de données si besoin :

  ```yaml
  volumes:
    - dvwa_db_data:/var/lib/mysql
  ```
* Ne jamais exposer DVWA directement sur internet, uniquement en laboratoire local.
* Sauvegarder les images Docker importantes pour réutilisation :

  ```bash
  docker save -o dvwa.tar vulnerables/web-dvwa
  docker load -i dvwa.tar
  ```

---

