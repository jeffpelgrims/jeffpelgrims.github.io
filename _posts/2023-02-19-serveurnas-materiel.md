---
layout: post
title: "Mon projet de serveur NAS - Partie 2 : Le matériel"
date: 2023-02-19 04:40:00 +0100
categories: serveur
tags: serveur nas backup
---

Mise à jour 2024 : Finalement un NAS va arriver à la maison il s'agira du Synology DS1522+ dont une page sera crée pour le présenter.

## Configuration minimale requise pour TrueNas Scale

Voici ce que IX Systems préconise pour TrueNas Scale :

| Processeur                        | Mémoire   | Disque d'amorçage | Stockage                      |
| --------------------------------- | --------- | ----------------- | ----------------------------- |
| Processeur 64bits avec 2 coeurs   | 8 Go      | SSD de 16 Go      | Deux disques de même capacité |

Ils apportent quelques précisions :

- TrueNas ne nécessite pas réellement deux coeurs, néanmois les processeurs récent en ont tous au moins deux.
- Pour la mémoire il est bon de noter que :
  - Il faut ajouter 1 Go de mémoire par disque ajouté au delà de 8 disques
  - Si l'utilisation du protocol iSCSI est prévu ils recommandent 16 Go de mémoire minimum et 32 Go pour de meilleur performance
  - Il faut prendre en compte la quantité de mémoire minimum que les apps et VM vont utiliser
  - Bien que pas obligatoire, l'utilisation de mémoire ECC reste vivement conseillé

- Au niveau du processeur :
  - Un processeur moins puissant peut créer des soucis de performance à cause de comment OpenZFS réalise ses vérifications, compresse et (optionellement) crypte les données
  - Un processeur haute fréquence avec peu de coeurs performe mieux si vous utilisez seulement SMB grâce à Samba
  - Un processeur avec beaucoup de coeurs convient pour une utilisation de cryptage parallèle ou de la virtualisation
  - Un processeur "Serveur" est recommandé pour sa puissance et la compatibilité avec les RAM ECC
  - Un processeur Intel Ivy Bridge ou supérieur est recommandé pour de la virtualisation

## Ma configutation

| Processeur              | Mémoire           | Disque d'amorçage | Stockage                      | Cache       |
| ----------------------- | ----------------- | ----------------- | ----------------------------- | ----------- |
| Intel Xeon E5 2360 V4   | 2 x 16 Go ECC     | SSD de 120 Go     | 4x 4To HDD Western Digital    | NVME 256 Go |

### Le processeur

J'ai choisi de prendre une processeur Intel Xeon d'occasion. Ce processeur, sorti en 2016, sera tout à fait à l'aise pour faire tourner ce système.

En effet, les dix coeurs me permettent non seulement de le faire tourner en tant que NAS mais également d'y lancer quelques apps supplémentaires (comme une instance Next Cloud par exemple).

### La mémoire

Pour la mémoire j'ai choisi de prendre deux barettes de mémoire Kingston 16 Go ECC pour un total de 32 Go. La mémoire ECC me permet d'ajouter une couche de sécurité supplémentaire en cas de corruption de données suite à un incident (comme une coupure de courant par exemple).

### Les disques d'amorçage

Oui les disques en effet TrueNas sera installé sur deux SSD de 120 Go en mode mirroir. Toujours pour la sécurité si le premier tombe en panne, le second prend le relais.

### Le cache

Afin d'accélerer la lecture et l'écriture de données, un SSD NVMe de 256 Go sera utilisé comme mémoire tampon.

### Le stockage

Dans un premier temps, un pool ZFS de 4 disques de 4 To chacun sera crée. Il donnera un espace libre d'environ 12 To.

### Matériel divers

Le restant des composants :

- Une tour Antec P101 Silencio
- Une alimentation Corsair de 450W
- Un refroidisseur de processeur Noctua
- Une carte-mère X99
