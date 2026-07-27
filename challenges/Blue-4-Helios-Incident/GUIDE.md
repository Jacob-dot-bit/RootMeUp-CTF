# 🔵 Helios Incident — Guide du joueur

**Catégorie :** Blue Team — Forensic réseau (analyse de capture)
**Difficulté :** Intermédiaire
**Flags :** série progressive

## 📖 Contexte

Le **serveur web interne d'Helios Corp** a été compromis. L'équipe réseau a réussi à
capturer le trafic **pendant l'incident**. À vous d'analyser cette capture (`.pcap`) pour
**reconstituer la chaîne d'attaque**, de l'intrusion initiale jusqu'à l'exfiltration des
données.

## 🎯 Objectifs

Reconstituer l'incident étape par étape (chaque étape = un flag) :
1. **Intrusion** — comment l'attaquant a obtenu l'exécution de code sur le serveur web.
2. **Prise de contrôle** — l'outil/fichier laissé sur le serveur et son utilisation.
3. **Command & Control** — la communication avec l'infrastructure de l'attaquant.
4. **Exfiltration** — comment les données sont sorties du réseau.

> Le **format exact des flags** et les questions précises sont indiqués sur la **page du
> challenge dans CTFd**.

## 🔌 Accès

**Téléchargez le fichier `capture.pcap`** fourni sur la page du challenge dans CTFd, puis
analysez-le **en local** avec vos outils.

## 🧰 Outils suggérés

- **Analyse de capture** : **Wireshark** (GUI) ou **`tshark`** (CLI), **NetworkMiner**.
- **Vue d'ensemble** : dans Wireshark → *Statistics → Protocol Hierarchy*, *Conversations*,
  et *Statistics → DNS* ; ou `tshark -q -z io,phs -r capture.pcap`.
- **Reconstruction de flux** : *Follow → HTTP/TCP Stream* (clic droit sur un paquet).
- **Décodage** : **CyberChef** (base64/base32/hex) pour d'éventuelles données encodées.

## 🪜 Pistes (sans spoiler)

- **Intrusion web** : concentrez-vous sur le trafic **HTTP** vers le serveur web. Quelles
  requêtes sortent de l'ordinaire ? Une fonctionnalité de l'application a-t-elle servi à
  **déposer un fichier** ? Que se passe-t-il ensuite avec ce fichier ?
- **Exécution de commandes** : après le dépôt, cherchez des requêtes qui **passent des
  commandes** au serveur (paramètres d'URL, réponses inhabituelles).
- **C2** : y a-t-il du trafic **sortant** vers un hôte externe qui n'a rien à faire là ?
  Regardez les domaines contactés et les IP publiques.
- **Exfiltration** : les requêtes **DNS** sont-elles toutes normales ? Des **sous-domaines
  longs / encodés** répétés vers un même domaine sont un grand classique d'exfiltration.
  Que contiennent-ils une fois décodés ?

## ✅ Validation

Soumettez chaque flag dans CTFd au fur et à mesure de votre reconstitution de l'incident.

Bonne analyse — *tout est dans les paquets.* 🔎
