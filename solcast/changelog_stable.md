# Changelog du plugin SolCast

>**IMPORTANT**
>
>S'il n'y a pas d'information sur la mise à jour, c'est que celle-ci concerne uniquement de la mise à jour de documentation, de traduction ou de texte.

# Version Stable

## 23/12/2022
Nouveautés :
- Masquage du champs de l'API dans les paramètres pour faciliter la publication de captures

Corrections :
- Aucun graphique affiché dans les premières heures d'utilisations
- Pas ou pas assez de données récupérées sur SolCast pour un nombre de jour de prévision supérieur à 2
- La prévision à 6h n'était plus recalculée en cas d'utilisation d'une actualisation toutes les 2h

## 07/12/2022
Nouveautés :
- Paramètre "Fréquence de raffraichissement des données" pour adapter le plugin à une modification de SolCast qui ne permet plus que 10 requêtes par jour. Par défaut, l'actualisation ne se fera que toutes les 2 heures lors des heures paires.  

**Important** : Si votre compte permet 50 API et que vous souhaitez maintenir une fréquence d'intérrogation chaque heure, il faut modifier ce paramètre

Corrections :
- La valeur de production n'était pas enregistrée le 1er jour du mois (et seulement le 1er jour)

## 03/12/2022
Changements et améliorations :
- Travail sur le graphique pour qu'il s'adapte mieux en fonction de la taille de tuile. Les tranches horaires du tableau sont maintenant en face des heures du graphique
- Les tranches horraires sont affichées totalement dans le tableau de la journée (9-10 plutôt que 10)
- Historisation des valeurs de prévision et production journalière pour permettre un affichage de courbes sur le mois et sur l'année

Corrections : 
- Positionnement incorrecte de la tranche horaire en cours
- Labels : W -> Wh
- En cas de production négative (parfois dans la nuit), elle est ramenée à 0
- La selection d'une seule journée de prévision provoquait une erreur 500 depuis l'introduction de l'indice de fiabilité (qui est toujours en test)

Notes : 
-  Sur le graphique "Année" la "Prévision à 6h" est désactivée par défaut, il faut cliquer dessus pour l'activer et la voir
-  **Important** : SolCast a changé ces conditions et les comptes ouvert depuis quelques jours ne permettent que 10 requêtes API sur 24h. Un adaptation sera faite sur le plugin dès que possible

## 06/11/2022
- Mise en place d’un template qui est activé par défaut pour les nouveaux équipements mais que vous devrez activer dans les paramètres pour les existants
- Ajout d’un nouveau paramètre spécifique pour renseigner son index de production
- Ajout d’un cron chaque heure à H + 5mn pour calculer la production
- Gestion de la suppression des Cron en cas de désinstallation du plugin
- Avertissement dans les logs et dans le centre de message si le plugin détecte une erreur dans "Commande index totale de production"

## 26/10/2022
- Version initiale

<hr/>

# Version Bêta

Voir le changelog de la version bêta ici : [Changelog Bêta](https://github.com/BisonJeedom/documentations/blob/main/solcast/changelog_beta.md)
