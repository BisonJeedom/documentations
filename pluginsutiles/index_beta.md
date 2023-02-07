# Documentation du plugin Plugins Utiles (version Bêta)

## Présentation
Configurez des mots-clefs / centres d'intérêt et ce plugin vous permettra de rester informé lors de la sortie d'un plugin correspondant à vos attentes

## Paramétrage et principe de fonctionnement

Aucun équipement n'est associé à ce plugin, tout ce passe dans la partie configuration

Configurer un ou plusieurs mots-clefs séparés par des points-virgules et sauvegarder  
Exemple : vmc;photovoltaïque;atlantic

![Création](images/Documentation.png)

L'historique des 50 derniers plugins découvert sera indiqué dans la partie "Historique" (même page que la configuration du plugin)
Les lignes de l'historique sont cliquables afin de voir directement le plugin en question

En cochant la case "Alertes dans le centre de message" vous recevrez, en plus, ces informations dans le centre de message

A chaque sauvegarde de la configuration la recherche sera réalisée sur l'ensembles des plugins existants. Les autres fois la recherche ne sera effectuée que sur les nouveaux plugins

Un plugin déjà signalé ne sera pas signalé à nouveau

Une vérification est réalisée :
- A chaque sauvegarde de la configuration
- Chaque jours lors du cron de minuit
