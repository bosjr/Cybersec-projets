# TP – Vérification installation Docker Desktop (Windows 11)

## Objectif

Valider que Docker Desktop est correctement installé et fonctionnel (WSL2 + moteur Docker + exécution de conteneurs).

---

## Vérification WSL2 (important sur Windows)

```powershell
wsl -l -v
```

## 1. Vérification du moteur Docker

### Commande

```bash
docker version
```

### Attendu

* Client Docker présent
* Server (Engine) accessible
* Aucune erreur de connexion

---

## 2. Vérification du service Docker

```bash
docker info
```

### Attendu 2

* WSL2 backend indiqué
* “Containers: running” ou informations système affichées
* Pas d’erreur “cannot connect to the Docker daemon”

---

## 3. Test d’exécution d’un conteneur simple

```bash
docker run hello-world
```

### Attendu 3

* Téléchargement de l’image
* Message :

```text
Hello from Docker!
This message shows that your installation appears to be working correctly.
```

---

## 4. Vérification des conteneurs actifs

```bash
docker ps
```

### Attendu 4

docker ps

Affiche uniquement les conteneurs en cours d’exécution.

* Liste vide ou conteneurs actifs
* Pas d’erreur

---

## 5. Vérification des conteneurs arrêtés

```bash
docker ps -a
```

### Attendu 5

* présence possible de `hello-world`

docker ps -a

Affiche tous les conteneurs :

en cours d’exécution,
arrêtés,
terminés,
en erreur.

---

## 6. Test réseau Docker

```bash
docker run --rm alpine ping -c 3 google.com
```

Alpine Linux est une distribution Linux très légère souvent utilisée pour :

les tests,
les conteneurs minimalistes,
les environnements Docker rapides.

Si l’image n’existe pas localement, Docker la télécharge automatiquement depuis Docker Hub

### Attendu 6

* résolution DNS OK
* ping réussi

---

## Critères de validation

✔ WSL2 actif
✔ Docker Engine répond
✔ `hello-world` fonctionne
✔ Pas d’erreur de daemon
✔ Réseau conteneur OK

---

## Si échec (diagnostic rapide)

| Problème                 | Cause probable              |
| ------------------------ | --------------------------- |
| docker command not found | Docker Desktop non installé |
| Cannot connect to daemon | Docker Desktop non démarré  |
| WSL error                | WSL2 non installé           |
| hello-world fail         | réseau ou proxy             |

---

## Conclusion TP

Si tous les tests sont OK :

## Docker Desktop est opérationnel pour TP DVWA / Git / SOC

---
