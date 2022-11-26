# Changelog du plugin Energy Saver

>**IMPORTANT**
>
>S'il n'y a pas d'information sur la mise à jour, c'est que celle-ci concerne uniquement de la mise à jour de documentation, de traduction ou de texte.

# Version Stable
Pas de version stable pour le moment

<hr/>

# Version Béta

## 26/11/2022
Nouveautés / Evolutions :
- Prise en compte des modifications sur le visuel de l'équipement Energy Saver dès la sauvegarde de la configuration
- Suppression du bouton refresh sur le visuel de l'équipement Energy Saver

## 24/11/2022
Nouveautés / Evolutions :
- Ajout de l'information indiquant si l'équipement ne doit pas être rallumé dans la "Liste des équipements compatibles"

Corrections : 
- Initialisation de quelques variables pour ne pas provoquer d'erreur dans http.error (merci @Phpvarious)
- Correction typo

## 23/11/2022
Nouveautés / Evolutions :
- Prise en charge des versions inférieures à Jeedom 4.3.1 dans le calcul des données (merci @Phpvarious)
- Ajout d'une pause de 1 seconde entre chaque éxécution de commandes pour éviter les ratés dans la transmission des ordres
- Ajout de l'informations indiquant s'il s'agit d'un déclencheur dans la planification

Corrections : 
- Modification des couleurs dans la "Liste des équipements compatibles" pour une meilleurs visibilité dans les 2 thèmes de Jeedom

Note : Ajout temporaire de logs en debug pour recherche d'un problème non résolu

## 22/11/2022
Nouveautés :
- Ajout Etat dans les commandes (compatibilité Jeedom > 4.3.0)

Corrections :
- Nombre d'équipement pris en charge incorrects
- Non affichage de la liste des équipements si la version de Jeedom est inférieur à 4.3.1 (gestion de l'erreur dans le calcul des éléments sur 30 jours)

## 17/11/2022
Nouveautés :
- Mode déclencheur pour les 3 planifications  

Dans ce mode les horaires paramétrées ne sont plus pris en compte et le déclenchement doit être réalisé par de nouvelles commandes dsponible sur l'équipement "Energy Saver"  
Exemple : #[Test][Energy Saver][Planification 1 Off]# et #[Test][Energy Saver][Planification 1 On]#

## 16/11/2022
Nouveautés :
- 3 plages de planifications au lieu d'une seule
- Option dans la configuration générale pour "Eteindre un équipement qui a été rallumé durant la planification (1 fois)"

**Important** :
Avec l'introduction des 3 planifications, les équipements ne seront plus désactivés en le désélectionnant. La selection "Aucune planification" suffira à ne pas prendre en compte l'équipement concerné.

Les équipements déjà pris en charges seront basculés dans la planification n°1 lors de la mise à jour

La consommation et la durée de fonctionnement sur les 30 derniers jours sont calculés par défaut à partir des horaires de la planification n°1 mais changeront en fonction de la planification selectionnées

- Mise à jour de la documentation et ajout d'images

## 10/11/2022
- Version initiale
