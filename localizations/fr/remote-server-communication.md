---
title: Communication avec un serveur distant
description: >-
  Envoyez et recevez des données textuelles personnalisées entre les clients
  FancyMenu et des serveurs externes.
---

# Communication avec un serveur distant

Le système de « Communication avec un serveur distant » permet aux clients FancyMenu de communiquer avec des serveurs externes à l’aide de connexions WebSocket.

Toutes les données sont basées sur du texte :

- Le texte brut est pris en charge
- JSON est pris en charge (en tant que texte normal)

Chaque URL de serveur reçoit un seul **ID de requête** mis en cache pendant l’exécution.
FancyMenu utilise cet ID pour suivre la connexion et l’exposer dans les variables des écouteurs.

# Démarrage rapide

1. Ajoutez [**Se connecter au serveur distant**](#se-connecter-au-serveur-distant) lorsque la connexion doit s’ouvrir tôt.
2. Ajoutez [**Envoyer des données au serveur distant**](#envoyer-des-donnees-au-serveur-distant) avec la même URL.
3. Ajoutez [**À la réception de données du serveur distant**](#a-la-reception-de-donnees-du-serveur-distant) pour réagir aux réponses.
4. Utilisez [**Lors de la connexion au serveur distant**](#lors-de-la-connexion-au-serveur-distant) et [**Lors de la fermeture de la connexion au serveur distant**](#lors-de-la-fermeture-de-la-connexion-au-serveur-distant) pour la logique d’état de connexion.
5. Fermez les connexions avec [**Fermer la connexion au serveur distant**](#fermer-la-connexion-au-serveur-distant) ou [**Fermer toutes les connexions au serveur distant**](#fermer-toutes-les-connexions-au-serveur-distant).

# Actions

## Se connecter au serveur distant

Ouvre ou réutilise une connexion à un serveur distant sans envoyer de données utiles.

Entrée :

- URL du serveur distant

## Envoyer des données au serveur distant

Se connecte (ou réutilise une connexion existante) et envoie des données textuelles.

Entrées :

1. URL du serveur distant
2. Données

## Fermer la connexion au serveur distant

Ferme une connexion à partir de son ID de requête.

Entrée :

- ID de requête de connexion

## Fermer toutes les connexions au serveur distant

Ferme toutes les connexions au serveur distant actuellement actives.

# Écouteurs

## Lors de la connexion au serveur distant

Déclenché après l’ouverture réussie d’une connexion à un serveur distant.

Variables :

- `$$request_id`
- `$$remote_server_url`

## À la réception de données du serveur distant

Déclenché lorsque des données sont reçues d’un serveur distant connecté.

Variables :

- `$$request_id`
- `$$remote_server_url`
- `$$data`

## Lors de la fermeture de la connexion au serveur distant

Déclenché lorsqu’une connexion à un serveur distant se ferme.

Variables :

- `$$request_id`
- `$$remote_server_url`
- `$$intentionally_closed`
- `$$crashed`
- `$$unknown_close_reason`

# Comportement de la connexion

- Les connexions sont **initiées par le client**
- FancyMenu maintient les connexions actives en arrière-plan
- Si une connexion plante ou expire, FancyMenu réessaie toutes les 10 secondes
- Lorsqu’une connexion plantée est restaurée, FancyMenu enregistre un message de restauration
- Les messages sortants non envoyés sont mis en file d’attente avec une **durée de vie maximale de 30 secondes**
- Les messages en file d’attente âgés de plus de 30 secondes sont supprimés

# Modes d’URL

- `wss://` est utilisé tel quel et est recommandé.
- `ws://` est utilisé tel quel et n’est pas chiffré.
- `https://` est converti en `wss://`.
- `http://` est converti en `ws://`.
- Un hôte seul est préfixé par `wss://`.
- Les autres schémas d’URL explicites sont rejetés.

Privilégiez des URL explicites en `wss://`. Exemple d’URL locale :

- `ws://127.0.0.1:8765`

Utilisez une URL stable par service, gérez les états d’écouteur fermé/planté et fermez les connexions lorsqu’elles ne sont plus nécessaires.
