+++
title = "Ouvrir ports et obtenir une IP statique en 4G (avec OpenMPTCProuter)"
date = '2019-10-23T00:00:00+02:00'
draft = false

categories = ['Sysadm']
description = "Obtenir une IP statique sur une connexion 4G (et donc derrière un CGNAT) n'est pas chose facile. Voyons comment faire."

[[variables]]
name = "vps_ip"
label = "IP de votre VPS"
default = "1.1.1.1"
validation = "text"

[[variables]]
name = "box_ip"
label = "IP de votre box 4G"
default = "192.168.1.1"
validation = "text"
+++

Ce tutoriel devrait vous permettre soit

- D'ouvrir vos ports en 4G et d'obtenir une IP statique par la meme occasion
- Et possiblement de fusionner des connexions afin d'en sommer la vitesse

Pour cela, nous allons utiliser l'excellent OpenMPTCProuter.

Il est indispensable pour ce tutoriel de disposer d'un VPS sous Debian 12.

> [!TIP] Ne pas payer trop cher
> N'importe quel VPS fera l'affaire. Votre bande passante est généralement limitée par votre connexion 4G,
> pas par le VPS.
> Un VPS à 2€/mois suffira largement.

Il vous faudra aussi disposer de

- Un Raspberry Pi (2B ou plus récent - Testé avec un 4)
- Une carte micro SD (1Go ou plus), et son lecteur pour le brancher à votre ordinateur.
- [Balena Etcher](https://www.balena.io/etcher/) pour graver les images sur la carte SD
- Une Box internet et/ou un routeur 4G

{{< variables-form >}}

Commencer par commander votre VPS. Une fois livré, utilisez votre client SSH préféré pour vous connecter dans le
serveur :

```bash
ssh {{< variable "vps_ip" >}} "apt-get update && apt-get upgrade -y && wget -O - https://www.openmptcprouter.com/server/debian-x86_64.sh | KERNEL="6.6" sh"
```

Ça devrait tourner pendant une petite dizaine de minutes.
Pendant ce temps, téléchargez [ici](https://www.openmptcprouter.com/download) l'image correspondant à votre PI.
Choisissez une image factory en ext4 64 bits.

Utilisez Etcher pour graver l'image sur la carte micro SD.

> [!WARNING] Attention !
> Il est possible que les étapes suivantes coupent votre connexion internet.
> Pensez à télécharger les élèments dont vous auriez besoin, tels que le manuel de votre routeur.
> Vérifiez aussi que la commande SSH s'est bien terminée sur le serveur, et sauvegardez la clé affichée.


À l'aide de votre ordinateur, connectez-vous à votre box/routeur 4G. Prenez note de son adresse IP locale, et vérifiez
qu'elle n'est pas en `192.168.100.X`. Si c'est le cas, changez le 100 en 1.

Désactivez le serveur DHCP de votre box, puis redémarrez.

Connectez votre RPI à la box, branchez la carte micro SD et l'alimentation, démarrez-le.

Branchez votre ordinateur ou connectez-le de nouveau au WiFi. Normalement, il devrait récupérer une IP locale en
`192.168.100.XXX`.

Connectez-vous sur le [panneau d'administration de OpenMPTCProuter](http://192.168.100.1/).

Dans l'onglet Système, ouvrez l'assistant de configuration, et placez-y la clé de configuration qui a été affichée à la
fin de l'execution de la commande SSH.
Placez-y aussi l'IP de votre VPS, {{< variable "vps_ip" >}}, et configurez l'IP de votre
box/routeur 4G {{< variable "box_ip" >}}

C'est fini ! Redémarrez vos appareils et ils devraient automatiquement utiliser la nouvelle connexion et obtenir une IP
locale en `192.168.100.XXX`.

Pour l'ouverture de ports, rendez-vous dans les paramètres réseau de OpenMPTCProuter ! [^1]

[^1]: Ou consultez la doc ;) — https://github.com/Ysurac/openmptcprouter/wiki/Port-forwarding