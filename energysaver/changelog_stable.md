# Changelog du plugin Energy Saver

>**IMPORTANT**
>
>S'il n'y a pas d'information sur la mise à jour, c'est que celle-ci concerne uniquement de la mise à jour de documentation, de traduction ou de texte.

# Version Stable

## 03/01/2023
Nouveautés / Evolutions :
- Ajout d'une vérification par jour pour informer de la découverte de nouveaux équipements que le plugin pourra prendre en charge. Cette information sera déposée dans le centre de message Jeedom
- Il est maintenant possible de spécifier sur quels jours de la semaine les planifications doivent s'enclencher
- Ajout de commande "Planification x Mode Declencheur On" et "Planification x Mode Declencheur Off"
   
Exemple : L'éxécution de la commande "Planification 1 Mode Declencheur On" (depuis un scénario ou autre) va permettre de désactiver la programmation horaire de la Planification 1. En effet, en activant le mode déclencheur, la planification ne s'éxécutera plus aux heures prévues jusqu'à ce que la commande "Planification 1 Mode Declencheur Off" soit à nouveau éxécutée

<hr/>

# Version Béta

Voir le changelog de la version bêta ici : [Changelog Bêta](https://github.com/BisonJeedom/documentations/blob/main/energysaver/changelog_beta.md)
