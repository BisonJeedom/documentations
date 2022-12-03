# Changelog du plugin SolCast

>**IMPORTANT**
>
>S'il n'y a pas d'information sur la mise à jour, c'est que celle-ci concerne uniquement de la mise à jour de documentation, de traduction ou de texte.

# Version Stable

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
