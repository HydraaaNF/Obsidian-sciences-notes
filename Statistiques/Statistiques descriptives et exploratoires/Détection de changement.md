#adm-9

# Modèle

Une série statistique est observée au fil du temps, sous la forme d'observations successives indexées par un instant. Autour d'un instant $t$, on distingue deux régimes, décrits chacun par une statistique $\theta$ :

| Régime | Fenêtre d'observation | Statistique |
|---|---|---|
| Avant l'instant $t$ | de $t-k$ à $t$ | $\theta_1$ |
| Après l'instant $t$ | de $t$ à $t+k$ | $\theta_2$ |

La fenêtre de largeur $k$ de part et d'autre de $t$ délimite les observations sur lesquelles chaque statistique est estimée : $\theta_1$ sur les observations qui précèdent $t$, $\theta_2$ sur celles qui le suivent. Sous l'hypothèse d'absence de changement, une statistique $\theta_0$ est estimée sur les observations des deux fenêtres réunies, de $t-k$ à $t+k$ ; la série observée s'étend toutefois au-delà de ces bornes, de part et d'autre.

# Interprétation

Détecter un changement dans une série statistique consiste à localiser l'instant $t$ où la loi des observations passe du régime décrit par $\theta_1$ à celui décrit par $\theta_2$, puis à décider s'il y a effectivement changement.

# Remarque

La comparaison des deux régimes se ramène à une comparaison de [[Fonction de vraisemblance|vraisemblances]] : c'est une application du [[Test du rapport de vraisemblance]], qui tranche entre les valeurs possibles du paramètre à partir des observations disponibles.
