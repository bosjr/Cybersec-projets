# Création d'une image Docker simple

## Objectif

Créer une image Docker personnalisée contenant un serveur web Apache affichant une page HTML personnalisée.

## Étape 1 : Créer un dossier de travail

Créer un répertoire dédié :

```bash
mkdir docker-web
cd docker-web
```

Vérification :

```bash
pwd
```

Résultat :

```bash
/home/kali/docker-web
```

---

## Étape 2 : Créer une page HTML

Créer un fichier :

```bash
nano index.html
```

Contenu :

```html
<html>
<head>
<title>Mon serveur Docker</title>
</head>
<body>
<h1>Hello depuis Docker</h1>
</body>
</html>
```

Sauvegarder le fichier.

---

## Étape 3 : Créer un Dockerfile

Créer le fichier :

```bash
nano Dockerfile
```

Contenu :

```dockerfile
FROM httpd:latest

COPY index.html /usr/local/apache2/htdocs/
```

Explication :

* `FROM` : image de base utilisée
* `COPY` : copie le fichier dans le conteneur

---

## Étape 4 : Construire l'image

Construire l'image :

```bash
docker build -t monsite .
```

Résultat attendu :

```bash
Successfully built xxxxx
Successfully tagged monsite:latest
```

Lister les images :

```bash
docker images
```

Exemple :

```bash
REPOSITORY   TAG      IMAGE ID
monsite      latest   a8f1234bcdef
httpd        latest   c56abc789def
```

L'image a été créée.

---

## Étape 5 : Lancer le conteneur

Exécuter :

```bash
docker run -d -p 8080:80 monsite
```

Options :

* `-d` : arrière-plan
* `-p` : publication du port local

Vérification :

```bash
docker ps
```

Exemple :

```bash
CONTAINER ID   IMAGE      PORTS
8d12e4fa       monsite    0.0.0.0:8080->80/tcp
```

---

## Étape 6 : Vérification

Accéder depuis un navigateur :

```text
http://localhost:8080
```

Affichage attendu :

```text
Hello depuis Docker
```

---

## Bonnes pratiques

* Éviter d'utiliser `latest` en production.
* Utiliser des versions fixes :

```dockerfile
FROM httpd:2.4.65
```

* Scanner les images :

```bash
docker scout quickview monsite
```

ou :

```bash
trivy image monsite
```

* Utiliser des images minimales pour réduire la surface d'attaque.

---

## Nettoyage

Arrêt :

```bash
docker ps
docker stop ID_CONTENEUR
```

Suppression :

```bash
docker rm ID_CONTENEUR
docker rmi monsite
```

