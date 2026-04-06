# Changelog du plugin Diagramme relationnel (Bêta)

>**IMPORTANT**
>
>S'il n'y a pas d'information sur la mise à jour, c'est que celle-ci concerne uniquement de la mise à jour de documentation, de traduction ou de texte.

# Version Stable

Voir le changelog de la version stable ici : [Changelog Stable](https://github.com/BisonJeedom/documentations/blob/main/diagrelationnel/changelog_stable.md)

<hr/>

# Version Béta

## 06/04/2026

Améliorations / Nouveautés :

- Ajout d'une option pour changer la direction de l'affichage : Top-Down (par défault) ou Left-Right

Corrections :

- Undefined index: actionCheckCmd dans une fonction

## 04/04/2026

Améliorations / Nouveautés :

- Prise en charge du format natif SVG à la place du PNG (cela permet d'afficher des diagrammes avec plus d'éléments)
- Refonte totale de la navigation dans le diagramme (déplacement à la souris, zoom, boutons) [Travail fait à l'aide d'une IA]
- Amélioration de la gestion des erreurs

Corrections :

- Nettoyage des chaines < et > pour que l'élément qui contient ces caractères puisse s'afficher
- Changement de la couleur de fond pour voir les flêches en mode Dark

## 09/11/2025

Corrections :

- Fix de l’appel à la fonction de refresh à partir de PHP 8 (merci @Noyax37 pour le signalement)

## 21/05/2024

Améliorations / Nouveautés :

- Support Fulls JS sur le widget (pour Jeedom > 4.4)

Corrections :

- Correction des liens vers la doc et le changelog

## 31/03/2024

Corrections :

- Erreur "Invalid argument supplied for foreach()" (merci @Phpvarious)

## 26/02/2024

Corrections :

- Pour éviter qu'une partie du texte concernant la colorisation des éléments inactifs ne passe à la ligne

## 25/02/2024

Améliorations / Nouveautés :

- Possibilité d'exclure un groupe de scénarios
- Possibilité de coloriser les éléments inactifs en gris

## 22/02/2024

Améliorations / Nouveautés :

- Possibilité de choisir la couleur des différents blocs dans la configuration du plugin
- Ajout des relations avec le plugin "Mode"

Corrections :

- Les éléments sont à présent cliquables sans raffraichir la page après une modification de la configuration
- Ajustement de l'amplitude du zoom in/out

## 18/02/2024

Améliorations / Nouveautés :

- Ajout d'une barre de zoom in/out sur l'image d'un diagramme
- Une vérification des relations sera effectuée immediatement après la modification du groupe d'un diagramme

## 17/02/2024

Corrections :

- Correction dans le parcours des scénarios car il pouvait y avoir des éléments en double
- Suppression de la bordure encadrant la descrption dans le widget s'il n'y a pas de description
- Correction d'un plantage quand on utilise le caractère &

## 16/02/2024

- Version initiale
