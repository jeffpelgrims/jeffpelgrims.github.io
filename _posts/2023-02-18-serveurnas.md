---
layout: post
title: "Mon projet de serveur NAS - Partie 1 : La réflexion"
date: 2023-02-18 17:45:00 +0100
categories: serveur
tags: serveur nas backup
---

## Pourquoi un serveur NAS ?

A la maison, nous avons plusieurs besoins en terme d'utilisation de fichiers et de sauvegarde. A savoir la possibilité de sauvegarder nos machines, pouvoir sauvegarder des snapshots quotidien, nos documents et garder plusieurs versions de ces derniers, nos photos.

Mais également y avoir accès peux importe où nous nous trouvons.

## DIY ou solution "clé sur porte" ?

Effectivement deux choix s'offre à moi :

- Monter une machine
- Utiliser des solutions complète comme les NAS Synology

Le choix est vite fait, je suis un geek bidouilleur et c'est pour nos besoins perso et donc je vais monter une machine pour être utilisée en tant que Serveur NAS. (plus d'information sur la machine dans l'article "Hardware" de ce projet)

## Le logiciel

Pour le logiciel j'ai également plusieurs choix :

- True NAS Core
- True NAS Scale
- UnRaid
- Open Media Vault

### Open Media Vault

Pour le trouver : [Open Media Vault](https://www.openmediavault.org/)

Je ne le connais pas car je ne l'ai jamais employé ni même installé.

Difficile pour moi d'en parler...

Je vais le tester sur une machine virtuelle et voir ce qu'il a dans le ventre en attendant je ne vais pas l'utiliser pour le serveur.

### UnRaid

Pour le trouver : [UnRaid](https://unraid.net/)

J'ai utilisé UnRaid ces dernières année sur un vieux PC AMD. Je l'aime beaucoup mais le seul défaut c'est qu'il est payant.

Le version "Basic" à 59$ permet d'y mettre jusqu'à 6 disques (et dans le futur j'y serai vite...)

Il fait le taf, permet de créer des machines virtuelles et on peut y installer des plugin grâce à Docker.

Comme je veux quelque chose à moindre coup, je passe mon tour ^^

### TrueNas Core & TrueNas Scale

Pour les trouver : [TrueNas](https://www.truenas.com/)

La société IX Systems possède deux logiciels de sauvegarde libre et gratuit :

- TrueNas Core
- TrueNas Scale

Le premier est basé sur FreeBSD, ne demande pas beaucoup de ressource et fonctionne avec le système de fichiers ZFS.

Le second est basé sur Debian, demande un peu plus de ressource et fonctionne également avec le système de fichiers ZFS.

Je ne vais pas trop entrer dans les détails téchnique, je réserve cela à une autre partie de ce projet, la principal différence c'est que Scale, basé sur Debian, permet quelques petites chose en plus que Core, comme plus d'application ou encore la création de machines virtuelles.

Vous l'aurez compris, mon choix va vers TrueNas Scale.
Il est puissant et permettra de mettre en place tout ce dont j'ai besoin en terme de partage, sauvegarde et virtualisation.
