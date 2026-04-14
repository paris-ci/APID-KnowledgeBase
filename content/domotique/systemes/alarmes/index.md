+++
date = '2026-04-13T15:57:00+02:00'
draft = false
title = 'Alarmes'
categories = ['Domotique']
description = "Un système d'alame parfait, sans abonnement, et qui préviens en amont des intrusions !"
+++

Un système d'alarme se conçoit en trois couches très complémentaires :

- L'extérieur du logement, avec des détecteurs de mouvement ou des caméras afin d'identifier un intrus AVANT qu'il pénètre ou n'abime une porte/fenetre.
- Des capteurs d'ouverture de porte/fenetre, qui permettent de détecter une intrusion dès que celle-ci se produit. Ils permettent aussi de se rassurer : "Est-ce que j'ai bien fermé la fenêtre de la chambre ?"
- L'intérieur (vérifier que personne n'est présent dans la maison, qu'il n'y a pas de fuite ou de problème si un autre capteur est déclenché)

Pour couvrir ces zones, on utilise généralement un mix de caméras, de détecteurs de mouvement, de capteurs d'ouverture de porte/fenetre,
de radars micro-ondes (pour détecter la présence), capteurs de vibrations et détecteurs de fuites (utiles aussi pour éviter la machine à laver qui fuit!).

# Extérieur

Pour l'extérieur, on recherche des caméras de surveillance qui 

1) Sont capables de détecter les personnes, et de faire la différence entre une personne, un animal, ou une voiture.
2) Sont cablées en Ethernet (pas de WiFi, qui peut être brouillé et qui capte mal à travers les murs)
3) Sont waterproof, infrarouges et (ou) munies d'un spot puissant.

> [!TIP] N'achetez pas n'importe quelle caméra
> La capacité de votre caméra à fonctionner sans internet, en local, avec un système de détection de personnes fiable,
> est plus importante que la qualité de l'image ou les fonctionnalités supplémentaires.
> Les caméras bon marché peuvent avoir une qualité d'image qui ne permet pas de distinguer le 
> type de mouvement amenant soit à manquer une notification utile, soit à être spammé de notifications inutiles
> (par exemple : un arbre qui bouge, un chat qui passe, etc.)
> 
> Ainsi, je conseille d'éviter les caméras solaires, ou les caméras WiFi, 
> qui sont souvent de moins bonne qualité que les caméras Ethernet filaires, et plus fiables à contourner.
> 
> Petit point vie privée également, essayez de choisir des caméras qui permettent un blackout total quand vous le souhaitez/automatiquement,
> et qui ne sont pas connectées à des serveurs tiers (ex: cloud du fabricant).

Pour cela, il existe deux possibilitiés, dépendant du nombre de caméras que vous souhaitez installer (et du prix que vous êtes prêts à payer) :

{{< columns >}}
{{< column >}}
## Caméras avec IA embarquée

Idéal si vous voulez une installation simple, avec peu de caméras, et une détection directement dans la caméra.

- La caméra analyse elle-même le flux vidéo.
- Mise en place généralement plus simple.
- Moins de matériel à maintenir.
- Bien adapté pour 1 à 3 caméras.
- Les caméras haut de gammes équipées de ce système sont plus chères que des caméras classiques.
- Les caméras "Unifi Protect" sont un bon exemple de ce type de caméras, avec une bonne intégration [Home Assistant](/domotique/installer-homeassistant/), et une détection de personnes/animaux/voitures fiable.
- Pas (forcément) besoin d'un serveur local dédié, ni de matériel d'accélération IA.

Le revers de la médaille est que vous dépendez davantage des capacités du fabricant : types d'objets reconnus, qualité des notifications,
intégration domotique, confidentialité et possibilité de tout faire fonctionner sans cloud.
{{< /column >}}
{{< column >}}
## Frigate NVR

[`Frigate`](https://frigate.video/) est une approche plus centralisée : les caméras envoient leur flux vidéo vers un NVR local (serveur vidéo)
qui se charge de la détection, des enregistrements et des automatisations.

- Détection homogène sur toutes les caméras.
- Excellent choix si vous avez plusieurs flux à gérer.
- Intégration locale très solide avec [Home Assistant](/domotique/installer-homeassistant/).
- Plus flexible pour filtrer les faux positifs et construire des scénarios avancés.
- **Permet d'acheter des caméras moins chères, par exemple chez Dahua (marque prisée des installateurs professionnels) !**
- Nécessite d'acheter un serveur local (ou d'utiliser un vieux PC), et idéalement un accélérateur IA compatible (ex: Coral USB) pour de bonnes performances.

{{< /column >}}
{{< /columns >}}

Personnellement, pour deux caméras, qui surveillent un jardin et des portes fenêtres, je suis parti sur un système Unifi Protect :

- Bonne qualité d'image
- Fonctionne en local avec le serveur [Home Assistant](/domotique/installer-homeassistant/) et la box UniFi Protect, sans cloud (et donc sans risque de coupure de service, de piratage, ou de problème de confidentialité)
- Un seul cable à faire passer dans le mur (Ethernet, qui alimente aussi la caméra en *PoE*)
- Un paiement unique, sans abonnement (contrairement à d'autres marques qui font payer un abonnement pour accéder aux fonctionnalités de détection avancées)
- Les caméras sont automatiquement éteintes lorsque je suis à la maison, et s'allument dès que je pars, pour respecter ma vie privée.

{{% details title="Exemple de vue depuis une caméra" closed="true" %}}

Voici le type de vue que l'on obtient avec une caméra correctement placée pour surveiller le jardin (la caméra détecte le chat 😁) :

![Vue depuis ma caméra Unifi Protect](image_camera_unifi.jpg)
{{% /details %}}

En plus des caméras, il est aussi possible d'installer des détecteurs de mouvement [ZigBee](/domotique/zigbee/), extérieurs. 
Je ne l'ai pas fait, mais celui de Philips Hue est recommandé.

Ils se connectent à un [réseau ZigBee](/domotique/zigbee/) existant, en passant par des prises de courant connectées par exemple. 

## Périmètre (portes/fenêtres)

En parlant de [ZigBee](/domotique/zigbee/), les détecteurs d'ouverture de portes et fenêtres sont à piles, peu chers et faciles à installer,
et sont un excellent complément aux caméras pour détecter une intrusion dès qu'elle se produit.

Il suffit de placer des petits capteurs autocollants sur chaque porte et fenêtre, et de les connecter à votre [réseau ZigBee](/domotique/zigbee/).

Sur [Home Assistant](/domotique/installer-homeassistant/), vous pouvez alors créer des automatisations pour recevoir une notification dès qu'une porte ou une fenêtre est ouverte, ou pour déclencher une alarme sonore si vous n'êtes pas à la maison.

{{< cards cols="2" >}}
{{< card
link="https://fr.aliexpress.com/item/1005006508846585.html"
image="aqara-door-sensor.png"
options="800x800 q100"
method="Fill"
title="Aqara Capteur Porte/Fenêtre"
subtitle="Capteur d'ouverture Zigbee, détecte l'état porte/fenêtre en temps réel. À piles, discret, autocollant. Compatible Home Assistant via Zigbee2MQTT."
tag="~8 €"
tagType="info" >}}
{{< card
link="https://fr.aliexpress.com/item/1005009740967694.html"
image="tuya-sirene-zigbee.png"
options="800x800 q100"
method="Fill"
title="Tuya Sirène Zigbee 3-en-1"
subtitle="Sirène d'alarme Zigbee 90dB avec capteurs de lumière et de son intégrés. Idéale pour déclencher une alerte sonore en cas d'intrusion détectée."
tag="~18 €"
tagType="warning" >}}
{{< /cards >}}

L'avantage, c'est que ces capteurs sont fiables et peu chèrs. Ils peuvent même être une bonne alternative pour éviter 
d'installer des caméras dans les pièces intérieures, si vous ne souhaitez pas surveiller en permanence l'intérieur de 
votre maison, mais simplement être alerté en cas d'intrusion.

Attention cependant, sans moyen de confirmer les alertes, il y a un petit risque de faux positifs.

Il existe aussi des capteurs de vibrations, qui peuvent être placés sur les portes ou les fenêtres,
et qui permettent de détecter une tentative d'effraction (ex: quelqu'un qui essaie de forcer une porte ou une fenêtre).
Je ne les ai pas testés.

# Intérieur

Pour l'intérieur, on peut aussi utiliser des caméras, mais aussi des capteurs de présence (radars micro-ondes) qui 
permettent à la fois de detecter la présence en temps normal (je rentre dans une pièce, je veux que les [lumières](/domotique/systemes/eclairage/) s'allument), 
mais aussi de détecter une présence anormale (il y a quelqu'un dans la maison alors que je suis parti).
