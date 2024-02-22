# Documentation du plugin Diagramme relationnel (version Bêta)

## Présentation

Ce plugin permet de visualiser la relation les scénarios et les déclencheurs de premier niveau

## Paramétrage général

La couleur des différents bloc peuvent être paramétrés à cet endroit (voir section "Colorisation des éléments du diagramme")

## Création et paramétrage d'un diagramme

Après la création d'un diagramme :

1 - paramétrer le groupe de scénarios parmis la liste [**obligatoire**]
2 - ajouter une description pour décrire ce que représente ce diagramme
3 - sur le widget, cliquer sur la double-flêche pour demander la mise à jour du diagramme

## Informations et principe de fonctionnement

Les scénarios sont assez souvent les pivots de beaucoup d'actions dans Jeedom.
Le plugin propose de montrer les relations entres les scénarios et des différents déclencheurs :

- Quel scénario appel quel autre scénario
- Quel sont les déclencheurs de niveau 1 de chacun d'eux

Un diagramme doit être configuré avec un groupe de scénario

Le plugin analysera les scénarios de ce groupe et constituera un diagramme relationnel permettant d'avoir une bonne visibilité des relations et des déclencheurs pour, par exemple, avoir vue macro de la gestion de son chauffage et pouvoir consitituer une documentation

A 00h30 le plugin effectuera une vérification des diagrammes à la recherche d'éléments qui auraient été modifiés depuis la dernière mise à jour (relation entre les éléments, déclencheurs, description des scénarios)

## Colorisation des éléments du diagramme (paramétrable)

Les scénarios faisant partie du groupe sont représentés avec la couleur "mediumturquoise"
Les actions de déclenchement sont représenté avec la couleur "wheat"
Les déclenchements liés au plugins sont représenté avec la couleur "orchid"
La note attachée au diagramme est représenté avec la couleur "palegreen"
Les scénarios ne faisant pas partie du groupe sont représentés avec la couleur "blanc"

## Remerciements

- Aux concepteurs de <https://yuml.me> sur lequel le plugin se repose pour la création des éléments graphiques
- @Furaxworld pour la conception du logo
