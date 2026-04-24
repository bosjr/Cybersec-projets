# TP – Vérification installation Docker Desktop (Windows 11)

## Objectif

Valider que Docker Desktop est correctement installé et fonctionnel (WSL2 + moteur Docker + exécution de conteneurs).

---

## 1. Vérification du moteur Docker

### Commande

```bash id="t1"
docker version
```

### Attendu t1

* Client Docker présent
* Server (Engine) accessible
* Aucune erreur de connexion

---

## 2. Vérification du service Docker

```bash id="t2"
docker info
```

### Attendu t2

* WSL2 backend indiqué
* “Containers: running” ou informations système affichées
* Pas d’erreur “cannot connect to the Docker daemon”

---

## 3. Test d’exécution d’un conteneur simple

```bash id="t3"
docker run hello-world
```

### Attendu t3

* Téléchargement de l’image
* Message :

```text
Hello from Docker!
This message shows that your installation appears to be working correctly.
```

---

## 4. Vérification des conteneurs actifs

```bash id="t4"
docker ps
```

### Attendu t4

* Liste vide ou conteneurs actifs
* Pas d’erreur

---

## 5. Vérification des conteneurs arrêtés

```bash id="t5"
docker ps -a
```

### Attendu t5

* présence possible de `hello-world` (Exited)

---

## 6. Vérification WSL2 (important sur Windows)

```powershell id="t6"
wsl -l -v
```

### Attendu t6

* `docker-desktop`
* `docker-desktop-data`
* Version 2

---

## 7. Test réseau Docker

```bash id="t7"
docker run --rm alpine ping -c 3 google.com
```

### Attendu t7

* résolution DNS OK
* ping réussi

---

## Critères de validation

✔ Docker Engine répond
✔ `hello-world` fonctionne
✔ WSL2 actif
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
