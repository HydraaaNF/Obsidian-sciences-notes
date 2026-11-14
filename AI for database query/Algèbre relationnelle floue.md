# Définition
L'**algèbre relationnelle floue** généralise l'algèbre relationnelle aux [[Relation floue|relations floues]]. Elle sert de base à SQLf, l'extension floue de SQL.

# Propriétés
Deux familles d'opérateurs :
- les **opérateurs ensemblistes** : [[Produit cartésien de relations floues]], [[Union de relations floues]], [[Intersection de relations floues]], [[Différence de relations floues]] ;
- les **opérateurs relationnels** : [[Sélection floue]], [[Projection floue]], [[Jointure floue]], [[Division de relations floues]] (voir aussi [[Division relationnelle]] pour le cas classique).

Une relation classique étant une relation floue dont tous les n-uplets ont le degré $1$, ces opérateurs redonnent les opérateurs classiques sur les relations classiques.

# Exemple
Deux relations : $\text{Emp}(\#e, \text{nom}, \text{salaire}, \text{prime}, \text{âge}, \text{dep})$ et $\text{Dep}(\#d, \text{budget}, \text{ville})$, où l'attribut $\text{dep}$ de $\text{Emp}$ est un numéro de département $\#d$.

Requête : *trouver les départements (\#d) qui ont un budget élevé et où ne travaille aucun employé de moins de 40 ans dont le salaire est moyen.*

Dans $\text{Emp}$, le degré entre parenthèses à côté d'un salaire est le degré auquel ce salaire est *moyen*. Dans $\text{Dep}$, le degré entre parenthèses à côté d'un budget est le degré auquel ce budget est *élevé*.

$\text{Emp}$ :

| \#e | nom | salaire | prime | âge | dep |
| --- | --- | --- | --- | --- | --- |
| 19 | Dupont | 2500 (0,1) | 1300 | 33 | 23 |
| 76 | Martin | 4000 (0,9) | 2600 | 42 | 23 |
| 26 | Durant | 3000 (0,4) | 1500 | 37 | 23 |
| 12 | Dubois | 2300 (0,1) | 900 | 39 | 17 |

$\text{Dep}$ :

| \#d | budget | ville |
| --- | --- | --- |
| 17 | 200k (1) | Toulouse |
| 23 | 150k (0,2) | Paris |

Expression en algèbre relationnelle floue :

$$
\pi_{\#d}\big(\sigma_{\text{budget élevé}}(\text{Dep})\big) \setminus \pi_{\text{dep}}\big(\sigma_{\text{âge} < 40 \ \wedge\ \text{salaire moyen}}(\text{Emp})\big)
$$

Évaluation sur cette base de données :
- $\pi_{\#d}\big(\sigma_{\text{budget élevé}}(\text{Dep})\big) = \{1/17,\; 0{,}2/23\}$
- $\pi_{\text{dep}}\big(\sigma_{\text{âge} < 40 \ \wedge\ \text{salaire moyen}}(\text{Emp})\big) = \{0{,}4/23,\; 0{,}1/17\}$ (Martin est exclu car $42 \geq 40$ ; le département 23 conserve $\max(0{,}1;\, 0{,}4) = 0{,}4$)
- différence : $\{1/17,\; 0{,}2/23\} \setminus \{0{,}1/17,\; 0{,}4/23\} = \{\min(1;\, 1 - 0{,}1)/17,\; \min(0{,}2;\, 1 - 0{,}4)/23\} = \{0{,}9/17,\; 0{,}2/23\}$
