#dmv-xai

# Définition

Un **jeu coopératif** est un couple formé d'un ensemble de joueurs et d'une fonction qui attribue une valeur à chaque coalition de joueurs, c'est-à-dire à chaque sous-ensemble de cet ensemble.

Dans l'explication d'un modèle, les joueurs sont les variables d'entrée, réunies dans l'ensemble $F$ : la valeur d'une coalition $S \subseteq F$ est la prédiction du modèle lorsque seules les variables de $S$ sont renseignées, les variables absentes étant ramenées à une valeur de référence.

La **valeur de Shapley** d'une variable $i$ est sa contribution marginale moyenne sur toutes les coalitions possibles des autres variables : on ajoute $i$ à une coalition, on mesure la variation de la prédiction, et on moyenne cette variation sur les coalitions.

# Propriétés

La valeur de Shapley de la variable $i$ s'écrit

$$
\phi_i = \sum_{S \subseteq F \setminus \{i\}} \frac{|S|!\,\left(|F|-|S|-1\right)!}{|F|!} \left[ f_{S \cup \{i\}}\left(x_{S \cup \{i\}}\right) - f_S(x_S) \right]
$$

Le facteur $\dfrac{|S|!\,\left(|F|-|S|-1\right)!}{|F|!}$ est le poids de la coalition $S$. Il ne dépend que du nombre de variables de $S$ et du nombre total de variables : c'est la proportion des ordres d'arrivée des variables dans lesquels $S$ forme exactement l'ensemble des variables déjà présentes quand $i$ arrive.

La valeur est caractérisée par quatre axiomes.

- **efficacité** : les valeurs se partagent exactement l'écart entre la prédiction sur la coalition complète et la prédiction sur la coalition vide,
- **symétrie** : deux variables qui apportent la même contribution marginale à toute coalition reçoivent la même valeur,
- **nullité** : une variable dont la contribution marginale est nulle pour toute coalition reçoit la valeur nulle,
- **additivité** : les valeurs d'une somme de deux jeux sont la somme des valeurs de chaque jeu.

L'efficacité s'écrit

$$
\sum_{i \in F} \phi_i = f_F(x_F) - f_\varnothing(x_\varnothing)
$$

# Exemple

Le modèle prédit la survie d'un passager à partir de trois variables : le genre, la classe du billet et l'âge. La coalition complète $F$ réunit `Gender=♂`, `PClass=3rd` et `Age=14`. On calcule la valeur de Shapley de la variable $i$ = `Gender=♂`, les autres variables formant l'ensemble $\{\text{PClass}, \text{Age}\}$.

| Coalition $S$ | $f(S)$ | $f(S \cup \{i\})$ | $\Delta$ | Poids | Contribution |
| --- | --- | --- | --- | --- | --- |
| $\varnothing$ | survit | décède | 1 | $1/3$ | $1/3$ |
| $\{\text{PClass}=3^{\text{rd}}\}$ | décède | décède | 0 | $1/6$ | $0$ |
| $\{\text{Age}=14\}$ | survit | survit | 0 | $1/6$ | $0$ |
| $\{\text{Age}=14,\ \text{PClass}=3^{\text{rd}}\}$ | survit | décède | 1 | $1/3$ | $1/3$ |

Les colonnes $f(S)$ et $f(S \cup \{i\})$ donnent la classe prédite par le modèle selon les variables renseignées, $\Delta$ la variation obtenue en ajoutant la variable $i$.

La somme pondérée des contributions donne la valeur de Shapley

$$
\phi_{\text{Gender}} = \frac{1}{3} \times 1 + \frac{1}{6} \times 0 + \frac{1}{6} \times 0 + \frac{1}{3} \times 1 = \frac{2}{3} \approx 0{,}67
$$

```chart
type: bar
labels: ["coalition vide", "PClass seule", "Age seul", "Age et PClass"]
series:
  - title: "Contribution marginale de Gender=♂"
    data: [1, 0, 0, 1]
```

# Remarque

Les modèles ne savent pas traiter des variables incomplètes : une coalition ne s'évalue pas sur une entrée partielle. Les variables absentes de $S$ sont donc fixées à une valeur de référence, et la prédiction $f_S(x_S)$ s'obtient sur l'entrée complétée de cette façon.

La valeur de Shapley est une **moyenne pondérée** des contributions marginales, pas leur moyenne arithmétique. Sur trois variables, la coalition vide et la coalition des deux autres variables pèsent chacune $1/3$, tandis que les deux coalitions d'une seule variable pèsent $1/6$ : les coalitions de tailles différentes ne comptent pas pour le même nombre d'ordres d'arrivée. Prendre la moyenne arithmétique des quatre contributions, soit $0{,}5$ ici, donne un nombre qui ne coïncide pas avec la formule ci-dessus et ne respecte pas l'efficacité ; la forme non pondérée est une erreur fréquente.

La coalition complète est l'ensemble $F$ des variables : l'appeler par une seconde lettre, $N$ par exemple, fait croire à un second ensemble, alors que c'est le même.

La valeur porte sur une instance donnée : additionnée sur les variables, elle reconstruit l'écart entre la prédiction de cette instance et la prédiction de référence. Cette construction est celle que reprend [[SHAP]] pour attribuer une prédiction aux variables, dans la ligne des [[Méthodes d'attribution par gradients]] et plus largement des méthodes d'[[Explication locale]]. Moyennée sur un échantillon d'instances, elle fournit une [[Importance des variables par agrégation]].
