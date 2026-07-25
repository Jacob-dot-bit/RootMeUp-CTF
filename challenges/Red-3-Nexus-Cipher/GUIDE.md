# 🔴 Nexus Cipher — Guide du joueur

**Catégorie :** Red Team — Pentest d'API (web / crypto)
**Difficulté :** Intermédiaire → avancé
**Flags :** 10 (progressifs)

## 📖 Contexte

**Nexus** est un portail d'API interne d'une entreprise fictive. Il expose plusieurs
endpoints (authentification, gestion de ressources, échanges chiffrés) développés
« maison », avec les mauvaises habitudes que ça implique : secrets mal protégés,
contrôle d'accès approximatif et **cryptographie faite maison**.

Votre mission : auditer l'API de bout en bout et récupérer les **10 flags** en
exploitant sa logique, ses failles d'accès et ses faiblesses cryptographiques.

## 🎯 Objectifs

- **10 flags progressifs**, du recon initial de l'API jusqu'à la compromission des
  données chiffrées. Chaque flag rapporte des points croissants — soumettez-les au
  fur et à mesure dans CTFd, sans attendre la fin.
- Le **brief détaillé de chaque étape** est disponible sur la page du challenge dans CTFd.

Format des flags : `FLAG{...}` (sensible à la casse).

## 🔌 Accès

1. Démarrer l'instance (**Start Instance**) : une **IP** et un **port** vous sont donnés.
2. L'API se consomme en **HTTP** :

   ```bash
   curl -i http://<ip>:<port>/
   ```

3. Explorez les endpoints exposés à partir de la racine et de la documentation
   éventuelle de l'API.

## 🧰 Outils suggérés

- **Exploration d'API** : `curl`, **Postman**/**Insomnia**, **Burp Suite** (proxy + Repeater).
- **Fuzzing d'endpoints** : `ffuf`, `gobuster` (mode `dir`), wordlists d'API.
- **Crypto** : **CyberChef**, Python (`pycryptodome`, `hashlib`), analyse d'encodages
  (base64/hex) et de schémas de chiffrement/signature.
- **Manipulation de jetons** : décodeur JWT, éditeur de cookies/headers.

## 🪜 Pistes (sans spoiler)

- **Recon** : cartographiez les endpoints et les **méthodes HTTP** acceptées. Que
  renvoient les réponses d'erreur ? Y a-t-il une doc, un `/version`, un `/debug` ?
- **Contrôle d'accès** : comparez ce qu'un utilisateur anonyme voit vs authentifié.
  Certains objets/ressources sont-ils accessibles en changeant simplement un
  **identifiant** dans la requête ?
- **Authentification** : observez la forme des **jetons** (structure, encodage,
  signature). Que se passe-t-il si vous les modifiez ?
- **Crypto maison** : quand une valeur est chiffrée/signée, cherchez la **faiblesse du
  schéma** (clé courte/devinable, encodage confondu avec du chiffrement, réutilisation,
  absence d'intégrité) plutôt que d'attaquer l'algorithme lui-même.

## ✅ Validation

Soumettez chaque flag dans CTFd dès que vous le trouvez. Les 10 étapes se jouent sur
**la même instance**.

Bonne chasse — *un cadenas fait maison n'est pas un cadenas.* 🔐
