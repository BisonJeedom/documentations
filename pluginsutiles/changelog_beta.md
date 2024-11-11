# Changelog du plugin Plugins Utiles (Bêta)

>**IMPORTANT**
>
>S'il n'y a pas d'information sur la mise à jour, c'est que celle-ci concerne uniquement de la mise à jour de documentation, de traduction ou de texte.

# Version Stable

Voir le changelog de la version stable ici : [Changelog Stable](https://github.com/BisonJeedom/documentations/blob/main/pluginsutiles/changelog_stable.md)

<hr/>

# Version Béta

## xx/11/2024

Améliorations :

- Refresh full dans la nuit du dimanche au lundi pour ne pas rater de changements sur les plugins
- Indication des mots clefs déclencheurs dans l'historique des évènements

Corrections :

- Le nombre de plugins signalés comme nouveau dans les logs n'était pas bon
- Modification des pastilles qui indiquent si le plugin est stable ou beta pour régler un problème d'alignement au survol de la souris

## 13/07/2023

Améliorations :

- Compatibilité Debian 12.5 et PHP 8.2

## 30/04/2023

Améliorations :

- Ajout de l'information sur la certification d'un plugin (Officiel, Conseillé, etc ...) et dans la notification

## 04/04/2023

Améliorations :

- Compatibilité Jeedom v4.4

## 14/02/2023

Corrections :

- Modification de la méthode de tri de l'historique affiché et qui n'était plus correcte dès le 13 de chaque mois

## 12/02/2023

Améliorations :

- Ajout d'une option pour "Exclure les plugins privés"
- Le changement d'une des options éxécutera un raffraichissement sur l'ensemble des plugins du Market lors de la sauvegarde
- Il n'est plus possible de selectionner à la fois "Version stable uniquement" et "Version beta uniquement"

## 10/02/2023

Merci à @tomitomas pour le gros coup de main sur cette version !

Améliorations :

- Modification du principe de fonctionnement : la configuration est transféré au niveau des équipements
- Sélection des champs dans lesquels faire la recherche (nom, description, utilisation, auteur)
- Filtre sur les versions stable ou beta
- Autres critères de recherche (promo, toutes les stables, toutes les beta, changements)
- Alerte possible via une commande de notification

## 07/02/2023

- Version initiale
