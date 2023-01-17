# Changelog du plugin SolCast

>**IMPORTANT**
>
>S'il n'y a pas d'information sur la mise à jour, c'est que celle-ci concerne uniquement de la mise à jour de documentation, de traduction ou de texte.

# Version Stable
Voir le changelog de la version stable ici : [Changelog Stable](https://github.com/BisonJeedom/documentations/blob/main/solcast/changelog_stable.md)

<hr/>

# Version Béta

## 17/01/2023
Nouveautés :
- 2 nouvelles commandes "Prévision J+0 à 6h de la journée complète" et "Prévision J+0 de la journée complète" permettent de voir la courbe de prévision dans un graphique historique dès le début de la journée (Jeedom, JeedomConnect, ...).

Notes : 
- Pour le visualiser dans Jeedom il faut "Autoriser les dates dans le futur coté Jeedom"
- Pour le visualiser dans Jeedom Connect il faut être en version 1.7.1 (à venir prochainement)

## 07/01/2023
Nouveautés :
- Ajout option pour "Ignorer l'avertissement d'index anormal"
- Ajout de la possibilité de modifier les données du graphique "Année". A UTILISER EN CONNAISSANCE DE CAUSE.

Corrections :
- Ajustement du décalage visuel de la prévision haute pour le lendemain qui n'était pas la même que pour aujourd'hui

## 03/01/2023
Nouveautés :
- Ajout des commandes "Prévision J+0 avec moins de nuages" et "Prévision J+0 avec plus de nuages"
- Ajout de données dans le tableau de prévision et production du jour : "Ecart 90/10" et "prévision %"
- Nouveau graphique (à la place du texte) pour les données de prévision du jour et de demain et nouvelles données : prévision minimum/maximum, écart, pourcentage de la prévision dans la fourchette basse/haute
- Le graphique "Année" devient glissant et permet de voir l'historique des mois précédents

## 21/12/2022
Nouveautés :
- Masquage du champs de l'API dans les paramètres pour faciliter la publication de captures

Corrections :
- Aucun graphique affiché dans les premières heures d'utilisations
- Pas ou pas assez de données récupérées sur SolCast pour un nombre de jour de prévision supérieur à 2
- La prévision à 6h n'était plus recalculée en cas d'utilisation d'une actualisation toutes les 2h

## 04/12/2022
Nouveautés :
- Paramètre "Fréquence de raffraichissement des données" pour adapter le plugin à une modification de SolCast qui ne permet plus que 10 requêtes par jour. Par défaut, l'actualisation ne se fera que toutes les 2 heures lors des heures paires.  

**Important** : Si votre compte permet 50 API et que vous souhaitez maintenir une fréquence d'intérrogation chaque heure, il faut modifier ce paramètre

Corrections :
- La valeur de production n'était pas enregistrée le 1er jour du mois (et seulement le 1er jour)

## 29/11/2022
Corrections :
- Un bug dans la gestion de l'affichage des jours pouvait provoquer une erreur 500
- La selection d'une seule journée de prévision provoquait une erreur 500 depuis l'introduction de l'indice de fiabilité (qui est toujours en test)

## 19/11/2022
Nouveautés :
- Visualisation de l'ensemble des valeurs (Prévision, Prévision à 6h et Production) lors du clic sur l'un de ces éléments (merci @jpty)

Corrections :
- Déplacement du bouton d'export qui n'était plus cliquable à cause des zones de slide
- Modification de l'icône pour lui redonner la taille attendu par Jeedom

## 18/11/2022
Nouveautés :
- Ajout des données de prévision à 6h sur le graphique "Mois" et "Année"
- Modification du tableau et du graphique pour que les cases du tableau soient alignées avec les données du graphique "Aujourd'hui"

Corrections :
- Les couleurs des courbes sont les mêmes quelle que soit la vue

Note : Sur le graphique "Année" la "Prévision à 6h" est désactivée par défaut, il faut cliquer dessus pour l'activer et la voir

## 12/11/2022
- Template : Ajout de la vue à l'année avec un graph en baton
- Template : Correction du label des abscisses "Mois" -> "Jour" sur le graphique "Mois"

## 11/11/2022
- Template : Historisation des valeurs de prévision et production journalière pour permettre un affichage de courbes sur le mois en cours. Apparition de sliders sur le graphique
- Core : En cas valeur négative de la production, elle sera ramenée à zéro

## 06/11/2022
- Template : Amélioration pour adapter le graphique à la taille de la tuile
- Template : Amélioration pour afficher la tranche horaire complète dans le tableau (Ex : 10-11 à la place de 11)
- Template : Correction du positionnement de la tranche horaire en cours
- Template : Correction des labels (W -> Wh)

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

## 18/10/2022
- Compatibilité Jeedom 4.3 pour afficher directement la valeur d'une commande lors de l'édition d'un équipement

## 13/10/2022
- Correction d'un bug lors de la création d'un équipement (une commande crée à tort)
- Journalisation de l'information si dépassement du nombre de requêtes journalière
- Limite le nombre d'interrogations de l'API en prenant en compte les limites définies dans le plugin ("Début de la prévision" et "Fin de la prévision")
- Ajout de 2 commandes "Prévision heure suivante (comparaison)" et "Prévision fin de journée (comparaison)" qui pourront être ajoutées à une vue pour comparer les données de prévision et de production réelle

## 08/10/2022
- Ajout de 2 paramètres "Début de la prévision" et "Fin de la prévision" permettant de limiter le nombre de commandes "#Jour x entre yyh et zzh". Il faut indiquer à chaque fois l'heure de fin donc selectionner 7 dans le paramètre permet de démarrer avec la commande "Jour x entre 06h et 07h"
- Ajout d'un paramètre "Niveau de détail des commandes de prévision". "Minimal" (à présent par défaut) permet de limiter la quantité de commandes et de n'afficher que les commandes totalisant l'énéergie de la journée à partir de J+1 (Prévision J+1, Prévision J+2, etc ...). Ce paramètre n'a pas d'influence sur les commandes J+0.

Note : Dans les 2 cas, les commandes déjà existantes sur l'équipement ne seront pas supprimées en changeant ces paramètres, vous devrez le faire manuellement

## 04/10/2022
- Ajout de commandes pour indiquer la prévision d'énergie totale dans le cas le plus favorable (moins de nuages) et le moins favorable (plus de nuages).
Ces commandes ne seront disponibles qu'à partir de J+1 donc avec un "Nombre de jour de prévision" paramétré à 2 minimum sur l'équipement 

## 27/09/2022
- Suppression du décalage empirique de +1h suite aux retours de rennais35000

## 10/09/2022
- Ajout de 3 commandes Top "valeur" et "heure de fin" pour connaitre les meilleurs tranches de prévision

## 08/09/2022
- Ajout d'une commande "Prévision heure suivante"
- Suppression des paramètres globaux

## 03/08/2022
- Version initiale

