# Changelog du plugin Impacts de foudre (Bêta)

>**IMPORTANT**
>
>S'il n'y a pas d'information sur la mise à jour, c'est que celle-ci concerne uniquement de la mise à jour de documentation, de traduction ou de texte.

# Version Stable

Non disponible en version stable

<hr/>

# Version Béta

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
