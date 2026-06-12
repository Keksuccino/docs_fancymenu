---
title: Entités Joueur
description: >-
  Comment fonctionne l'élément « Entité Joueur » de FancyMenu et comment
  l'utiliser correctement.
---
# Entités Joueur

FancyMenu vous permet d'ajouter des entités joueur aux écrans, afin d'afficher le joueur client ou d'autres joueurs, y compris des entités personnalisées qui ne représentent pas du tout un vrai joueur, avec une apparence, un nom, une cape, etc. personnalisés.

# Joueur client

Pour afficher un « miroir » du joueur client, faites simplement un clic droit sur l'élément Entité Joueur et ակտիվez **Copier le joueur client**. Cela copiera l'apparence, la cape et le nom du joueur client.

# Autres joueurs

Si vous souhaitez afficher un autre joueur existant, faites simplement un clic droit sur l'élément et définissez **Nom du joueur** sur le nom d'un joueur existant. Cela affichera automatiquement l'apparence, la cape et le nom de ce joueur existant, tant que vous n'avez pas défini d'apparence ou de cape personnalisée et que **Copier le joueur client** est **désactivé**.

# Entités joueur personnalisées

Si vous ne souhaitez pas afficher un vrai joueur et préférez personnaliser entièrement l'apparence, la cape et le nom de l'entité, vous pouvez faire un clic droit sur l'élément. Des options permettent de définir une texture d'apparence et de cape personnalisée. Si une apparence et une cape personnalisées sont actives, vous pouvez aussi définir n'importe quel nom de joueur sans que l'apparence du nom soit copiée si le joueur existe.

# Pose de l'entité

L'élément Entité Joueur prend entièrement en charge la personnalisation de sa pose ; autrement dit, vous pouvez déplacer librement tous ses membres, parties du corps, etc.

Pour cela, faites un clic droit sur l'élément puis cliquez sur **Pose du joueur**. Cela ouvrira un écran avec des curseurs pour configurer la rotation X/Y/Z de toutes les parties du corps.

Les paramètres de pose du joueur disposent d'un mode normal où vous pouvez personnaliser les rotations avec des curseurs, ainsi que d'un mode avancé qui permet une saisie texte pour toutes les rotations avec prise en charge complète des espaces réservés, ce qui permet même d'animer l'entité avec un élément Ticker qui définit des variables de rotation !

# Modifier la taille de l'entité

Dans Minecraft 1.20.1+, vous pouvez simplement utiliser les poignées de redimensionnement normales de l'élément pour mettre l'entité à l'échelle.

Pour les versions plus anciennes (1.19.2 et antérieures), les éléments Entité Joueur ne prennent pas en charge le redimensionnement direct via les poignées de redimensionnement. À la place, vous devez faire un clic droit sur l'élément puis cliquer sur **Échelle**. Cela vous permet de définir une échelle pour l'élément. La valeur par défaut devrait être `30`, donc la régler à `60`, par exemple, rend le joueur deux fois plus grand que la normale, la régler à `15` l'affiche à moitié de sa taille, et ainsi de suite.

# Dépendance : Fancy Entity Renderer (FER)

Pour **Minecraft 1.20.1+**, un **mod supplémentaire est nécessaire** pour faire fonctionner les éléments Entité Joueur. Ce mod s'appelle **Fancy Entity Renderer** et est disponible sur [CurseForge](https://www.curseforge.com/minecraft/mc-mods/fancy-entity-renderer) et [Modrinth](https://modrinth.com/mod/fancy-entity-renderer).

S'il n'existe pas encore de version disponible pour la version de Minecraft que vous utilisez, elle sera très probablement publiée ultérieurement.

Veuillez garder à l'esprit que FER n'est pas développé par Keksuccino, il n'a donc aucun contrôle sur le moment où les versions sont publiées.
