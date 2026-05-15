---
title: Entités Joueur
description: >-
  Comment fonctionne l’élément « Entité Joueur » de FancyMenu et comment
  l’utiliser correctement.
---

# Entités Joueur

FancyMenu vous permet d’ajouter des entités de joueur aux écrans, afin d’afficher le joueur du client ou d’autres joueurs, y compris des entités personnalisées qui ne représentent aucun joueur réel, avec une skin, un nom, une cape, etc. personnalisés.

# Joueur du client

Pour afficher un « miroir » du joueur du client, faites simplement un clic droit sur l’élément Entité Joueur et सक्रियez **Copier le joueur du client**. Cela copiera la skin, la cape et le nom du joueur du client.

# Autres joueurs

Si vous souhaitez afficher un autre joueur existant, faites simplement un clic droit sur l’élément et définissez **Nom du joueur** sur le nom d’un joueur existant. Cela affichera automatiquement la skin, la cape et le nom de ce joueur existant, tant que vous n’avez pas défini de skin ou de cape personnalisé et que **Copier le joueur du client** est **désactivé**.

# Entités joueur personnalisées

Si vous ne souhaitez pas afficher un vrai joueur et préférez personnaliser entièrement la skin, la cape et le nom de l’entité, vous pouvez faire un clic droit sur l’élément. Des options permettent de définir une skin et une texture de cape personnalisées. Si une skin et une cape personnalisées sont actives, vous pouvez aussi définir n’importe quel nom de joueur sans que la skin de ce nom soit copiée si le joueur existe.

# Pose de l’entité

L’élément Entité Joueur prend entièrement en charge la personnalisation de sa pose ; autrement dit, vous pouvez déplacer librement tous ses membres, parties du corps, etc.

Pour cela, faites un clic droit sur l’élément et cliquez sur **Pose du joueur**. Cela ouvrira un écran avec des curseurs permettant de configurer la rotation X/Y/Z de toutes les parties du corps.

Les paramètres de pose du joueur proposent un mode normal où vous pouvez personnaliser les rotations avec des curseurs, ainsi qu’un mode avancé qui permet une saisie de texte pour toutes les rotations avec prise en charge complète des placeholders, ce qui rend même possible d’animer l’entité avec un élément Ticker qui définit des variables de rotation !

# Changer la taille de l’entité

Dans Minecraft 1.21.1+, vous pouvez simplement utiliser les poignées de redimensionnement normales de l’élément pour mettre l’entité à l’échelle.

Pour les versions plus anciennes (1.21.0 et antérieures), les éléments Entité Joueur ne prennent pas en charge le redimensionnement direct via les poignées de redimensionnement. À la place, vous devez faire un clic droit sur l’élément et cliquer sur **Échelle**. Cela vous permet de définir une échelle pour l’élément. La valeur par défaut devrait être `30`, donc la régler à `60`, par exemple, rend le joueur deux fois plus grand que la normale, la régler à `15` l’affiche à moitié de sa taille, et ainsi de suite.

# Dépendance : Fancy Entity Renderer (FER)

Pour Minecraft 1.21.1+, un mod supplémentaire est nécessaire pour faire fonctionner les éléments Entité Joueur. Ce mod s’appelle « Fancy Entity Renderer » et est disponible sur CurseForge et Modrinth.

Si aucune version n’est encore disponible pour la version de Minecraft que vous utilisez, elle sera très probablement publiée plus tard.

Veuillez garder à l’esprit que FER n’est pas विकसितé par Keksuccino, donc il n’a aucun contrôle sur le moment où les versions sont publiées.
