# Changelog du plugin Impacts de foudre (Bêta)

>**IMPORTANT**
>
>S'il n'y a pas d'information sur la mise à jour, c'est que celle-ci concerne uniquement de la mise à jour de documentation, de traduction ou de texte.

# Version Stable

Voir le changelog de la version stable ici : [Changelog Stable](https://github.com/BisonJeedom/documentations/blob/main/blitzortung/changelog_stable.md)

<hr/>

# Version Béta

## 30/10/2023

Améliorations / Ajustements :
- Amélioration du widget mobile pour ajouter le graphique radar. Le choix de l'affichage est à faire dans la configuration de l'équipement (Merci @Spine)

Corrections :
- Un nouvel équipement ne pouvait pas être crée s'il n'y avait pas de coordonnées GPS définies au niveau Jeedom (Merci @Spine)

## 03/10/2023

Corrections :

- Passage d'une valeur forcée de type int à l'API car parfois en string (merci @Bad)

## 28/09/2023

Améliorations / Ajustements :

- Validation du format de la latitude, longitude et rayon au moment de sauver l'équipement (cette validation avait disparue avec le démon)
- Suppression des fichiers inutiles (merci @Bad)
- Nettoyage du code inutilisé (merci @Bad)
- Modification de certain niveau de log pour que le log "info" soit plus leger (merci @Bad)

Corrections :

- Erreur de traitement après la création d'un premier équipement à cause du cache (merci @Bad)
- L'entrée dans le moteur de tâche était défini à 5mn au lieu d'une minute quand elle n'existait pas (merci @Spine pour le signalement)

## 26/09/2023

Améliorations / Ajustements :

- Aucun appel à l'API si aucun équipement n'est actif
- Message de warning dans les logs lorsqu'un équipement à un rayon supérieur à 200 km ce qui ne permet plus de récupérer les données depuis l'API
- Suppression des informations lors d'un changement de paramètres dans l'équipement (latitude, longitude ou rayon)

Corrections :

- Modification de la fonction de génération d'un point GPS aléatoire car elle pouvait poser problème

## 24/09/2023

Améliorations / Ajustements :

- API v2 : Interrogation de l'API avec latitude, longitude et rayon en transmettant des coordonnées aléatoires autour du point pour réduire la quantité de données
- Interrogation aléatoire entre 0 et 40 secondes pour ne pas flooder le serveur
- Ajout d'icônes sur le widget si le plugin ne peux plus communiquer avec le serveur et si le serveur ne reçoit plus d'impacts dans les 5mn afin d'indiquer un problème potentiel

Corrections :

- Utilisation d'un timestamp classique à 10 digits pour l'envoi du payload et et l'anayse des données reçues

## 16/09/2023

Améliorations / Changements :

- Refonte du mecanisme de récupération des impacts
  - Disparition du démon
  - Raffraichissement des impacts chaque minute depuis un serveur tier (un grand merci à @Bad pour l'hébergement et la modification du code concernant cette partie)
  - Plus d'impacts sur les performances puisque cette partie est réalisé sur un serveur et non plus dans un Démon
- Ajout d'un template mobile (un grand merci à @Spine pour cette contribution)
- Amélioration de la visibilité du graphique Radar et adaptation aux thèmes Dark / Light (Merci @Spine)
- Disparition de la commande "Expression déclenchant l'écoute" qui devient inutile

## 12/09/2023

Corrections :

- Ajout d'intervalles forcés tout les 10km sur le graphique Radar car ils n'étaient pas automatiquement calculés suivant le rayon choisi

## 04/09/2023

Améliorations :

- Mise à jour de la documentation
- Configuration de la valeur maximum du rayon pour mieux voir les impacts sur le graphioque Radar (merci @Bad)

Corrections :

- Les paramètres Latitude et Longitude étaient parfois avec des virgules et parfois avec des points sans que cela n'est d'incidence sur le fonctionnement (merci @sagitaz)
- Ajout de la source sur l'ensemble des graphiques

## 01/09/2023

Corrections :

- Impossible de selectionner une commande autre que binaire pour "Expression déclenchant l'écoute"

## 31/08/2023

Améliorations :

- Renommage du paramètre "Commande binaire déclenchant l'écoute des évènements" en "Expression déclenchant l'écoute" puisqu'il est possible à présent de lui indiquer une expression  
Exemple : #[Blitz][Blitz][Probabilité Orage]# > 3
- Ajout d'un graphique "radar" permettant de voir les impacts en fonction de l'orientation et de la distance
- Ajout d'un paramètre "Visualiser les impacts récents sur" pour voir les impacts récents dans une couleur différente pendant 5, 10 ou 15mn
- Mise en place d'un caroussel pour selectionner l'un ou l'autre des graphiques
- Ajout d'un paramètre "Graphique par défaut" pour choisir entre le graphique initial (Distance / Temps) ou le nouveau graphique Radar (Distance / Angle)

Corrections :

- Le changement d'un des paramètres provoquant le redémarrage du démon relançait celui-ci toutes les 5mn
- La commande "Délai de traitement trop important" n'était pas mise à jour
- L'icône "orage" n'était pas toujours correctement géré suivant le statut du paramètre permettant de déclencher l'écoute des évènements

## 28/08/2023

Améliorations :

- Nouveau paramètre "Commande binaire déclenchant l'écoute des évènements"  
Ce paramètre permet de mettre en pause le processus d'écoute des impacts quand la commande est fausse et ainsi de réduire considérablement l'utilisation des ressources quand il n'y a pas de risques d'orage (merci @tomdom pour l'aide sur ce sujet)  
A vous de créer cette commande et de l'alimenter, par exemple à partir des prévisions d'un autre plugin (Metéo France...)
- Ajout d'un icône "orage" dans la barre de l'équipement quand la commande binaire devient vraie
- Validation des données de latitude, longitude et du rayon pour que le démon puisse s'éxécuter
- Redémarrage automatique du démon en cas de changements (latitude, longitude ou rayon) sur un équipement

Corrections :

- Ajustement de la flêche d'orientation sur les templates "Horizontal" et "Vertical"
- Les icônes "map" et "info" n'étaient pas visibles en theme light

## 22/08/2023

Améliorations :

- Optimisation du processus pour filtrer les évènements post-traitement par Jeedom et réduire la charge. *Attention*, il est nécéssaire de redémarrer le démon à chaque modification des coordonnées d'un équipement
- Modification du calcul de la distance jusqu'au point d'impact (abandon du calcul de la distance orthodromique)

Corrections :

- Correction des templates pour être plus fonctionnel avec Jeedom < 4.4

## 21/08/2023

Améliorations :

- Début de l'optimisation du code par l'ajout d'une durée de cycle pour l'envoi des informations à Jeedom. Cette durée est paramétrable mais est de 5 secondes par défaut
- Utilisation du cache pour moins solliciter la base de données
- Nouvelle commande "Délai de traitement trop important" que vous pouvez historiser pour voir les moments où Jeedom ne parvient pas à traiter les données avant le passage du prochain cycle
- Ajout d'un nouveau widget "Minimal" en collaboration avec @Bad, merci à lui !
- Jeedom v4.4 : Ajout d'un bouton pour automatiser l'ouverture d'un post sur Community (merci @tomitomas)
- Démarrage travail de cohérence sur le code des templates (non visible)

Corrections :

- Le bouton d'accès à la documentation n'était pas actif
- Les minutes n'apparaissait plus si la fenêtre était trop réduite et si le nombre d'heure de rétention était trop grand : modification de l'interval

## 16/08/2023

Améliorations :

- Ajout d'un template avec une présentation "vertical" pour faciliter l'affichage sur mobile

Corrections :

- Erreurs relatives à la non initialisation de certaines variables (merci @phpvarious d'avoir corrigé avant moi)
- Protection du code en cas de commandes manquantes

## 15/08/2023

Améliorations :

- Modification du template (widget) pour rendre l'affichage plus cohérent (merci @ngratalou pour les idées)
  - Des cercles pour les données live
  - Des ellipses pour les données sur l'évolution durant les 15 dernières minutes
  - Le nombre de cerles autour du nombre d'impacts augmente en fonction du nombre (1 si moins de 50, 2 si moins de 200 et 3 au dela)
- Nouvelle commande indiquant l'orientation du dernier impact (en degrés par rapport au nord)
- Extension du zoom possible jusqu'à 5 pour voir l'ensemble de la France

Corrections :

- L'évolution sur 15mn pouvait donner un résultat incorrect
- Le nombre d'impact n'était pas remis à zéro s'il n'existait plus d'impacts dans le rayon choisi
- Adaptation de l'interface à la taille horizontal souhaitée dans le dashboard

## 11/08/2023

Améliorations :

- Modification du template (widget) et ajout d'un cercle qui change de couleur en fonction de la distance du dernier impact
- Zones de couleurs pour les impacts très proches (<= 10 km), proches (<= 30 km) ou plus eloignés (> 30 km)
- Nouvelle commande indiquant l'URL de la carte
- Possibilité de paramétrer le zoom lors de l'ouverture de la carte
- 2 Nouvelles commandes pour indiquer l'évolution du nombre d'impacts et de la distance sur les 15 dernières minutes :
    -1 pour une diminution du nombre des impacts / de la distance des impacts
    0 s'il n'y a pas d'orage ou que la variation n'est pas continue
    1 pour une augmentation du nombre des impacts / de la distance des impacts

Corrections :

- Démarrage à 0 de l'axe des distances
- Prise en compte des informations qui arrivent parfois en double dans certains régions
- Modification du paramétrage de la commande "Dernière distance" pour l'historique (Lissage : aucun ; Purge : 1 mois ; Répéter les valeurs identiques : Oui)

## 08/08/2023

Améliorations :

- Ajout d'un bouton pour l'accès à la documentation de la version stable quand elle serait publiée
- Ajout d'un bouton pour l'accès à la carte de Blitzortung
- Ajout d'un serveur d'accès aux données
- Mecanisme de contrôle des dépendances lors de l'installation

Corrections :

- Correction de message "No module named 'websockets'" en ajoutant la dépendance à python3-pyudev
- Correction de l'axe des minutes sur le graphique

## 06/08/2023

Améliorations :

- Ajout d'une entrée personnalisée dans le moteur de tâche

Corrections :

- Modification du nom du plugin : Impacts de foudre (Blitzortung) -> Impacts de foudre
- Modification de l'auteur du plugin (Jeedom SAS vers Bison)
- Le rayon par défaut est bien pris en compte à 50 km par défaut
- Nettoyage d'imports inutiles dans le démon

## 05/08/2023

- Version initiale
