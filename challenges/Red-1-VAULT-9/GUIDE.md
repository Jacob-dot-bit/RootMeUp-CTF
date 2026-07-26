# 🔴 VAULT-9 — Guide du joueur

**Catégorie :** Red Team — Reverse & Exploitation binaire
**Difficulté :** Intermédiaire
**Flags :** 2 (progressifs)

## 📖 Contexte

L'entreprise **Meridian Corp** protège son module mémoire sensible derrière une console d'administration maison, `VAULT-9`. Un binaire de cette console a fuité. Votre équipe doit démontrer qu'il est vulnérable : contourner sa licence, puis en prendre le contrôle pour ouvrir le coffre.

## 🎯 Objectifs

1. **Flag 1** — Contourner la vérification de licence du binaire.
2. **Flag 2** — Prendre le contrôle de l'exécution pour atteindre la routine qui ouvre le coffre.

Format des flags : `RM{...}` (sensible à la casse).

## 🔌 Accès

**Environnement fourni — rien à installer chez vous.**

1. Démarrez l'instance (**Start Instance**) : vous obtenez une **IP** et un **port SSH**.
2. Connectez-vous à la boîte d'attaque :

   ```bash
   ssh hacker@<ip> -p <port>      # mot de passe : vault9
   ```

3. Tout est déjà dans la boîte :
   - le **binaire à analyser** : `~/vault`
   - le **service vulnérable**, en écoute locale : `nc localhost 9003` (exécute le même binaire)
   - les **outils** préinstallés (voir ci-dessous)

> Vous **ne pouvez pas lire les flags directement** (ils appartiennent au service, pas à
> votre compte) : vous devez **exploiter** `localhost:9003` pour qu'il vous les révèle.

## 🧰 Outils (déjà installés dans la boîte)

- **Reverse** : `objdump -d ~/vault`, `gdb`, `file ~/vault`, `strings ~/vault`.
- **Exploitation** : `python3` + **pwntools** (`from pwn import *`), `nc`.
- **Info binaire** : `python3 -c "from pwn import *; print(ELF('vault'))"` (équivalent `checksec`).

> Vous pouvez aussi **télécharger le binaire `vault`** depuis CTFd pour l'analyser sous
> Ghidra / IDA en local si vous préférez une interface graphique.

## 🪜 Pistes (sans spoiler)

- **Étape 1** : regardez la fonction qui valide la licence. Quelle **opération** est appliquée
  à votre saisie avant la comparaison ? La donnée de référence est présente dans le binaire…
  mais transformée.
- **Étape 2** : une fois « administrateur », le terminal de maintenance lit votre entrée.
  Combien d'octets accepte-t-il réellement vs la taille du tampon ? Existe-t-il une fonction
  **intéressante jamais appelée** ?

## ✅ Validation

Exploitez le service `localhost:9003` depuis la boîte. Le **flag 1** apparaît dès l'accès
administrateur ; le **flag 2** nécessite de détourner l'exécution. Soumettez chaque flag dans CTFd.

Bon courage — et n'oubliez pas : *ne codez jamais un secret en dur.* 😉
