# Changelog du plugin SolCast

>**IMPORTANT**
>
>S'il n'y a pas d'information sur la mise à jour, c'est que celle-ci concerne uniquement de la mise à jour de documentation, de traduction ou de texte.

# Version Stable

## 30/09/2023

Améliorations :

- Lors d'un nouveau jour c'est à présent l'index de la production qui sert de point de départ et non plus la valeur 0. Cela évitera le 1er pic lors d'un nouvelle installation du plugin

Corrections :

- Les calculs de production pouvaient ne pas être fait dans le cas d'un trop grand nombre d'équipements car dépassement de la 5eme minutes -> réduction des temps de pause à 2s entre chaque équipement

## 15/08/2023

Nouveautés / Améliorations :

- Possibilité de corriger la prévision avec un coefficient (cela peut servir pour les petits producteurs puisque Solcast ne permet pas de paramétrer en dessous de 1 kW)

Corrections :

- Le total de la journée "Prévision J+0" n'était pas calculé lors du cron de 00h45
- Les graphiques en barre Aujourd'hui et demain devenaient illisibles quand la prévision la plus basse etait la même que la prévision la plus haute
- Meilleure visibilité des couleurs sur les graphiques "aujourd'hui" et "demain" en version 4.4
- Quelques changements dans les logs en debug
- Erreur dans les logs "Undefined variable: tendance"

## 23/05/2023

Nouveautés / Améliorations :

- Possibilité de définir une commande de production pour un équipement global (utile si l'on a pas de valeur de production pour chaques orientations)
- Introduction de statistiques, accessibles dans la page de configuration des équipements
- 2 Options pour le tracé des graphiques "Aujourd'hui" et "Mois"
  - Lignes droites ou lignes courbes. Lignes droites par défaut
  - Affichage ou non des points sur la courbes. Affichage des points par défaut

Corrections :

- L'historisation de certaines commandes étaient réactivée alors qu'elle avait été désactivée manuellement
- Ajout d'un timeout sur le chargement des graphiques barres d'informations aujourd'hui et demain pour préparer l'arrivée de la v4.4
- La commande "Production de la journée par heure" n'était pas calculée dans l'équipement global
- La première valeur de production de la journée pouvait être incorrecte
- Réduction de la marge pour changer la vue du graphique afin de pouvoir cliquer sur le dernier point de la journée

## 16/04/2023

Nouveautés :

- Ajout d'une commande "Production de la journée par heure". Elle pourra servir, par exemple dans Jeedom Connect pour le tracé des graphiques dans un widget

Corrections :

- L'affichage de certaines commandes était réactivé systématiquement
- Fautes d'orthographes dans la documentation (merci @Furaxworld)

## 30/03/2023

Corrections :

- Suppression du moyennage de l'historique pour les commandes  "Prévision J+0 de la journée complète" et  "Prévision J+0 à 6h de la journée complète" afin que la courbe tracée soit correcte
- La courbe de prévision évolutive d'un équipement global n'était pas prise en compte avec un niveau de detail défini sur "Minimal"
- Les bargraphs du jour et du lendemain n'étaient pas affichés sur un équipement global dans certaines conditions

## 12/03/2023

Nouveautés :

- Mode "Contournement de l'API" : Nouvelle option à paramétrer pour récupérer les données (limité à J+3 environ) à l'aide des identifiants du compte SolCast et sans consommation de l'API  
Cette possibilité permet de repasser sur une interrogation toutes les heures pour les comptes limités à 10 requêtes par jour et de faciliter l'utilisation de l'équipement global dans ce cas de figure  
Merci à @Noyax37 pour la découverte  

**Attention** : Il est possible que cette méthode ne fonctionne plus du jour au lendemain !

Corrections :

- Problème potentiel lors du reset des données à 00h05

## 16/02/2023

Nouveautés :

- Possibilité de passer sur un template "horizontal" afin d'occuper moins de place verticalement et s'adapter plus facilement à un design "tablette"
- Possibilité de ne pas afficher certains éléments du template pour gagner encore de la place au besoin : barre d'information "Aujourd'hui", barre d'information "Demain", tableau de données "Aujourd'hui", graphiques en courbes, informations de dernières actualisation
- Un équipement peut maintenant être global afin de regrouper les données d'autres équipements : A utiliser dans le cas de plusieurs orientations.-
- 2 nouvelles commandes : "Prévision J+0 à 6h" et "Indice de fiabilté J+0"
- Ajout de la prévision à 6h pour la journée
- Ajout d'un indice de fiabilité entre 1 (faible fiabilité) et 4 (très bonne fiabilité) réalisé avec une autre méthode de calcul (proposition @pj66). Cet indice est basé sur la prévision à 6h et ne bougera donc pas de la journée.

Corrections :

- Les données de la commande "Prévision J+0 à 6h de la journée complète" permettant de tracer la courbe de prévision des 6h était celle de la veille
- Aucune mise à jour des données de 6h quand le début de prévision paramétrée est supérieur 7h
- Correction des messages d'erreurs qui peuvent apparaitre au début, lorsque toutes les données ne sont pas obtenues par le plugin
- Erreurs PHP Notice

## 22/01/2023

Corrections :

- L'affichage des graphiques plantait dans certaines condition suite à la mise à jour du 21/12 (liée aux commandes "Prévision J+0 avec moins de nuages" et "Prévision J+0 avec plus de nuages"

## 21/01/2023

Nouveautés :

- Ajout des commandes "Prévision J+0 avec moins de nuages" et "Prévision J+0 avec plus de nuages"
- Ajout de données dans le tableau de prévision et production du jour : "Ecart 90/10 » et « prévision %"
- Nouveau graphique (à la place du texte) pour les données de prévision du jour et de demain et nouvelles données : prévision minimum/maximum, écart, pourcentage de la prévision dans la fourchette basse/haute
- Le graphique "Année" devient glissant et permet de voir l’historique des mois précédents
- Ajout option pour "Ignorer l’avertissement d’index anormal"
- Ajout de la possibilité de modifier les données du graphique "Année". A UTILISER EN CONNAISSANCE DE CAUSE
- 2 nouvelles commandes "Prévision J+0 à 6h de la journée complète" et "Prévision J+0 de la journée complète" qui permettent de voir la courbe de prévision dans un graphique historique dès le début de la journée (pour une utilisation dans JeedomConnect ou bien dans Jeedom)

Notes :

- Pour visualiser dans un historique Jeedom il faut "Autoriser les dates dans le futur"
- Pour visualiser dans Jeedom Connect il faut être en version 1.7.1 et activer le mode "Dates dans le futur" dans le widget Historique

Corrections :

- Ajustement du décalage visuel de la prévision haute pour le lendemain qui n’était pas la même que pour aujourd’hui

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

- Sur le graphique "Année" la "Prévision à 6h" est désactivée par défaut, il faut cliquer dessus pour l'activer et la voir
- **Important** : SolCast a changé ces conditions et les comptes ouvert depuis quelques jours ne permettent que 10 requêtes API sur 24h. Un adaptation sera faite sur le plugin dès que possible

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
