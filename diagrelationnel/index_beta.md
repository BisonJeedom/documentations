# Documentation du plugin Diagramme relationnel (version Bêta)

## Présentation

Ce plugin permet de visualiser la relation les scénarios et les déclencheurs de premier niveau

## Paramétrage général

Aucun paramétrage n'est nécéssaire

## Création et paramétrage d'un diagramme

Après la création d'un diagramme :

- paramétrer le groupe de scénarios parmis la liste [**obligatoire**]
- ajouter une description pour décrire ce que représente ce diagramme

## Informations et principe de fonctionnement

Les scénarios sont assez souvent les pivots de beaucoup d'actions dans Jeedom.
Le plugin propose de montrer les relations entres les scénarios et des différents déclencheurs :

- Quel scénario appel quel autre scénario
- Quel sont les déclencheurs de niveau 1 de chacun d'eux

Un diagramme doit être configuré avec un groupe de scénario

Le plugin analysera les scénarios de ce groupe et constituera un diagramme relationnel permettant d'avoir une bonne visibilité des relations et des déclencheurs pour, par exemple, avoir vue macro de la gestion de son chauffage et pouvoir consitituer une documentation

## Colorisation des éléments du diagramme

Les scénarios faisant partie du groupe paramétré sont représentés avec la couleur "mediumturquoise"
Les scénarios ne faisant pas partie du groupe paramétré sont représentés avec la couleur "blanc"
Les actions de déclenchement sont représenté avec la couleur "wheat"
La note attachée au diagramme est représenté avec la couleur "palegreen"
