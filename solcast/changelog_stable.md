# Changelog du plugin SolCast

>**IMPORTANT**
>
>S'il n'y a pas d'information sur la mise à jour, c'est que celle-ci concerne uniquement de la mise à jour de documentation, de traduction ou de texte.

# Version Stable

## 03/11/2022
- Template : Correction de la courbe de prévision à 6h qui ne s'actualisait pas
- Template : Ajout d'une colorisation des heures pour les 3 tops de la journée
- Configuration : Amélioration de la page de configuration et précision sur l'attendu de "Commande index totale de production"
- Core : Avertissement dans les logs et dans le centre de message si le plugin détecte une erreur dans "Commande index totale de production"

## 31/10/2022
- Template : Correction du tableau car les données de production n'était pas affichées dans certains cas
- Template : Ajout de la courbe de la prévision à 6h. Celle-ci ne bougera pas contrairement à la prévision évolutive
- Template : Ajout d'un indice de fiabilité de la prévision J+1 (EN TEST)

## 30/10/2022
- Evolution du template pour ajouter la production totale de la journée et corriger un problème si "Nombre de jour de prévision" est de 1
- Correction d'un problème sur la production journalière qui ne se mettait pas à 0
- Gestion de la suppression des Cron en cas de désinstallation du plugin

## 29/10/2022
- Mise en place d’un template qui est activé par défaut pour les nouveaux équipements mais que vous devrez activer dans les paramètres pour les existants
- Ajout d’un nouveau paramètre spécifique pour renseigner son index de production
- Ajout d’un cron chaque heure à H + 5mn pour calculer la production

## 26/10/2022
- Version initiale

<hr/>

# Version Béta

Voir le changelog de la version stable ici : [Changelog Bêta](https://github.com/BisonJeedom/documentations/blob/main/solcast/changelog_beta.md)
