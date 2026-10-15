# Création d'une image Docker simple sous Windows

## Objectif

Créer une image Docker personnalisée sous Windows avec Docker Desktop contenant un serveur web Apache affichant une page HTML personnalisée.

Environnement :

* Windows 10/11
* Docker Desktop installé
* PowerShell ou Terminal

---

## Étape 1 : Créer un dossier de travail

Ouvrir PowerShell ou Terminal :

```powershell
mkdir C:\docker-web

cd C:\docker-web
```

Vérification :

```powershell
pwd
```

Résultat :

```textV
Path
----
C:\docker-web
```

---

## Étape 2 : Créer une page HTML

Créer un fichier :

```powershell
notepad index.html
```

Cliquer sur **Oui** si le fichier n'existe pas.

Contenu :

```html
<html>
<head>
<title>Mon serveur Docker</title>
</head>

<body>
<h1>Hello depuis Docker sous Windows</h1>
</body>
</html>
```

Enregistrer puis fermer.

Vérification :

```powershell
dir
```

Résultat :

```text
Directory: C:\docker-web

Mode      LastWriteTime
----      -------------
-a----    index.html
```

---

## Étape 3 : Créer le Dockerfile

Créer le fichier :

```powershell
notepad Dockerfile
```

Attention : le fichier doit s'appeler exactement :

```text
Dockerfile
```

Pas :

```text
Dockerfile.txt
```
sinon renommer en Dockerfile (supprimer extension .txt)
mv .\Dockerfile.txt .\Dockerfile

Contenu :

```dockerfile
FROM httpd:latest

COPY index.html /usr/local/apache2/htdocs/
```

Explication :

* `FROM` : image de base Apache
* `COPY` : copie le fichier HTML dans le conteneur

---

## Étape 4 : Construire l'image Docker

Construire l'image :

```powershell
docker build -t monsite .
```

Le `.` indique le répertoire courant.

Résultat attendu :

```text
[+] Building ...
Successfully built 1a2b3c4d
Successfully tagged monsite:latest
```

---

## Étape 5 : Vérifier l'image créée

Lister les images :

```powershell
docker images
```

Exemple :

```text
REPOSITORY     TAG       IMAGE ID
monsite        latest    a1b2c3d4
httpd          latest    c5d6e7f8
```

L'image `monsite` est maintenant disponible localement.

---

## Étape 6 : Démarrer le conteneur

Exécuter :

```powershell
docker run -d -p 8080:80 monsite
```

Paramètres :

* `-d` : exécution en arrière-plan
* `-p` : port local → port conteneur

---

## Étape 7 : Vérification

Contrôler :

```powershell
docker ps
```

Exemple :

```text
CONTAINER ID     IMAGE      PORTS
95bbbaf121f9     monsite    0.0.0.0:8080->80/tcp
```

Accéder depuis le navigateur :

```text
http://localhost:8080
```

Résultat attendu :

```text
Hello depuis Docker sous Windows
```

---

## Étape 8 : Arrêt et suppression

Lister :

```powershell
docker ps -a
```

Arrêter :

```powershell
docker stop 95bbbaf121f9
```

Supprimer le conteneur :

```powershell
docker rm 95bbbaf121f9
```

Supprimer l'image :

```powershell
docker rmi monsite
```

Si Docker refuse :

```powershell
docker rmi -f monsite
```

---

## Bonnes pratiques sécurité

Éviter :

```dockerfile
FROM httpd:latest
```

Préférer une version fixe :

```dockerfile
FROM httpd:2.4.65
```

Scanner l'image :

```powershell
docker scout quickview monsite
```

ou :

```powershell
docker scan monsite
```

Limiter l'utilisation de `latest` réduit les changements imprévus et facilite la reproductibilité des déploiements.
