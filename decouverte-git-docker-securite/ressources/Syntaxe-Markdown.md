# Récapitulatif ce la syntaxe Markdown pour fichiers `.md` (GitHub-Flavored Markdown) avec focus liens et mise en page

## Titres et structure

```texte
# Titre principal (H1) ← UNIQUEMENT pour titre page
## Section (H2)
### Sous-section (H3)
#### Sous-sous-section (H4)
```

## Mise en forme texte

```texte
**gras** ou __gras__
*italique* ou _italique_
***gras+italique***
`code inline`
~~barré~~
```

## Listes

```texte
- Élément liste (tiret, étoile *, +)
  - Sous-élément (indentation 2 espaces)

1. Liste numérotée
2. Continue auto
```

## Liens (votre priorité)

```texte
[Texte](url)                           # Lien externe
[Tutoriel](01-github.md)               # Fichier même dossier
[Git](./etudiants/git-proc.md)         # Sous-dossier
[Retour](../README.md)                 # Dossier parent
[DVWA](https://example.com) # GitHub repo
```

## Images

```texte
![Alt texte](image.png)                # Même dossier
![Logo](./img/logo.png)                # Sous-dossier img
```

## Tableaux

```tableau
| Logiciel | Windows | macOS | Linux |
|----------|---------|-------|-------|
| Git      | ✅ exe  | ✅ dmg | ✅ apt |
| Desktop  | ✅ exe  | ✅ dmg | ❌     |
```

## Blocs code

```bash
git clone url

```

ou

```bash
git status
```

## Séparateurs

---
📚 ÉMOJIS TP/CYBERSÉCURITÉ

📝 TP/Docs        🔒 Sécurité       🐛 Vulnérabilité
💻 Terminal       🖥️ Windows        🍎 macOS
🐧 Linux/Kali     ⚙️ Config         ✅ OK/Validé
❌ Erreur         ⚠️ Attention       🚀 Succès
📁 Dossier        📄 Fichier        🔗 Lien
📸 Capture        🎯 Objectif       ⏳ En cours

📚 TP1 Git/GitHub

✅ **Objectifs** : [01-github.md]
🔧 **Étapes** : 
  - Installation Git ✅
  - GitHub Desktop 🚀
  - Premier commit 🎯

🎯 RÈGLES ESPACES & SAUTS DE LIGNE

| Action                  | Syntaxe                                 | Rendu             |
| ----------------------- | --------------------------------------- | ----------------- |
| Nouveau paragraphe      | Ligne 1<ligne vide>Ligne 2              | Paragraphe séparé |
| Saut ligne (même para.) | Ligne 1  (2 espaces fin ligne + Entrée) | Ligne 1Ligne 2    |
| Liste sous-élément      | - Sous-item(2 espaces début ligne)      | - Sous-item       |


## Voici les **meilleurs plugins VSCode pour mise en forme Markdown**

## 🎯 **EXTENSION #1 : Markdown All in One** ⭐

``` text
👉 Marketplace : "Markdown All in One" (yzhang)
✅ Raccourcis auto : Ctrl+B (gras), Ctrl+I (italique)
✅ Ctrl+Shift+V : Preview côte à côte
✅ Ctrl+Shift+P > "Print to HTML/PDF"
✅ Table des matières auto
✅ Formatage listes/tables
```

## 🛠️ **EXTENSION PACK COMPLÈTE**

``` text
1. Markdown All in One  ← OBLIGATOIRE
2. markdownlint        ← Vérifie syntaxe
3. Markdown PDF        ← Export PDF direct
4. Markdown Preview Enhanced ← Avancé
```

## 🚀 **INSTALLATION 30s**

``` text
Ctrl+Shift+X  → Tapez "Markdown All in One"
→ Install  → Reload
```

## 💻 **RACCOURCIS TP ESSENTIELS**

``` text
Ctrl+B     → **Gras**
Ctrl+I     → *Italique*
Ctrl+Shift+V → Preview ↔
Ctrl+K V   → Split view
Ctrl+Shift+P → "TOC: Create"
```
