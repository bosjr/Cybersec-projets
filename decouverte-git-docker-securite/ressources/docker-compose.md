
# Docker : Build & Compose 🐳

_Construire ses images et orchestrer ses conteneurs_

---

## Rappel express ⚡

--

### Ce qu'on sait déjà

- **Image** = la recette (immuable) 📦
- **Conteneur** = le plat servi (instance d'une image) 🍽️
- **DockerHub** = le supermarché des images 🛒

Aujourd'hui, on apprend à **cuisiner nos propres recettes** ! 👨‍🍳

---

## Le Dockerfile 📄

_La recette de votre image_

--

### C'est quoi ?

Un fichier texte qui décrit **étape par étape** comment construire une image Docker.

Comme une recette de cuisine : on part d'une base, on ajoute des ingrédients, on configure 🧑‍🍳

--

### Les instructions essentielles

- **FROM** — l'image de base (point de départ)
- **RUN** — exécuter une commande pendant le build
- **COPY** — copier des fichiers locaux dans l'image
- **WORKDIR** — définir le répertoire de travail
- **EXPOSE** — déclarer un port
- **CMD** — la commande lancée au démarrage du conteneur

--

### Exemple : un serveur web simple

```dockerfile
FROM nginx:alpine

COPY ./mon-site/ /usr/share/nginx/html/

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
```

_4 lignes et on a une image prête à servir notre site !_ 🚀

--

### Exemple : une app Node.js

```dockerfile
FROM node:20-alpine

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .

EXPOSE 3000

CMD ["node", "server.js"]
```

<em style="font-size:smaller">On copie d'abord le package.json pour profiter du <b>cache Docker</b> sur les dépendances 🧠</em>

---

## Docker Build 🔨

_Transformer un Dockerfile en image_

--

### La commande magique

```bash
docker build -t mon-app:v1 .
```

- `-t mon-app:v1` → le nom et le tag de l'image
- `.` → le contexte de build (le dossier courant)

--

### Les layers (couches) 🧅

Chaque instruction du Dockerfile crée une **couche** :

- Les couches sont **mises en cache** 💾
- Si rien ne change → pas de rebuild
- D'où l'importance de l'**ordre des instructions**

<em style="font-size:smaller">Astuce : mettez les éléments qui changent le moins souvent en premier !</em>

--

### Le .dockerignore 🚫

Comme un `.gitignore`, mais pour Docker :

```
node_modules
.git
.env
*.md
```

Évite d'envoyer des fichiers inutiles dans le contexte de build.

---

## Bonnes pratiques Dockerfile 📋

--

### Les réflexes à avoir

- 🪶 Utiliser des images **légères** (`alpine`)
- 📦 **Minimiser** le nombre de couches (combiner les RUN)
- 🔒 Ne **jamais** mettre de secrets dans l'image
- 👤 Utiliser un **utilisateur non-root** quand c'est possible

--

### Exemple : combiner les RUN

❌ Mauvais :

```dockerfile
RUN apt-get update
RUN apt-get install -y curl
RUN apt-get install -y vim
```

✅ Mieux :

```dockerfile
RUN apt-get update && apt-get install -y \
    curl \
    vim \
    && rm -rf /var/lib/apt/lists/*
```

---

## Docker Compose 🎼

_Orchestrer plusieurs conteneurs_

--

### Le problème

Une application web moderne, c'est souvent :

- 🌐 Un frontend (Nginx, Apache...)
- ⚙️ Un backend (Node, PHP, Python...)
- 🗄️ Une base de données (MySQL, PostgreSQL...)
- 📦 Un cache (Redis...)

Gérer tout ça à la main avec `docker run` ? 😩

--

### La solution : Docker Compose

Un fichier `docker-compose.yml` qui décrit **toute l'architecture** :

Quels conteneurs, quels réseaux, quels volumes, quelles dépendances.

_Analogie : le chef d'orchestre qui coordonne tous les musiciens_ 🎵

--

### Syntaxe YAML — rappel express

```yaml
# Un commentaire
cle: valeur
liste:
  - element1
  - element2
objet:
  sous_cle: sous_valeur
```

<em style="font-size:smaller">C'est comme du JSON, mais plus lisible (et sensible à l'indentation !)</em>

---

## Exemple concret 🖥️

_Une stack LAMP en Docker Compose_

--

### Le fichier docker-compose.yml

```yaml
services:
  web:
    image: php:8.2-apache
    ports:
      - "8080:80"
    volumes:
      - ./src:/var/www/html
    depends_on:
      - db

  db:
    image: mariadb:11
    environment:
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: myapp
    volumes:
      - db_data:/var/lib/mysql

volumes:
  db_data:
```

--

### Décryptage 🔍

- **services** : les conteneurs à lancer
- **image** : quelle image utiliser
- **ports** : mapping host → conteneur
- **volumes** : persistance des données
- **depends_on** : ordre de démarrage
- **environment** : variables d'environnement

---

## Les commandes Compose 🧰

--

### Les essentielles

- `docker compose up -d` → tout lancer en arrière-plan 🚀
- `docker compose down` → tout arrêter et nettoyer 🧹
- `docker compose ps` → voir l'état des services 👀
- `docker compose logs -f` → suivre les logs en temps réel 📋

--

### Les pratiques

- `docker compose build` → rebuild les images custom 🔨
- `docker compose exec web bash` → entrer dans un conteneur 🐚
- `docker compose restart web` → redémarrer un service ♻️
- `docker compose pull` → mettre à jour les images ⬇️

---

## Réseaux dans Compose 🌐

--

### Par défaut

Docker Compose crée automatiquement un réseau pour chaque projet.

Les conteneurs se trouvent par leur **nom de service** !

```yaml
# Dans le code PHP :
# host = "db" (pas "localhost" ni "127.0.0.1")
$pdo = new PDO("mysql:host=db;dbname=myapp", "root", "secret");
```

--

### Réseaux custom

```yaml
services:
  web:
    networks:
      - frontend
      - backend
  db:
    networks:
      - backend

networks:
  frontend:
  backend:
```

<em style="font-size:smaller">Le service <code>db</code> n'est pas accessible depuis le réseau <code>frontend</code> → segmentation ! 🔒</em>

---

## Volumes & persistance 💾

--

### Le problème

Un conteneur est **éphémère** : si on le supprime, les données disparaissent 💨

Solution : les **volumes** !

--

### Deux types

- **Named volumes** : gérés par Docker, persistants
  `db_data:/var/lib/mysql`
- **Bind mounts** : lien vers un dossier de l'hôte
  `./src:/var/www/html`

<em style="font-size:smaller">Bind mounts = pratique en dév. Named volumes = recommandé en prod</em>

---

## Variables d'environnement 🔐

--

### Le fichier .env

```env
MYSQL_ROOT_PASSWORD=supersecret
MYSQL_DATABASE=myapp
APP_PORT=8080
```

```yaml
services:
  db:
    image: mariadb:11
    environment:
      MYSQL_ROOT_PASSWORD: ${MYSQL_ROOT_PASSWORD}
      MYSQL_DATABASE: ${MYSQL_DATABASE}
  web:
    ports:
      - "${APP_PORT}:80"
```

⚠️ Ne commitez **jamais** le fichier `.env` !

---

## En résumé 📝

- 📄 **Dockerfile** = recette pour construire une image
- 🔨 **docker build** = cuire la recette
- 🎼 **Docker Compose** = orchestrer plusieurs conteneurs
- 📋 **docker-compose.yml** = la partition de l'orchestre

Prochaine étape : l'orchestration à grande échelle avec Docker Swarm ! 🚀
