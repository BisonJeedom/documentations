# Changelog du plugin SolCast

>**IMPORTANT**
>
>S'il n'y a pas d'information sur la mise à jour, c'est que celle-ci concerne uniquement de la mise à jour de documentation, de traduction ou de texte.

# Version Stable
Il n'y a pas de version stable pour le moment

<hr/>

# Version Béta

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

