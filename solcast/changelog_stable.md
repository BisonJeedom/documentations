# Changelog du plugin SolCast

>**IMPORTANT**
>
>S'il n'y a pas d'information sur la mise à jour, c'est que celle-ci concerne uniquement de la mise à jour de documentation, de traduction ou de texte.

# Version Stable

## 28/11/2024

Corrections :

- {Moteur} Correction d'un problème suite à MAJ du 08/11. La récupération des données étaient réalisées en dehors de heures configurées ce qui pose un problème avec 10 requêtes par jour
- {Template} Correction de l'affichage des barres et courbes qui ne s'affichaient pas dans le cas où des certaines enregistrées étaient vides

Améliorations :

- Modification du comportement de la case à cochée "Ignorer l'avertissement d'index anormal" pour ne pas avertir quand la PROD est trop élevée (> 500 W) dans la nuit à 3h
- {Moteur} Refresh à 00h05 pour voir les courbes durant la nuit uniquement quand on est en bypass API pour ne pas solliciter "pour rien"

## 14/11/2024

Améliorations :

- {Commandes} Modification des options de "Calcul de la meilleure heure de démarrage" :  
  Réalisable, le plus tôt dans la journée  
  Réalisable, le plus tard dans la journée  
  Réalisable pour la plus grande quantité de production  
- {Commandes} Linéarisation du calcul de la meilleure heure de démarrage pour éviter des paliers suite au travail avec @micheld
- {Commandes} Modification de la lecture de la Production pour permettre aux index journalier d'être traité de la bonne façon quand l'index n'est pas remis à zéro à minuit mais seulement le matin
- {Template} Possibilité de masquer les informations sur la meilleure heure de démarrage dans le template
- {Template} Ajout d'une option (désélectionné par défaut) pour afficher les informations concernant le template quand les logs sont en debug (afin de réduire la quantité de logs du mode debug)
- {Moteur} Refresh à 00h05 pour voir les courbes durant la nuit

Corrections :

- {Moteur} Renvoi incorrect d'une "Heure de démarrage en fonction de la durée demandée" (suite au travail avec @micheld)
- {Moteur} L'enregistrement d'un équipement créait un nouveau listener alors qu'il existait déjà
- {Moteur} Correction d'un plantage sur la fonction array_sum() quand l'API n'a pas retourné assez de données
- {Typo} Fautes de frappes

## 05/10/2024

Améliorations :

- Ajout d'un contrôle à 3h05 pour vérifier que la valeur de production n'est pas trop élevée (> 500 W) car pouvant montrer un problème

Corrections :

- {Moteur} "Unsupported operand types" dans certains cas sous Debian 12
- {Moteur} "Unsupported operand types: string * int" en cas de commandes de prévisions vides
- {Moteur} Ajustements sur la déclaration des méthodes
- {Typo} Correction d'une faute de frappe dans une bulle d'information

## 26/07/2024

Améliorations :

- Compatibilité Debian 12.5 et PHP 8.2
- La commande "Durée de fonctionnement pour retour heure de démarrage" peut maintenant prendre 2 paramètres : durée;puissance
durée : pas de changement, la durée de fonctionnement de l'appareil
puissance : la puissance de l'appareil
Ainsi suivant les prévisions il pourrait ne pas y avoir d'horaire répondant à ces conditions. Dans ce cas la commande "Heure de démarrage en fonction de la durée demandée" pendra la valeur "no proposal"
- {Moteur} Possibilité de faire un écrêtage de la puissance maximum pour un équipement global
- {Moteur} Ajout de statistiques sur l'écrêtage d'un équipement global
- {Moteur} La commande Index de production supporte à présent un calcul donc par exemple #[obj][eq][commande1]# + #[obj2][eq2][commande2]#
- {Moteur} Sécurisation de l'enregistrement des données du mois qui pouvait provoquait un dysfonctionnement dans l'affichage des graphiques (plus de graphique en barres, etc ...)

Corrections :

- {Commandes} Le calcul de la meilleure heure de démarrage ne se faisait pas dans le cas d'un équipement global
- {Commandes} Parfois, la mise à jour de "Durée de fonctionnement pour retour heure de démarrage" ne déclenchait pas le calcul de la commande "Heure de démarrage en fonction de la durée demandée". Ajout d'une routine de vérification (à xxh45) pour vérifier la présence de la bonne entrée dans les Listener
- {Commandes} Suppression de la commande JSON SolCast qui était surtout utilisée par le développeur et qui pose problème dans les futures versions de Jeedom à cause de la longueur de la chaine (merci @m.georgein)
- {Moteur} Correction d'un impact sur les performances lors des déclenchements à xxh45 (récupération prévision) et xxh05 (récupération production)
- {Moteur} Correction "Undefined offset" durant l'affichage du template
- {Moteur} Correction "Unsupported operand types" durant l'affichage du template
- {Moteur} Correction d'un possible "Undefined offset" lié à la mise à jour de la commande "Durée de fonctionnement pour retour heure de démarrage"
- {Moteur} Correction "Argument #2 must be of type array" dans une fonction
- {Template} Un warning inapproprié (commande manquante) dans certaines conditions lors de l'affichage d'un template

## 26/05/2024

Merci @noodom et @Phpvarious pour la fonction de chargement des JS externes et pour la nouvelle librairie du carousel

Améliorations :

- {Général} Meilleure prise en compte d'un problème lors de la récupération des données (comme le non remplissage d'un élément sur le rooftop solcast)
- {Général} Les pluparts des paramètres seront maintenant pré-remplis à la création d'un équipement
- {Commandes} 2 nouvelles commandes permettant de demander au plugin l'heure de démarrage la plus rentable pour mettre en route un appareil (voir documentation et exemple de scénario dans la configuration de l'équipement)
- {Commandes} "Prévision heure suivante" sera mise à jour chaque heure si le paramétrage de la fréquence de raffraichissement est définie toutes les 2 heures (sans récupération des nouvelles  les données)
- {Tableau} Les lignes de l'heure, de la prévision et de la production sont en gras pour mieux les distinguer
- {Tableau} Nouvelle option de paramétrage pour coloriser la ligne de prévision de la même couleur que la fiabilité du jour
- {Tableau} Affichage des heures sur 2 lignes différentes pour garder une cohérence lorsque le nombre d'heure affichées augmentes avec les beaux jours
- {Template} Passage en full JS, changement de la librairie du carousel, suppression du timeout pour l'affichage des graphiques
- {Template mobile} Passage en full JS, changement de la librairie du carousel, suppression du timeout pour l'affichage des graphiques et amélioration du positionnement des éléments
- {Template mobile} Nouveaux templates pour un accès depuis les mobiles (choix possible d'un complet ou réduit)
- {Logs} Plus de lisibilité en mode debug

Corrections :

- {Commandes} Ajout de l'unité manquante (Wh) sur la commande "Ecart entre la production et la prévision"
- {Template} Il pouvait arriver que les graphiques ne s'affichaient pas sur certaines configurations
- {Template} Non cohérence entre l'affichage du tableau et des courbes de prévision (bug probablement introduit en mars 2024)

## 10/03/2024

Corrections :

- Suppression de l'affichage d'un Warning dans les logs si des commandes n'existent pas du fait du paramètre "Niveau de détail des commandes" à Minimal
- Les courbes Demain et Après-Demain ne s'afficheront plus si "Niveau de détail des commandes" est paramétré à Minimal (car ces courbes ont besoin de commandes qui n'existent pas à ce niveau de détail)
- L'étiquette Max ne sera plus affichée sur la courbe évolutive si la valeur est nulle
- Les courbes débutaient une heure trop tôt (pour ne pas afficher si la prévision est nulle)
- Potentielle erreur "Unsupported operand types: int + string" lors du cron de xxh05

## 03/03/2024

Améliorations :

- Ajout de deux commandes "Ecart entre la production et la prévision" et "Ecart entre la production et la prévision (pourcentage)". Elles permettent de connaitre l'écart entre la production et la prévision évolutive à chaque mise à jour de la production (xxh05). Elles pourraient par exemple servir à pondérer la mise en service d'appareil qui serait uniquement basé sur la prévision
- Ajout de 2 courbes (maximum et suivant le nombre de jour de prévision choisi dans les paramètres). "Demain" et "Après-demain". Elles sont accessibles après la courbe "Aujourd'hui" pour montrer la courbe de prévision de ces journées
- Ajout d'une étiquette "Max" sur la courbe pour visualiser rapidement le maximum de la prévision évolutive dans la journée

## 16/12/2023

Corrections :

- Potentielle erreur "Unsupported operand types: string * int" lors du cron de xxh45

## 05/11/2023

Améliorations :

- Ajout d'une case à coché pour ceux qui utilisent un index de production journalier car le calcul de production pouvait être incorrect

Corrections :

- La production restait à 0 pour le mois et l'année sur un équipement global

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
