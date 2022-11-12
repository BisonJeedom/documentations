# Documentation du plugin Energy Saver (version Béta)

## Présentation
Ce plugin permet d'aider à stopper certains équipements de votre installation Jeedom durant une fourchette horaire afin d'économiser de l'énergie

**Important** : Les équipements doivent posséder une commande On et une commande Off

## Paramétrage

1. [Obligatoire] Dans "Configuration" paramétrer une heure d'arrêt et une heure de remise en service des équipements

## Utilisation

1. Cliquer sur "Liste des équipements compatibles" pour afficher les équipements possedant des commandes On et Off
2. Cocher la case "Prendre en charge" sur les équipements à gérer puis cliquer sur "Sauvegarder"

A l'heure programmée pour l'arrêt les équipements actifs seront éteints
A l'heure programmée pour la mise en service les équipements actifs seront allumés

3. Une option "Ne pas rallumer l'équipement automatiquement" est disponible pour chaque équipement afin qu'il soit arrêté mais non remis en service

## Informations complémentaires

Dans la liste des équipements compatibles, plusieurs informations permettent d'aider à savoir si un équipement devrait être géré :
- La consommation globale
- La puissance instantanée (celle disponible lors de l'ouverture de la fenêtre)
- La consommation sur les 30 derniers jours pendant la période programmée
- La durée de fonctionnement sur les 30 derniers jours pendant la période programmée

Les équipements surlignés en rouge sont ceux non gérés par le plugin et qui présente assez d'informations (Consommation / Puissance / Etat)

En décochant l'un des équipements dans la fenêtre "Liste des équipements compatibles" cet équipement ne sera pas supprimé mais uniquement désactivé
Il ne sera donc plus pris en charge dans la routine de planification

Un équipement est crée en non visible pour chaque équipement pris en charge

Un équipement principal est crée pour supporter l'affichage d'un template donc à afficher sur le dashboard ou dans un design
**Important** : Ne supprimez pas cet équipement

**Important** : Si un évènement venait à rallumer un équipement durant la période planifiée (scénario, action manuelle, action d'un autre plugin, etc...), Energy Saver ne l'éteindra pas !

## Evolutions envisagées
- Option pour permettre d'éteindre un équipement qui venait à se rallumer dans la période planifiée
- Arrêt et démarrage des équipements par déclencheur en plus de la programmation horaire
- Ajout de 2 plages de planification pour en avoir 3 différentes au total
