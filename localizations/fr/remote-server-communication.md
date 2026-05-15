---
title: Communication avec un serveur distant
description: >-
  Envoyez et recevez des données textuelles personnalisées entre les clients
  FancyMenu et des serveurs externes.
---

# Communication avec un serveur distant

Le système de « Communication avec un serveur distant » permet aux clients FancyMenu de communiquer avec des serveurs externes via des connexions WebSocket.

Toutes les données sont basées sur du texte :

- Le texte brut est pris en charge
- Le JSON est pris en charge (en tant que texte normal)

Chaque URL de serveur reçoit un seul **ID de requête** mis en cache pendant l’exécution.
FancyMenu utilise cet ID pour suivre la connexion et l’exposer dans les variables des listeners.

# Démarrage rapide

1. Ajoutez l’action **Se connecter à un serveur distant** (facultatif, mais utile pour ouvrir la connexion tôt)
2. Ajoutez l’action **Envoyer des données au serveur distant** avec la même URL
3. Ajoutez le listener **À la réception de données du serveur distant** pour réagir aux réponses
4. Utilisez **Lors de la connexion au serveur distant** / **Lors de la fermeture de la connexion au serveur distant** pour la logique d’état de connexion
5. Fermez les connexions lorsque nécessaire avec les actions de fermeture

# Actions

## Se connecter à un serveur distant

Initialise une connexion à un serveur distant sans envoyer de données de charge utile.

Entrée :

- URL du serveur distant

## Envoyer des données au serveur distant

Se connecte (ou réutilise une connexion existante) et envoie des données textuelles.

Entrées :

1. URL du serveur distant
2. Données

## Fermer la connexion au serveur distant

Ferme une connexion à l’aide de l’ID de requête.

Entrée :

- ID de requête de la connexion

## Fermer toutes les connexions au serveur distant

Ferme toutes les connexions actives au serveur distant.

# Listeners

## Lors de la connexion au serveur distant

Déclenché lorsqu’une connexion à un serveur distant est initialisée.

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
- Lorsqu’une connexion en échec est restaurée, FancyMenu consigne un message de restauration
- Les messages sortants non envoyés sont mis en file d’attente avec une **durée de vie maximale de 30 secondes**
- Les messages en file d’attente datant de plus de 30 secondes sont abandonnés

# Modes d’URL

- `wss://` = sécurisé (TLS), recommandé
- `ws://` = non chiffré, utile pour les tests locaux

Exemple d’URL locale :

- `ws://127.0.0.1:8765`

# Bonnes pratiques

1. Utilisez une URL stable par service backend.
2. Conservez un format de charge utile cohérent pour chaque cas d’utilisation.
3. Gérez les connexions fermées ou en échec avec une logique d’interface de secours.
4. Utilisez les actions de fermeture lorsque votre flux est terminé.
5. Utilisez `wss://` pour les environnements de production.
