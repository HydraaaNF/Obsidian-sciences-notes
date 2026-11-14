#dmv-visualization

# Définition

La conception d'une visualisation se conduit en répondant à cinq questions de réalisation, qui décomposent le comment :

- comment arranger les données dans la vue, spatialement ?
- comment les mapper sur les canaux non spatiaux ?
- comment les manipuler dans la vue ?
- comment les facetter entre plusieurs vues ?
- comment les réduire dans la vue ?

# Interprétation

Chaque question ouvre une famille de choix, traitée par des techniques distinctes :

- l'arrangement spatial combine l'expression de toutes les données, leur séparation sans recouvrement, leur ordre et leur alignement : voir [[Exprimer toutes les données dans la vue]], [[Séparer les marques sans recouvrement]] et [[Ordonner et aligner les marques]] ;
- le mapping sur les canaux non spatiaux fixe l'efficacité de la lecture : voir [[Canaux visuels et efficacité d'encodage]] ;
- la manipulation regroupe le changement, la sélection et la navigation : voir [[Manipulation d'une visualisation]] ;
- la facettisation répartit les données entre plusieurs vues : voir [[Vues multiples coordonnées]] ;
- la réduction filtre, agrège ou résume les données pour alléger la vue : voir [[Réduction des données affichées]].

# Remarque

Ces questions forment le volet comment du [[Cadre d'analyse de la visualisation]], une fois les données et les tâches abstraites.
Elles ne se traitent pas isolément : une même vue répond aux cinq à la fois, et chaque réponse contraint les autres.
