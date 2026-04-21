
# Commandes docker utiles

## Docker, c’est quoi ?

Docker sert à empaqueter une application avec tout ce dont elle a besoin pour fonctionner, puis à l’exécuter dans un conteneur léger. Un conteneur partage le noyau du système hôte, ce qui le rend plus rapide et plus souple qu’une machine virtuelle classique. 

## Vocabulaire essentiel

- **Image** : modèle immuable servant de base pour créer des conteneurs.
- **Conteneur** : instance en cours d’exécution d’une image.
- **Dockerfile** : fichier qui décrit comment construire une image.
- **Volume** : espace de stockage persistant pour conserver les données.
- **Docker Compose** : outil pour lancer plusieurs services avec un fichier YAML.

## Installation et vérification

Après installation, on vérifie généralement que Docker fonctionne avec une première exécution de conteneur de test. Les tutoriels débutants recommandent de commencer par un conteneur simple pour valider l’installation avant de passer à des cas plus avancés. 

Exemple :

```bash
docker run hello-world
```

## Commandes de base

Voici les commandes les plus utiles pour débuter :

- `docker pull` : télécharger une image.
- `docker run` : télécharger et lancer un conteneur.
- `docker ps` : lister les conteneurs en cours.
- `docker ps -a` : lister tous les conteneurs.
- `docker logs` : consulter les journaux.
- `docker exec -it` : entrer dans un conteneur.
- `docker stop` et `docker rm` : arrêter et supprimer un conteneur.

Exemple :

```bash
docker run -d -p 8080:80 --name mon-nginx nginx
docker ps
docker logs mon-nginx
docker exec -it mon-nginx sh
```

## Les volumes

Par défaut, les données dans un conteneur sont temporaires : si le conteneur disparaît, les données peuvent aussi disparaître. Les volumes servent à conserver ces données de façon persistante, ce qui est indispensable pour une base de données ou un site web avec fichiers.

Exemple :

```bash
docker volume create mon_volume
```

## Docker Compose

Docker Compose est pratique dès qu’une application dépend de plusieurs services, par exemple une API, une base de données et un front-end. Il permet de tout définir dans un fichier unique et de démarrer l’ensemble avec une seule commande.

Commandes utiles :

```bash
docker compose up -d
docker compose logs -f
docker compose down
```


## Bonnes pratiques de départ

- Utiliser des images légères quand c’est possible.
- Garder un conteneur pour un service principal.
- Utiliser des volumes pour les données persistantes.
- Préférer Docker Compose pour les stacks multi-services.

## Mini TP

1. Installer Docker.
2. Lancer `docker run hello-world`.
3. Lancer un serveur web simple avec `nginx`.
4. Lire les logs avec `docker logs`.
5. Entrer dans le conteneur avec `docker exec -it`.
6. Tester la persistance avec un volume.
7. Refaire l’exercice avec Docker Compose.

## Ressources

[datacamp](https://www.datacamp.com/fr/tutorial/docker-tutorial)
[thecodingmachine](https://thecodingmachine.com/commencer-avec-docker/)
[labsdevops](https://labsdevops.fr/blog/docker-guide-debutant) 