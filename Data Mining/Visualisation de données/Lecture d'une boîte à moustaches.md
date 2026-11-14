#dmv-visualization

# Définition

Une boîte à moustaches résume une distribution par cinq repères : le minimum, le premier quartile, la médiane, le troisième quartile et le maximum.

# Propriétés

- La boîte s'étend du 25e percentile, ou premier quartile $Q_1$, au 75e percentile, ou troisième quartile $Q_3$ : elle contient la moitié centrale des données.
- La médiane est marquée à l'intérieur de la boîte.
- La moustache supérieure s'arrête à la plus grande valeur observée inférieure ou égale à $Q_3 + 1{,}5\,\mathrm{IQR}$.
- La moustache inférieure s'arrête à la plus petite valeur observée supérieure ou égale à $Q_1 - 1{,}5\,\mathrm{IQR}$.
- Une observation située au-delà de ces bornes est tracée séparément, comme valeur possiblement aberrante.

L'écart interquartile est la hauteur de la boîte :

$$\mathrm{IQR} = Q_3 - Q_1$$

L'encoche pratiquée autour de la médiane figure son intervalle de confiance à 95 %, pour $n$ observations :

$$\text{encoche} = \text{médiane} \pm 1{,}57 \times \frac{\mathrm{IQR}}{\sqrt{n}}$$

# Interprétation

La position de la boîte donne le niveau central de la distribution, sa hauteur l'étalement de la moitié centrale, et la longueur relative des deux moustaches l'asymétrie des queues.
L'encoche rend deux boîtes comparables : elle matérialise l'intervalle de confiance de chaque médiane, et deux encoches disjointes signalent des médianes nettement distinctes.
Les points isolés attirent l'attention sur des observations atypiques, qu'un simple résumé numérique masquerait.

# Remarque

L'anatomie de la boîte et le calcul de ses bornes sont détaillés dans [[Boîte à moustaches]].
La boîte à moustaches est une agrégation : elle résume la distribution sans la montrer. Le diagramme en violon donne, pour la même agrégation, le profil de densité de la distribution, ce qui révèle les distributions multimodales qu'une boîte laisse invisibles ; voir [[Réduction des données affichées]].
Un résumé de distribution peut masquer une structure : voir [[Quartet d'Anscombe]].
Comparer plusieurs boîtes suppose de les ordonner et de les aligner : voir [[Ordonner et aligner les marques]].
Le facteur $1{,}5$ fixe la longueur maximale des moustaches : sans lui, une moustache s'arrêterait au quartile et ne dirait plus rien des valeurs extrêmes.
