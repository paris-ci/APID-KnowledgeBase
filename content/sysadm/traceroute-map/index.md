+++
date = '2025-01-20T15:38:07+01:00'
draft = false
title = 'Afficher un traceroute sur une carte'
categories = ['Sysadm']
description = "Affichage des résultats d'un traceroute sur une carte du monde. Joli !"

[[variables]]
name = "domain"
label = "Domaine"
default = "google.fr"
validation = "text"
+++

{{< variables-form >}}

```shell
open "https://stefansundin.github.io/traceroute-mapper/?trace=$(traceroute -q1 {{< variable "domain" >}})"
```