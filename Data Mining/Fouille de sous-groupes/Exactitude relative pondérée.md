#dmv-subgroup_discovery

# Définition

L'exactitude relative pondérée (en anglais *Weighted Relative Accuracy*, WRAcc) est une mesure de qualité d'un sous-groupe $P$ pour une cible binaire :

$$WRAcc(P) = \frac{n}{N} \cdot (t_P - t_{all}) = \frac{n}{N} \cdot \left( \frac{a}{n} - \frac{a + c}{N} \right)$$

Les effectifs $a$, $c$, et les totaux $n$, $N$, sont ceux de la [[Matrice de confusion d'un sous-groupe]] : $n = a+b$ est l'étendue du sous-groupe, $N = a+b+c+d$ la population entière, $t_P = a/n$ le taux de présence de la cible dans le sous-groupe et $t_{all} = (a+c)/N$ ce taux sur toute la population.

# Interprétation

La mesure quantifie l'« unusualness » du sous-groupe : intuitivement, c'est la couverture du sous-groupe multipliée par le gain d'exactitude.

Le facteur $n/N$ pondère l'écart $t_P - t_{all}$ par la part de la population que le sous-groupe couvre : il l'amplifie dans les deux sens, un sous-groupe large mais moins riche en cible que la moyenne obtenant une valeur négative de plus grande amplitude.

Le facteur $t_P - t_{all}$ est le gain d'exactitude : il est positif quand la cible est plus fréquente dans le sous-groupe que dans la population entière, négatif quand elle y est plus rare.

# Exemple

Cible binaire : `Income = 'High'`. Le jeu de données compte 16 individus décrits par `Income` (cible), `Sex`, `Age`, `Education level`, `Married` et `Has Children`.

| Income | Sex | Age | Education level | Married | Has Children |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **High** | M | >50 | High | Y | Y |
| **High** | M | >50 | Medium | Y | Y |
| **High** | F | 40-50 | Medium | Y | Y |
| **High** | M | 40-50 | Low | N | Y |
| Medium | M | 30-40 | Medium | Y | Y |
| Medium | M | >50 | High | Y | N |
| Low | M | <30 | High | Y | N |
| Medium | F | <30 | Medium | Y | N |
| Low | F | 40-50 | Low | Y | N |
| Low | M | 40-50 | Medium | N | N |
| Medium | F | >50 | Medium | N | N |
| Low | F | <30 | Low | N | N |
| Low | F | 30-40 | Medium | N | N |
| Low | F | 40-50 | Low | N | N |
| Low | M | <30 | Low | N | N |
| Medium | F | 30-40 | Medium | N | N |

Les quatre premiers individus, ceux dont `Income` vaut `High` (mis en gras dans le tableau), sont les seuls à compter dans $a$ et dans $c$ : ils fixent le taux global $t_{all} = 4/16$.

Sous-groupe `Sex = 'M'` et `Age < 30` : $n = 2$, $a = 0$, d'où

$$\text{WRAcc} = 2/16 \times (0/2 - 4/16) = -0.03125$$

Sous-groupe `Married = 'Y'` : $n = 8$, $a = 3$, d'où

$$\text{WRAcc} = 8/16 \times (3/8 - 4/16) = 0.0625$$

Sous-groupe `HasChildren = 'Y'` : $n = 5$, $a = 4$, d'où

$$\text{WRAcc} = 5/16 \times (4/5 - 4/16) = 0.17$$

# Remarque

L'exactitude relative pondérée est une [[Fonction de qualité d'un sous-groupe]] particulière, définie pour une cible binaire.

La [[Fonction de qualité pour cible numérique]] en reprend la structure : les pourcentages de présence de la cible y sont remplacés par la moyenne de la valeur cible.

Le premier sous-groupe de l'exemple illustre le cas défavorable : il ne contient aucune cible ($a = 0$), donc $t_P = 0$ et l'écart $t_P - t_{all}$ est négatif ; sa faible couverture ($2/16$) en atténue l'amplitude, d'où une valeur négative proche de zéro.
