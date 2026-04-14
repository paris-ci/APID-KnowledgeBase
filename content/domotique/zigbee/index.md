+++
date = '2026-04-13T15:57:00+02:00'
draft = false
title = 'Réseau ZigBee'
categories = ['Domotique']
description = "ZigBee permet de faire communiquer des appareils à faible consommation d'énergie sur de longues distances, en formant un réseau maillé. C'est une technologie très utilisée en domotique pour connecter des capteurs, des interrupteurs, des ampoules, etc."
+++

Pas grand-chose d'écrit ici pour l'instant, mais je recommande :

- Cette antenne : https://fr.aliexpress.com/item/1005006285239013.html (SMLIGHT SLZB-MR4U, ~65€, très bonne portée, fonctionne avec Matter aussi pour l'avenir ! Elle est PoE, Ethernet, Wifi, USB Sérial... bref, on peut la brancher partout et comme on veut !)
- Zigbee2MQTT, qui permet de faire communiquer des appareils Zigbee avec Home Assistant, et de les contrôler depuis votre interface domotique. 
  - C'est une solution très populaire et bien supportée, avec une grande compatibilité d'appareils Zigbee.
- Puisqu'il s'agit d'un réseau maillé, ajouter des prises connectées ZigBee, pas chères sur AliExpress, permet d'avoir un réseau de grande qualité, sans problème de portée dans toute la maison !

## Boutons Zigbee

{{< cards cols="2" >}}
{{< card
link="https://fr.aliexpress.com/item/1005006142580022.html"
image="snzb-01p.png"
options="800x800 q100"
method="Fill"
title="SONOFF SNZB-01P"
subtitle="Bouton sans fil Zigbee, appui simple/double/long, pile CR2477 (~5 ans). Parfait pour déclencher des automatisations Home Assistant."
tag="~8 €"
tagType="info" >}}
{{< card
link="https://fr.aliexpress.com/item/1005007575864175.html"
image="tuya-button-zigbee.png"
options="800x800 q100"
method="Fill"
title="Tuya ZigBee Bouton DIY"
subtitle="Bouton Zigbee sans fil, appui simple/double/long. Ultra économique pour déclencher des scènes et automatisations Home Assistant."
tag="~6 €"
tagType="info" >}}
{{< /cards >}}

## Capteurs Zigbee

{{< cards cols="2" >}}
{{< card
link="https://fr.aliexpress.com/item/1005006508846585.html"
image="aqara-door-sensor.png"
options="800x800 q100"
method="Fill"
title="Aqara Capteur Porte/Fenêtre"
subtitle="Capteur d'ouverture Zigbee, détecte l'état porte/fenêtre en temps réel. Compatible Home Assistant via Zigbee2MQTT ou ZHA."
tag="~8 €"
tagType="info" >}}
{{< card
link="https://fr.aliexpress.com/item/1005009740967694.html"
image="tuya-sirene-zigbee.png"
options="800x800 q100"
method="Fill"
title="Tuya Sirène Zigbee 3-en-1"
subtitle="Sirène d'alarme Zigbee 90dB avec capteurs de lumière et de son intégrés. Idéale pour les alertes et automatisations de sécurité."
tag="~18 €"
tagType="warning" >}}
{{< /cards >}}

## Prises Zigbee

Les prises connectées Zigbee ont un double intérêt : contrôler vos appareils à distance **et** renforcer votre réseau maillé Zigbee, améliorant la portée dans toute la maison.

{{< cards cols="2" >}}
{{< card
link="https://fr.aliexpress.com/item/1005007115973815.html"
image="tuya-prise-zigbee.png"
options="800x800 q100"
method="Fill"
title="Tuya Prise Intelligente EU"
subtitle="Prise Zigbee EU avec mesure de consommation électrique en temps réel. Parfaite pour surveiller vos appareils et étendre votre réseau maillé."
tag="~4 €"
tagType="info" >}}
{{< /cards >}}

## Coordonnateur Zigbee

Le coordonnateur est le cœur de votre réseau Zigbee : il fait le lien entre vos appareils et Home Assistant.

{{< cards cols="2" >}}
{{< card
link="https://fr.aliexpress.com/item/1005006285239013.html"
image="smlight-mr4u.png"
options="800x800 q100"
method="Fill"
title="SMLIGHT SLZB-MR4U"
subtitle="Coordonnateur Zigbee 3.0 multi-connectivité : PoE, Ethernet, WiFi et USB. Supporte jusqu'à 200 appareils, compatible Zigbee2MQTT, ZHA et Matter."
tag="~65 €"
tagType="info" >}}
{{< /cards >}}