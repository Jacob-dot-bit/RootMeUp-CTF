# 🚩 RootMeUp — Plateforme CTF

Bienvenue sur **RootMeUp**, une plateforme de challenges de cybersécurité (Capture The Flag)
mêlant **Blue Team** (défense, forensics, analyse) et **Red Team** (attaque, exploitation).
Chaque challenge se joue dans un environnement isolé, dédié à votre équipe.

Ce dépôt contient uniquement les **guides joueur**. Pas de solutions, pas d'indices avancés :
tout se joue sur la plateforme.

---

## 1. Accéder à la plateforme

La plateforme n'est **pas exposée sur Internet** : on y accède via un réseau privé **Tailscale**.

1. **Installer Tailscale** : https://tailscale.com/download (Windows, macOS, Linux, mobile).
2. **Rejoindre le réseau** du CTF via le **lien d'invitation** fourni par l'équipe organisatrice
   *(le lien vous est communiqué séparément — il n'est pas publié ici)*.
3. Une fois connecté à Tailscale, ouvrir la plateforme **CTFd** dans un navigateur
   (accès en **HTTPS**) :

   ```
   https://ctf-rootmeup.tail8588a8.ts.net/
   ```

## 2. Créer un compte & une équipe

1. Sur CTFd, cliquer **Sign Up** et créer votre compte (nom, email, mot de passe).
2. Rejoindre ou **créer une équipe** (jusqu'à 3 participants).
3. Vous êtes prêt à jouer.

## 3. Jouer un challenge

1. Ouvrir la liste des **Challenges**.
2. Choisir un challenge et lire son énoncé.
3. Pour les challenges avec instance : cliquer **Start Instance** → un environnement dédié
   à votre équipe démarre (une **IP** et un **port** vous sont donnés).
4. Résoudre le challenge (voir le guide de chaque challenge dans `challenges/`).
5. Soumettre le **flag** trouvé dans CTFd. Les flags sont **sensibles à la casse**.

> ℹ️ Un flag ressemble à `RM{...}`, `blue{...}`, `MERIDIAN{...}` ou `FLAG{...}` selon le challenge.

---

## 4. Les challenges

| Équipe | Challenge | Thème | Guide |
|---|---|---|---|
| 🔵 Blue 1 | Phishing sur corp.local | Forensics — analyse de logs (ELK/Kibana) | [`GUIDE`](challenges/Blue-1-Phishing-corp-local/GUIDE.md) |
| 🔵 Blue 2 | Mémoire & analyse de malware | Forensics — dump mémoire | [`GUIDE`](challenges/Blue-2-Memoire-Forensics/GUIDE.md) |
| 🔵 Blue 3 | Hardening | Durcissement système | [`GUIDE`](challenges/Blue-3-Hardening/GUIDE.md) |
| 🔴 Red 1 | VAULT-9 | Reverse & exploitation binaire | [`GUIDE`](challenges/Red-1-VAULT-9/GUIDE.md) |
| 🔴 Red 2 | Opération Silent Ledger | Machine Linux compromise (escalade) | [`GUIDE`](challenges/Red-2-Silent-Ledger/GUIDE.md) |
| 🔴 Red 3 | Nexus Cipher | Pentest d'une API (crypto/web) | [`GUIDE`](challenges/Red-3-Nexus-Cipher/GUIDE.md) |
| 🔴 Red 4 | Breach & Ascend | Intrusion web puis élévation → root | [`GUIDE`](challenges/Red-4-Breach-and-Ascend/GUIDE.md) |

---

## 5. Règles & bonnes pratiques

- Jouez uniquement sur **vos** instances ; n'attaquez pas la plateforme elle-même ni les
  instances des autres équipes.
- Ne partagez pas les flags entre équipes.
- Une instance a une durée de vie limitée : relancez-la si elle expire.
- Amusez-vous et apprenez ! 🎯

*Bon CTF.*
