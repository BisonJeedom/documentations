# Changelog du plugin SolCast

>**IMPORTANT**
>
>S'il n'y a pas d'information sur la mise à jour, c'est que celle-ci concerne uniquement de la mise à jour de documentation, de traduction ou de texte.

# Version Stable

Voir le changelog de la version stable ici : [Changelog Stable](https://github.com/BisonJeedom/documentations/blob/main/solcast/changelog_stable.md)

<hr/>

# Version Bêta

## 14/03/2025

Nouveautés / Evolutions :

- {Template} Suppression du paramètre "Voir les prévisions à zéro en fin de journée"
- {Template} Ajout d'un paramètre "Valeur maximum pour l'affichage des prévisions". Ce paramètre permet d'afficher les prévisions jusqu'à la valeur indiquée. Valeur par défaut : 1 (pour ne pas afficher le 0 et conserver l'ancien fonctionnement)

## 09/03/2025

Corrections :

- {Template} Correction de l'affichage du tableau si le paramètre "Voir les prévisions à zéro en fin de journée" est coché

## 08/03/2025

Nouveautés / Evolutions :

- {Template} Paramètre "Voir les prévisions à zéro en fin de journée" permettant de tracer les courbes de prévisions jusqu'au zéro en fin de journée

## 03/03/2025

Corrections :

- {Template} Correction message Undefined variable lors de l'affichage sur mobile
- {Template} Correction affichage pour le premier jour du mois sur le graphique "Année"

## 26/11/2024

Corrections :

- {Moteur} Correction d'un problème suite à MAJ du 08/11. La récupération des données étaient réalisées en dehors de heures configurées ce qui pose un problème avec 10 requêtes par jour
- {Template} Correction de l'affichage des barres et courbes qui ne s'affichaient pas dans le cas où des certaines enregistrées étaient vides
- {Moteur} Refresh à 00h05 pour voir les courbes durant la nuit uniquement quand on est en bypass API pour ne pas solliciter "pour rien"

## 17/11/2024

Améliorations :

- Modification du comportement de la case à cochée "Ignorer l'avertissement d'index anormal" pour ne pas avertir quand la PROD est trop élevée (> 500 W) dans la nuit à 3h

## 14/11/2024

Alignement avec la version stable

## 12/11/2024

Corrections :

- {Moteur} Correction d'un plantage sur la fonction array_sum() quand l'API n'a pas retourné assez de données

## 08/11/2024

Améliorations :

- Refresh à 00h05 pour avoir des infos durant la nuit

## 03/11/2024

Améliorations :

- Modification des options de "Calcul de la meilleure heure de démarrage" :  
  Réalisable, le plus tôt dans la journée  
  Réalisable, le plus tard dans la journée  
  Réalisable pour la plus grande quantité de production  
- Linéarisation du calcul de la meilleure heure de démarrage pour éviter des paliers suite au travail avec @micheld
- Modification de la lecture de la Production pour permettre aux index journalier d'être traité de la bonne façon quand l'index n'est pas remis à zéro à minuit mais seulement le matin
- Possibilité de masquer les informations sur la meilleure heure de démarrage dans le template
- Ajout d'une option (désélectionné par défaut) pour afficher les informations concernant le template quand les logs sont en debug (afin de réduire la quantité de logs du mode debug)

Corrections :

- {Moteur} Renvoi incorrect d'une "Heure de démarrage en fonction de la durée demandée" (suite au travail avec @micheld)
- {Typo} Fautes de frappes

## 20/10/2024

Corrections :

- {Moteur} Renvoi incorrect d'une "Heure de démarrage en fonction de la durée demandée" quand la puissance demandée dépassait la prévision
- {Moteur} L'enregistrement d'un équipement créait un nouveau listener alors qu'il existait déjà

## 19/10/2024

Corrections :

- {Moteur} Renvoi incorrect d'une "Heure de démarrage en fonction de la durée demandée" quand la puissance demandée dépassait la prévision

## 05/10/2024

Corrections :

- {Typo} Correction d'une faute de frappe dans une bulle d'information

## 21/09/2024

Améliorations :

- Ajout d'un contrôle à 3h05 pour vérifier que la valeur de production n'est pas trop élevée (> 500 W) car pouvant montrer un problème

Corrections :

- {Moteur} "Unsupported operand types" dans certains cas sous Debian 12
- {Moteur} "Unsupported operand types: string * int" en cas de commandes de prévisions vides
- {Moteur} Ajustements sur la déclaration des méthodes

## 25/07/2024

Corrections :

- {Commandes} Suppression de la commande JSON SolCast qui était surtout utilisée par le developpeur et qui pose problème dans les futures versions de Jeedom à cause de la longeur de la chaine (merci @m.georgein)

## 16/07/2024

Améliorations :

- {Moteur} Ajout de statistiques sur l'écrêtage d'un équipement global

## 13/07/2024

Améliorations :

- {Moteur} Possibilité de faire un écrêtage de la puissance maximum pour un équipement global
- {Moteur} La commande Index de production supporte à présent un calcul donc par exemple #[obj][eq][commande1]# + #[obj2][eq2][commande2]#

Corrections :

- {Moteur} Correction "Unsupported operand types" durant l'affichage du template
- {Moteur} Correction "Argument #2 must be of type array" dans une fonction

## 02/07/2024

Améliorations :

- Compatibilité Debian 12.5 et PHP 8.2

Corrections :

- {Moteur} Correction "Undefined offset" durant l'affichage du template
- {Moteur} Sécurisation de l'enregistrement des données du mois qui pouvait provoquait un dysfonctionnement dans l'affichage des graphiques (plus de graphique en barres, etc ...)

## 17/06/2024

Corrections :

- {Commandes} Parfois, la mise à jour de "Durée de fonctionnement pour retour heure de démarrage" ne déclenchait pas le calcul de la commande "Heure de démarrage en fonction de la durée demandée". Ajout d'une routine de vérification (à xxh45) pour vérifier la présence de la bonne entrée dans les Listener
- {Moteur} Correction d'un possible "Undefined offset" lié à la mise à jour de la commande "Durée de fonctionnement pour retour heure de démarrage"
- {Moteur} Correction d'un impact sur les performances lors des déclenchements à xxh45 (récupération prévision) et xxh05 (récupération production)

Améliorations :

- La commande "Durée de fonctionnement pour retour heure de démarrage" peut maintenant prendre 2 paramètres : durée;puissance
durée : pas de changement, la durée de fonctionnement de l'appareil
puissance : la puissance de l'appareil
Ainsi suivant les prévisions il pourrait ne pas y avoir d'horaire répondant à ces conditions. Dans ce cas la commande "Heure de démarrage en fonction de la durée demandée" pendra la valeur "no proposal"

## 03/06/2024

Corrections :

- {Template} Un warning inaproprié (commande manquante) était loggué dans certaines conditions lors de l'affichage d'un template

## 01/06/2024

Corrections :

- {Commandes} Le calcul de la meilleure heure de démarrage ne se faisait pas dans le cas d'un équipement global

## 21/05/2024

Merci @noodom et @Phpvarious pour la fonction de chargement des JS externes et pour la librairie du carousel

Améliorations :

- {Template} Passage en full JS, changement de la librairie du carousel, suppression du timeout pour l'affichage des graphiques
- {Template mobile} Passage en full JS, changement de la librairie du carousel, suppression du timeout pour l'affichage des graphiques et amélioration du positionnement des éléments

Corrections :

- {Template} Il pouvait arriver que les graphiques ne s'affichaient pas sur certaines configurations

## 02/05/2024

Améliorations :

- {Template mobile} Ajout d'informations sur le template mobile complet

Corrections :

- {Commandes} La commande "Heure de démarrage en fonction de la durée demandée" donnait un résultat une heure trop tard
- {Template mobile} La bascule entre le choix du template mobile complet ou réduit ne se faisait pas correctement
- {Template mobile} Correction de l'affichage pour éviter un décalage sur certains mobiles

## 28/04/2024

Améliorations :

- {Template mobile} Mise à jour du template mobile pour affichage sur la totalité de l'écran et ajout d'un template réduit (uniquement texte) pour affichage sur la moitié de l'écran
- {tableau} Affichage des heures sur 2 lignes différentes pour garder une cohérence lorsque le nombre d'heure affichées augmentes avec les beaux jours
- {commandes} "Prévision heure suivante" sera mise à jour chaque heure si le paramétrage de la fréquence de raffraichissement est définie toutes les 2 heures (sans récupération des nouvelles  les données)
- {logs} Plus de lisibilité en mode debug

Corrections :

- Non cohérence entre l'affichage du tableau et des courbes de prévision (bug probablement introduit en mars 2024)

## 02/04/2024

Corrections :

- La récupération des données pouvaient être correcte mais étaient rejetée par le plugin
- Affichage incorrect des données de la meilleure heure de démarrage quand le template était en mode horizontal

## 01/04/2024

Améliorations :

- Nouveau template pour un accès depuis les mobiles en gardants les mêmes éléments que le template dashboard mais dans l'idée d'être plus facilement utilisable sur mobile (taille de certains caractères, caroussel sur les 2 premiers bargraphs, position des chevrons, etc ...)
- 2 nouvelles commandes permettant de demander au plugin l'heure de démarrage la plus rentable pour mettre en route un appareil (voir documentation et exemple de scénario dans la configuration de l'équipement)
- Les pluparts des paramètres seront maintenant pré-remplis à la création d'un équipement
- {Tableau} Les lignes de l'heure, de la prévision et de la production sont en gras pour mieux les distinguer
- {Tableau} Nouvelle option de paramétrage pour coloriser la ligne de prévision de la même couleur que la fiabilité du jour
- Meilleure prise en compte d'un problème lors de la récupération des données (comme le non remplissage d'un élément sur le rooftop solcast)

Corrections :

- Ajout de l'unité manquante (Wh) sur la commande "Ecart entre la production et la prévision"

## 10/03/2024

Corrections :

- Potentielle erreur "Unsupported operand types: int + string" lors du cron de xxh05

## 05/03/2024

Corrections :

- Suppression de l'affichage d'un Warning dans les logs si des commandes n'existent pas du fait du paramètre "Niveau de détail des commandes" à Minimal
- Les courbes Demain et Après-Demain ne s'afficheront plus si "Niveau de détail des commandes" est paramétré à Minimal (car ces courbes ont besoin de commandes qui n'existent pas à ce niveau de détail)
- L'étiquette Max ne sera plus affichée sur la courbe évolutive si la valeur est nulle
- Les courbes débutaient une heure trop tôt (pour ne pas afficher si la prévision est nulle)

## 23/01/2024

Améliorations :

- Ajout de deux commandes "Ecart entre la production et la prévision" et "Ecart entre la production et la prévision (pourcentage)". Elles permettent de connaitre l'écart entre la production et la prévision évolutive à chaque mise à jour de la production (xxh05). Elles pourraient par exemple servir à pondérer la mise en service d'appareil qui serait uniquement basé sur la prévision
- Ajout de 2 courbes (maximum et suivant le nombre de jour de prévision choisi dans les paramètres). "Demain" et "Après-demain". Elles sont accessibles après la courbe "Aujourd'hui" pour montrer la courbe de prévision de ces journées
- Ajout d'une étiquette "Max" sur la courbe pour visualiser rapidement le maximum de la prévision évolutive dans la journée

## 20/11/2023

Corrections :

- Potentielle erreur "Unsupported operand types: string * int" lors du cron de xxh45

## 09/10/2023

Corrections :

- Production restait à 0 pour le mois et l'année sur un équipement global (2eme correction)

## 04/10/2023

Corrections :

- Production restait à 0 pour le mois et l'année sur un équipement global

## 01/10/2023

Améliorations :

- Ajout d'une case à coché pour ceux qui utilisent un index de production journalier car le calcul de production pouvait être incorrecte suite à la précédente version

## 22/09/2023

Corrections :

- Les calculs de production pouvaient ne pas être fait dans le cas d'un trop grand nombre d'équipements car dépassement de la 5eme minutes -> réduction des temps de pause à 2s entre chaque équipement

## 17/09/2023

Améliorations :

- Lors d'un nouveau jour c'est à présent l'index de la production qui sert de point de départ et non plus la valeur 0. Cela évitera le 1er pic lors d'un nouvelle installation du plugin

## 15/08/2023

Corrections :

- Correction de l'arrondi sur la nouvelle fonctionnalité de correction de la prévision à l'aide du coefficient

## 13/08/2023

Améliorations :

- Possibilité de corriger la prévision avec un coefficient (cela peut servir pour les petits producteurs puisque Solcast ne permet pas de paramétrer en dessous de 1 kW)

## 14/07/2023

Corrections :

- Erreur dans les logs "Undefined variable: tendance"

## 28/05/2023

Corrections :

- Le total de la journée "Prévision J+0" n'était pas calculé lors du cron de 00h45
- Les graphiques en barre Aujourd'hui et demain devenaient illisibles quand la prévision la plus basse etait la même que la prévision la plus haute
- Meilleure visibilité des couleurs sur les graphiques "aujourd'hui" et "demain" en version 4.4
- Quelques changements dans les logs en debug

## 15/05/2023

Améliorations :

- Possibilité de définir une commande de production pour un équipement global (utile si l'on a pas de valeur de production pour chaques orientations)
- Introduction de statistiques, accessibles dans la page de configuration des équipements

Corrections :

- L'historisation de certaine commande étaient réactivée alors qu'elle avait été désactivée manuellement

## 29/04/2023

Corrections :

- La commande "Production de la journée par heure" n'était pas calculée dans l'équipement global (nouveau fix)
- Ajout d'un timeout sur le chargement des graphiques barres d'informations aujourd'hui et demain pour préparer l'arrivée de la v4.4

## 24/04/2023

Nouveautés :

- 2 Options pour le tracé des graphiques "Aujourd'hui" et "Mois"
  - Lignes droites ou lignes courbes. Lignes droites par défaut
  - Affichage ou non des points sur la courbes. Affichage des points par défaut

Corrections :

- La commande "Production de la journée par heure" n'était pas calculée dans l'équipement global

## 20/04/2023

Corrections :

- La première valeur de production de la journée pouvait être incorrecte
- Réduction de la marge pour changer la vue du graphique afin de pouvoir cliquer sur le dernier point de la journée

## 08/04/2023

Nouveautés :

- Ajout d'une commande "Production de la journée par heure". Elle pourra servir, par exemple dans Jeedom Connect pour le tracé des graphiques dans un widget

Corrections :

- L'affichage de certaines commandes était réactivé systématiquement

## 21/03/2023

Corrections :

- Les bargraphs du jour et du lendemain n'étaient pas affichés sur un équipement global dans certaines conditions

## 18/03/2023

Corrections :

- Suppression du moyennage de l'historique pour les commandes  "Prévision J+0 de la journée complète" et  "Prévision J+0 à 6h de la journée complète" afin que la courbe tracée soit correcte
- La courbe de prévision évolutive d'un équipement global n'était pas prise en compte avec un niveau de detail défini sur "Minimal"

## 12/03/2023

Corrections :

- Problème potentiel lors du reset des données à 00h05

## 27/02/2023

Corrections :

- Problème d’affichage de la page de configuration d'un équipement (merci @cddu33)

## 20/02/2023

Nouveautés :

- Mode "Contournement de l'API" : Nouvelle option à paramétrer pour récupérer les données (limité à J+3 environ) à l'aide des identifiants du compte SolCast et sans consommation de l'API  
Cette possibilité permet de repasser sur une interrogation toutes les heures pour les comptes limités à 10 requêtes par jour et de faciliter l'utilisation de l'équipement global dans ce cas de figure  
Merci à @Noyax37 pour la découverte  

**Attention** : Il est possible que cette méthode ne fonctionne plus du jour au lendemain !

## 12/02/2023

Nouveautés :

- Equipement global :  
    Ajustement des données de l'équipement en fonction des fils lors de la sauvegarde  
    Création des commandes nécéssaires au-delas de J+0  
    Commande "Prévision heure suivante"  

Corrections :

- Erreurs PHP Notice

## 09/02/2023

Nouveautés :

- Equipement global :  
    Information du rafraichissement  
    Non affichage d'une partie de l'équipement (liée à l'information de rafraichissement)  
    Erreur de calcul sur la prévision à 6h  
    Correction des messages d'erreurs qui peuvent apparaitre au début, lorsque toutes les données ne sont pas obtenues par le plugin  
    Calcul des 3 tops  
    "Prévision J+0 de la journée complète" pour courbe prévisionnelle de la journée  
    "Prévision J+0 à 6h de la journée complète" pour courbe prévisionnelle de la journée à 6h  

## 03/02/2023

Nouveautés :

- Un équipement peut maintenant être global afin de regrouper les données d'autres équipements. A utiliser dans le cas de plusieurs orientations.
- 2 nouvelles commandes : "Prévision J+0 à 6h" et "Indice de fiabilté J+0"
- Ajout de la prévision à 6h pour la journée
- Ajout d'un indice de fiabilité entre 1 (faible fiabilité) et 4 (très bonne fiabilité) réalisé avec une autre méthode de calcul (proposition @pj66). Cet indice est basé sur la prévision à 6h et ne bougera donc pas de la journée.

Corrections :

- Correction des messages d'erreurs qui peuvent apparaitre au début, lorsque toutes les données ne sont pas obtenues par le plugin

## 25/01/2023

Corrections :

- Aucune mise à jour des données de 6h quand le début de prévision paramétrée est supérieur 7h

## 24/01/2023

Nouveautés :

- Possibilité de passer sur un template "horizontal" afin d'occuper moins de place verticalement et s'adapter plus facilement à un design "tablette"
- Possibilité de ne pas afficher certains éléments du template pour gagner encore de la place au besoin : barre d'information "Aujourd'hui", barre d'information "Demain", tableau de données "Aujourd'hui", graphiques en courbes, informations de dernières actualisation

Corrections :

- Les données la nouvelle commande "Prévision J+0 à 6h de la journée complète" permettant de tracer la courbe de prévision des 6h était celle de la veille

## 22/01/2023

Corrections :

- L'affichage des graphiques plantait dans certaines condition suite à la mise à jour du 21/12 (liée aux commandes "Prévision J+0 avec moins de nuages" et "Prévision J+0 avec plus de nuages"

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
