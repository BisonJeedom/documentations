# Documentation du plugin SolCast (version Béta)

## Présentation

Ce plugin permet de récupérer les données de SOLCAST afin de disposer des prévisions de production photovoltaïque (jusqu'à J+4) dans Jeedom
**Il est nécéssaire de créer un compte sur SOLCAST**

## Création d'un compte sur le site SOLCAST

Une fois votre compte créé sur [SOLCAST](https://solcast.com) il faudra renseigner votre "Rooftop" et le site vous fournira un lien et une clef API correspondant à votre installation photovoltaïque. Il est obligatoire de paramétrer votre site SolCast dans le plugin avec ces 2 informations (ressource_id et api_key)

Dans le détail :

1. Créer votre compte de type "Home User" sur <https://toolkit.solcast.com.au/register>  
![Création](images/SolCast_10_requests_only.png)
2. Créer votre "Rooftop" et indiquer les données techniques de vos panneaux photovoltaïques (Latitude, Longitude, AC Capacity, DC Capacity, Azimuth et Tilt)
    - Latitude et Longitude au format x.y. Exemple pour la tour Eiffel : Latitude : 48.85823 / Longitude : 2.29457
    - AC Capacity (inverters) à exprimer en kW : indiquer la puissance maximum que peut produire votre installation dans la réalité (max vos courbes en été)
    - DC Capacity (modules) à exprimer en kW : indiquer la puissance crête théorique de votre installation
    - Azimuth : Orientation de vos panneaux entre -180 et 180 sachant que 0 correspond au Nord et 180 au Sud et qu'il faudra indiquer un nombre négatif si les panneaux sont orientés vers l'EST et positif si les panneaux sont orientés vers l'OUEST.  
   Exemple : -90 pour EST et 90 pour OUEST  
![Création](images/SolCast_Boussole.png)  
      > TIPS : vérifier l'orientation de votre toit sur <https://www.geoportail.gouv.fr/carte> en utilisant "Outils > Mesures > Mesurer un azimut"  
      > &rarr; Tracer un trait depuis le faîtage jusqu'à la goutière en suivant la rive  
      > Si le chiffre obtenu est X alors :
      >
      > - Si les panneaux sont orientés vers l’EST alors indiquer : 0-X
      > - Si les panneaux sont orientés vers l’OUEST alors indiquer : 360-X  
      > Exemple avec une maison dont les panneaux sont orientés vers l'EST :  
      ![Création](images/SolCast_Determiner_Azimuth.png)  

    - Tilt (Horizontal) : Inclinaison des panneaux par rapport à l'horizontale
    - Efficiency factor : Le pourcentage d'efficacité de votre installation
![Création](images/rooftop-site_creation.png)

3. Ouvrir votre Rooftop, le résumé de votre site est à droite :  
    - Copier l'information Ressource Id, elle sera à saisir dans le paramètre **Ressource ID** du plugin  
![Création](images/SolCast_Site_Summary.png)

4. Dans le menu en haut à droite, cliquer sur "Your API Key" puis sur "Show API Key"
    - Noter votre clef API, elle sera à saisir dans le paramètre **API Key** du plugin  
![Création](images/SolCast_API_Key.png)

## Création d'un site dans le plugin SolCast

1. Créer un nouveau site côté plugin
2. Renseigner obligatoirement :
    - Ressource ID : Information issue du bloc précédent à l'étape 3
    - API Key : Information issue du bloc précédent à l'étape 4
3. (Optionel) Paramétrage d'un équipement global : voir section "Configurer plusieurs orientations" à la fin de la documentation
4. (Optionnel) Fréquence de raffraichissement des données : Toutes les 2 heures par défaut mais il est possible de demander une actualisation chaque heure si votre abonnement le permet. **Attention laisser ce paramètre par défaut si votre compte ne permet que 10 requêtes ou renseignez-vous sur Community**
5. (Optionnel) Nombre de jour de prévision : Chiffre entre 1 (par défaut) et 4 correspondant au nombre de jour(s) de prévision. 1 jour correspond au jour en cours. Je recommande de ne pas aller au delà de 2 jours dans un premier temps pour ne pas créer des commandes inutilement
6. (Optionnel) Configurer au besoin l'heure de "Début de la prévision" et "Fin de la prévision" pour limiter le nombre de commandes (**Attention si votre compte ne permet que 10 requêtes**)
7. (Optionnel) Choisir le "Niveau de détail des commandes" : Si vous choisissez "Minimal" (par défault) les commandes principales ne seront générées et visibles que pour "Jour 0", même si vous choisissez un nombre de jour de prévision supérieur à 1. Cela impact l'affichage des courbes (voir section "Les courbes et graphiques")
8. (Optionnel) Indiquer votre commande d'index de production dans "Commande index total de production"
9. (Optionnel) Cocher "Index de production de type journalier" si votre index est de ce type donc remis à zéro chaque jour
10. (Optionnel) "Ignorer l'avertissement d'index anormal" permet de ne plus recevoir d'avertissement si l'index de production redescend, ce qui pourrait-être le cas d'une installation qui consomme un peu dirant la nuit.
11. (Optionnel) "Corriger la prévision avec un coefficient" permet d'ajuster la prévision pour les petits producteurs puisque Solcast ne permet pas un paramétrage en dessous de 1 kW. Exemple : 0.8 vas transformer une prévision de 700 W en 560 W
12. (Optionnel) "Ecrêter la puisssance maximale" est réservé dans le cas d'un équipement global pour indiquer la puissance maximum que peut délivrer l'onduleur
13. (Optionnel) "Calcul de la meilleur heure de démarrage" si le calcul doit renvoyer le plus tôt ou le plus tard dans la journée
14. (Optionnel) "Coloriser les valeurs de prévision" permet d'afficher les valeurs de prévision dans la couleur de de l'indice de fiabilité
15. (Optionnel) "Utiliser le template du plugin" permet d'afficher le template du plugin à la place d'une suite de commandes
16. (Optionnel) "Template horizontal" permet d'afficher le template du plugin de façon plus horizontal pour ête plus adaptée à un affichage sur tablette
17. (Optionnel) "Template mobile" permet de choisir sir l'affichage doit se faire sur 1 ou 2 colonnes lors de l'affichage en version mobile
18. (Optionnel) "Ne pas afficher les points sur les courbes" permet de voir une courbe sans les points
19. (Optionnel) Les options "Ne pas afficher la barre d'information Aujourd'hui", "Ne pas afficher la barre d'information Demain", "Ne pas afficher le tableau de données Aujourd'hui", "Ne pas afficher les graphiques en courbes" et "Ne pas afficher les informations de dernières actualisation" permettent de masquer ces éléments sur le template

Note : Afin d'économiser de la place en largeur, les heures pour lesquelles les données de prévision sont nulles ne sont pas affichées dans le tableau  

## Les courbes et graphiques

Le widget affiche plusieurs informations (suivant le paramétrage de votre équipement - Section "Création d'un site dans le plugin SolCast") :  

- Les données, sous forme de barre, de la prévision et de la production du jour
- Les données, sous forme de barre, de la prévision du lendemain
- Les données, sous forme de tableau, de la prévision et de la production du jour
- Plusieurs courbes dont :
  - Les courbes de prévision à 6h, prévision évolutive et production pour Aujourd'hui
  - Les courbes de prévision à 6h, prévision évolutive et production pour Demain (si Affichage Maximal et nombre de jour supérieur ou égal à 2)
  - Les courbes de prévision à 6h, prévision évolutive et production pour Après-Demain (si Affichage Maximal et nombre de jour supérieur ou égal à 3)
  - Les courbes de prévision à 6h, prévision évolutive et production pour le mois en cours
  - Des colonnes de prévision à 6h, prévision évolutive et production pour une année glissante

Quelques captures et explications des données :  
![Création](images/SolCast_template.png)
![Création](images/SolCast_template_part1.png)![Création](images/SolCast_template_part2.png)  
![Création](images/SolCast_template_graphique_demain.png)![Création](images/SolCast_template_graphique_apresdemain.png)  
![Création](images/SolCast_template_graphique_mois.png)![Création](images/SolCast_template_graphique_annee.png)

## Cron

Le plugin génère 2 cron :

- Le premier à chaque heure et 45 minutes pour mettre à jour les commandes en fonction des prévisions
- Le deuxieme à chaque et 5 minutes pour mettre à jour les données de production si vous l'avez renseigné

## Commandes principales

La quantité de commandes dépend du nombre de jours de prévision choisi dans le plugin  
Les commandes issues de SOLCAST sont les commandes de ce type : "Jour 0 entre 10h et 11h"  
Ces commandes contiennent la quantité de Wh prévue à la fin de la tranche horaire

Le plugin rafraichit les informations chaque heure et 45 minutes (Exemple : 10h45)

Lors du cron de 0h45 ces commandes sont remises à zéro

**Important** : Les commandes antérieures à l'heure du rafraichissement ne sont pas mises à jour (elles ne sont plus communiquées par l'API) c'est à dire que lors du cron de 10h45, la commande "J0 entre 11h et 12h" et les suivantes sont mises à jour mais la commande "J0 entre 10h et 11h" et les précédentes conserveront leurs valeurs

## Commandes secondaires

- Une commande indiquant la prévision sur l'heure suivante : "Prévision heure suivante"
- Des commandes totalisant la quantité de Wh pour chaque jour : "Prévision J+x"
- Des commandes totalisant la quantité de Wh pour chaque jour dans les cas où il y a plus ou moins de nuages que prévu : "Prévision J+x avec moins de nuages" / "Prévision J+x avec plus de nuages"
- Des commandes indiquant les 3 Tops de la journée avec les valeurs et les heures de fin : "Top x valeur" / "Top x heure de fin"
- 2 commandes "Prévision heure suivante (comparaison)" et "Prévision fin de journée (comparaison)" qui permettent de comparer les prévisions à la production réelle sur une vue car ces commandes sont décalées dans le temps pour donner la valeur au même moment que la valeur de production
- 2 commandes "Prévision J+0 à 6h de la journée complète" et "Prévision J+0 de la journée complète" qui permettent de voir la courbe de prévision de la journée dans un graphique historique dès le début de la journée (Jeedom, JeedomConnect, ...). La courbe à 6h ne bouge pas mais l'autre évoluera avec l'affinage de la prévision au fil des heures.  
Pour les visualiser dans Jeedom il faut "Autoriser les dates dans le futur" (Réglages > Système > Configuration > Equipements)
Pour les visualiser dans Jeedom Connect il faut être en version 1.7.1 et activer le mode "Dates dans le futur" dans le widget Historique
- 2 commandes "Ecart entre la production et la prévision" et "Ecart entre la production et la prévision (pourcentage)" qui permettent de connaitre l'écart entre la production et la prévision évolutive à chaque mise à jour de la production (xxh05)
- 2 commandes "Durée de fonctionnement pour retour heure de démarrage" et "Heure de démarrage en fonction de la durée demandée" :  
  Vous pouvez envoyer une valeur "durée" ou "durée;puissance" dans la commande "Durée de fonctionnement pour retour heure de démarrage"  
  En retour le plugin alimentera la commande "Heure de démarrage en fonction de la durée demandée" avec la meilleure heure de démarrage pour maximiser l'utilisation de la production  
  En fournissant la "puissance" de votre équipement, le plugin en tiendra compte et pourrait ne pas trouver d'heure adequate. Dans ce cas la commande "Heure de démarrage en fonction de la durée demandée" prendra la valeur "no proposal"  
  Il est donc possible de planifier, par scénario, le démarrage d'un équipement qui va tourner, par exemple, pendant 90mn, en le faisant au plus tôt et au sommet de la production  
  Si l'heure à laquelle il aurait fallut mettre en service est dépassée, le retour sera l'heure actuelle + 1 minute  
  
  Note : Un exemple de scénario est disponible dans la configuration de l'équipement

## Utilisation et principes de fonctionnement

L'utilisation principale est de connaitre la quantité de Watts qui sera produite pour chaque tranche horaire afin de prévoir de faire fonctionner des équipements au bon moment (chauffe-eau, pompe, etc ...)  
Un comparatif entre les données du jour et du lendemain permet de reporter ou d'avancer l'utilisation des équipements consommateurs

10 requêtes par jour sont possibles sur l'API depuis le 1er décembre 2022.  
**Attention de définir les paramètres "Début de la prévision" et "Fin de la prévision" en conséquence**  

Si votre compte permet 50 requêtes il est possible de créer un second rooftop avec des paramètres (inclinaison, puissances AC et DC) un peu différents pour voir si les prévisions se rapprochent un peu plus de la réalité.

## Configurer plusieurs orientations

Si vous avez la chance d'avoir plusieurs orientations, il est possible de paramétrer le plugin pour obtenir des données globales.  
Procédure pour 2 orientations, à adapter si vous en avez plusieurs !  

1. Créer, configurer et activer l'équipement correspondant à l'orientation n°1. Laisser le paramétrage global sur "Aucun" puis sauvegarder
![Création](images/SolCast_EqGlobalVierge.png)
2. Créer, configurer et activer l'équipement correspondant à l'orientation n°2. Laisser le paramétrage global sur "Aucun" puis sauvegarder
![Création](images/SolCast_EqGlobalVierge.png)
3. Créer et activer l'équipement global puis sauvegarder (il n'y a pas à indiquer de paramètres)
4. Parametrer l'équipement global sur les équipements correspondants aux orientations n°1 et n°2 puis sauvegarder
![Création](images/SolCast_EqFils.png)
5. Sur l'équipement global, cocher "Equipement Global" puis sauvegarder
![Création](images/SolCast_EqGlobal.png)

## Modification des données

Dans la page de configuration d'un équipement, il est possible de modifier les données du graphique "Année", pour réinitialiser les valeurs ou corriger ce qui que vous voulez. A UTILISER EN CONNAISSANCE DE CAUSE.  
Selectionner le mois, le type de données (prévision évolutive, prévision à 6h, production) et la valeur à envoyer. Une valeur non saisie sera considéré comme nulle.  
![Création](images/SolCast_Modify_Values.png)
