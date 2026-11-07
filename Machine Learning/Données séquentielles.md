#ml-1

# Définition

Une donnée séquentielle est une instance décrite par une **séquence** de vecteurs de caractéristiques :

$$x = (x_1, x_2, \dots, x_T)$$

avec $x_t \in \mathbb{R}^n$ pour chaque pas $t$.

Deux propriétés distinguent une séquence d'un simple ensemble de vecteurs :

- l'**ordre** des éléments est porteur d'information ;
- la **longueur** $T$ change d'une instance à l'autre.

Chaque $x_t$ est un vecteur de $n$ attributs, voir [[Donnée et attributs]] : la séquence compte $T$ pas, et $T$ varie.

# Exemple

- une phrase : une séquence de mots, ou de lettres ;
- un signal audio : une séquence de fenêtres de quelques millisecondes ;
- une vidéo : une séquence d'images ;
- une série temporelle : nombre de passagers par mois, prix, relevés de capteurs, journaux d'événements ;
- une séquence d'ADN : une suite de bases.

# Remarque

La longueur variable soulève la question centrale des modèles de séquences : comment un modèle à nombre de poids fixe peut-il lire une entrée de longueur quelconque ? Voir [[Longueur variable des séquences]].

L'ordre porteur d'information interdit de traiter une séquence comme une simple collection de vecteurs : deux séquences formées des mêmes $x_t$ dans un ordre différent sont deux instances distinctes.

Le traitement de ces entrées est l'objet des modèles récurrents, voir [[Réseau récurrent]], et conditionne les tâches que l'on peut mener dessus, voir [[Tâches sur les séquences]].
