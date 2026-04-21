
# 📄 docs/03-dvwa.md (très guidé)

## 🎯 Objectif : Découverte d'une vulnérabilité avec DVWA

Découvrir une vulnérabilité web simple : **l’injection SQL**.

Vous allez :

- tester une faille
- observer le résultat
- comprendre le principe

---

## ⚙️ 1. Accéder à DVWA

Dans votre navigateur :

[http://localhost:8080](http://localhost:8080)

---

## 🔐 2. Connexion

Identifiants par défaut :

- login : admin
- mot de passe : password

---

## 🛠️ 3. Configuration

1. Aller dans le menu **DVWA Security**
2. Mettre le niveau sur : **Low**
3. Cliquer sur **Submit**

---

## 🔎 4. Accéder à la fonctionnalité vulnérable

1. Aller dans **SQL Injection**
2. Vous voyez un champ permettant d’entrer un ID

---

## 🧪 5. Test normal

Entrer : 1

👉 Résultat :

- une seule entrée s’affiche

---

## 💥 6. Test de la faille

Entrer : 1' OR '1'='1


---

## 👀 7. Observation

👉 Résultat attendu :

- plusieurs utilisateurs apparaissent
- la requête est détournée

---

## 🧠 8. Comprendre simplement

L’application construit une requête SQL avec votre saisie.

👉 Problème :

- la saisie utilisateur n’est pas contrôlée

👉 Conséquence :

- il est possible de modifier la requête

---

## 📊 Explication simplifiée

Entrée utilisateur : 1' OR '1'='1


👉 Cela transforme la requête en :

SELECT * FROM users WHERE id = '1' OR '1'='1';

```md

👉 Condition toujours vraie → toutes les données sont affichées

---

## 📸 9. Travail demandé

Faire une capture d’écran :
- du test normal
- du test avec injection

---

## ✏️ 10. À rédiger dans votre README

### Questions

1. Que se passe-t-il lors de l’injection ?
2. Pourquoi cela fonctionne-t-il ?

---

## 🛡️ 11. Comment corriger (niveau débutant)

Solutions simples :

- filtrer les entrées utilisateur
- utiliser des requêtes sécurisées

👉 Exemple (principe) :
- requêtes préparées
- ne pas concaténer directement les entrées utilisateur

---

## 📌 À retenir

- une injection SQL exploite une mauvaise gestion des entrées
- elle permet d’accéder à des données non prévues
- c’est une faille fréquente

---

## 🎯 Objectif validé

Vous savez :
- tester une vulnérabilité simple
- comprendre son fonctionnement
- expliquer le problème

---

## ➡️ Suite

Passer à la rédaction du projet final

## Attendu

- capture écran
- explication simple
