# 🔴 Breach & Ascend — Guide du joueur

**Catégorie :** Red Team — Web → élévation de privilèges
**Difficulté :** Intermédiaire
**Flags :** 3 (progressifs)

## 📖 Contexte

Une application web d'entreprise (fictive) est exposée. Elle propose notamment une
fonctionnalité d'**upload de fichiers**. Votre mission : prendre pied sur le serveur
via l'application, puis **remonter les privilèges** étape par étape jusqu'à `root`.

## 🎯 Objectifs

| # | Flag | Étape | Points |
|---|------|-------|-------:|
| 1 | **Breach** | Compromettre l'application web et obtenir un premier accès sur le serveur | 100 |
| 2 | **Pivot vers user** | Passer de l'accès web à un véritable compte utilisateur | 50 |
| 3 | **Root** | Élever vos privilèges jusqu'à `root` | 200 |

Soumettez chaque flag dans CTFd au fur et à mesure — tout se joue sur la **même instance**.

## 🔌 Accès

1. Démarrer l'instance (**Start Instance**) : une **IP** et un **port** vous sont donnés.
2. L'application est un service **web (HTTP)** — ouvrez-la dans un navigateur :

   ```
   http://<ip>:<port>/
   ```

## 🧰 Outils suggérés

- **Web** : navigateur + **Burp Suite** (ou proxy équivalent), `curl`, `ffuf`/`gobuster`
  pour l'énumération de contenu.
- **Post-exploitation** : un **reverse shell** (netcat / `bash -i`), stabilisation de TTY.
- **Élévation de privilèges** : **LinPEAS** / `linenum.sh`, `sudo -l`, recherche de
  binaires SUID, tâches planifiées, fichiers de config lisibles.

## 🪜 Pistes (sans spoiler)

- **Flag 1 — Breach** : regardez de près la fonction d'**upload**. Quels types de
  fichiers sont réellement acceptés ? Où les fichiers atterrissent-ils, et sont-ils
  **exécutables** par le serveur web ? Un contrôle côté client n'est pas un contrôle.
- **Flag 2 — Pivot vers user** : depuis l'accès obtenu par le web (souvent limité),
  cherchez ce qui traîne sur le système — **fichiers de configuration**, identifiants
  en dur, historiques, répertoires personnels — pour basculer sur un vrai compte utilisateur.
- **Flag 3 — Root** : une fois utilisateur, énumérez méthodiquement les vecteurs
  d'escalade classiques (`sudo -l`, SUID, cron, capabilities, services mal configurés).

## ✅ Validation

Trois flags, trois paliers. Soumettez-les dans CTFd dès que vous les obtenez.

Bonne ascension — *du navigateur à `root`.* ⛰️
