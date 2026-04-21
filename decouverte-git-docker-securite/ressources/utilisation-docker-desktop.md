
# Utilisation de Docker Desktop via l’interface graphique

## 1. Accès à l’interface Docker Desktop

* Ouvrir **Docker Desktop** depuis le menu Démarrer (Windows) ou Applications (macOS).
* La fenêtre principale affiche :

  * **Conteneurs / Apps** : liste des conteneurs en cours et arrêtés.
  * **Images** : toutes les images Docker présentes sur la machine.
  * **Volumes** : stockages persistants.
  * **Settings / Preferences** : configuration des ressources (CPU, RAM, disque).

---

## 2. Exemple : Hello World

1. Dans l’onglet **Images** :

   * Cliquer sur **Pull** pour rechercher l’image `hello-world`.
   * Docker Desktop télécharge l’image depuis Docker Hub.

2. Exécuter le conteneur :

   * Cliquer sur l’image `hello-world`.
   * Cliquer sur **Run**.
   * La console intégrée affiche le message "Hello from Docker!".

> Cela confirme que Docker fonctionne correctement sans passer par le terminal.

---

## 3. Lister les conteneurs

* Onglet **Containers / Apps** :

  * Les conteneurs actifs apparaissent en vert.
  * Les conteneurs arrêtés apparaissent en gris.
  * Pour chaque conteneur, on peut :

    * **Start** : démarrer un conteneur arrêté.
    * **Stop** : arrêter un conteneur en cours.
    * **Restart** : redémarrer un conteneur.
    * **Logs** : afficher les logs dans une fenêtre intégrée.

---

## 4. Lancer un conteneur interactif (exemple Ubuntu)

1. Dans l’onglet **Images**, chercher et pull `ubuntu:22.04`.
2. Cliquer sur **Run** :

   * Cocher **Interactive / Terminal**.
   * Docker Desktop ouvre une console interactive attachée au conteneur.
   * Vous pouvez exécuter des commandes Linux comme `/bin/bash`, `ls`, etc.

---

## 5. Gérer les volumes et données persistantes

* Onglet **Volumes** :

  * Créer un nouveau volume pour stocker des données persistantes (ex : bases MySQL).
  * Lors du lancement d’un conteneur via GUI, sélectionner le volume à monter.

---

## 6. Supprimer des conteneurs ou images

* Conteneurs : cliquer sur **… → Remove** pour supprimer un conteneur.
* Images : cliquer sur **… → Remove** pour libérer de l’espace disque.

---

## 7. Points pratiques GUI vs Terminal

| Action              | GUI               | Terminal                  |
| ------------------- | ----------------- | ------------------------- |
| Lister conteneurs   | Onglet Containers | `docker ps -a`            |
| Lancer conteneur    | Run sur image     | `docker run`              |
| Voir logs           | Bouton Logs       | `docker logs <container>` |
| Supprimer conteneur | Remove            | `docker rm <container>`   |
| Pull image          | Pull bouton       | `docker pull <image>`     |

---

