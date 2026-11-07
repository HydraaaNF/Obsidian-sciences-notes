#adm-9

# Modèle

On considère une population unique $X_1, \dots, X_n$ observée à travers une même variable, mais mesurée à deux instants différents : pour chaque individu $i$, la valeur $A_i$ avant traitement et la valeur $P_i$ après traitement. Les deux échantillons ainsi obtenus sont dits **appariés**, chaque mesure « après » étant associée à la mesure « avant » du même individu.

# Propriétés

Le test confronte deux [[Hypothèse nulle et hypothèse alternative|hypothèses]] sur les espérances des deux séries de mesures. L'absence d'effet s'écrit

$$H_0 : \text{aucun effet} \Rightarrow \mathbb{E}[A] = \mathbb{E}[P]$$

et la présence d'un effet prend l'une des trois formes suivantes :

- test bilatéral : $H_1 : \mathbb{E}[A] \neq \mathbb{E}[P]$ ;
- test unilatéral : $H_1 : \mathbb{E}[A] > \mathbb{E}[P]$ ;
- test unilatéral : $H_1 : \mathbb{E}[A] < \mathbb{E}[P]$.

Le test se construit sur les différences individuelles entre les deux mesures,

$$Z_i = A_i - P_i$$

qui forment $n$ variables indépendantes et identiquement distribuées, d'espérance

$$\mathbb{E}[Z] = \mathbb{E}[A] - \mathbb{E}[P] .$$

Sous $H_0$, cette espérance s'annule. Le test se ramène alors à un [[Test de comparaison d'une moyenne à une valeur donnée|test de comparaison d'une moyenne à une valeur donnée]] portant sur les $Z_i$, avec la valeur de référence $m_0 = 0$ : on confronte la [[Moyenne empirique|moyenne empirique]] $\overline{Z}$ des différences à $0$ au moyen de sa [[Statistique de test|statistique de test]].

# Interprétation

Le test répond à la question de savoir s'il existe une différence statistique entre les $A_i$ et les $P_i$, c'est-à-dire si un traitement ou un algorithme a un effet. Le passage aux différences $Z_i$ en est la clé : chaque individu étant comparé à lui-même, la variabilité propre aux individus affecte de la même façon la mesure avant et la mesure après, et disparaît de la différence, qui ne retient que la variation attribuable au traitement.

# Remarque

Des échantillons appariés ne sont pas deux échantillons indépendants : les $A_i$ et les $P_i$ proviennent des mêmes individus, alors que le [[Test de Student d'égalité de deux moyennes]] compare deux groupes d'individus distincts. Analyser des données appariées comme deux échantillons indépendants méconnaît le lien entre $A_i$ et $P_i$ et fausse le risque du test.

La démarche suivie reste celle de la [[Méthodologie d'un test d'hypothèse]] : définition des hypothèses, choix d'une statistique dont la loi sous $H_0$ est connue, fixation du seuil, puis décision.
