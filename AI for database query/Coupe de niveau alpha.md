# Définition
La **coupe de niveau $\alpha$** (ou **$\alpha$-coupe**) d'un [[Ensemble flou]] $E$ est l'ensemble **classique** des éléments dont le degré d'appartenance atteint au moins $\alpha$ :

$$
E_\alpha = \{x \in X \mid \mu_E(x) \geq \alpha\}
$$

La **coupe de niveau $\alpha$ stricte** utilise une inégalité stricte :

$$
E_{\bar{\alpha}} = \{x \in X \mid \mu_E(x) > \alpha\}
$$

# Propriétés
- **Décroissance pour l'inclusion** : $\alpha_1 > \alpha_2 \implies E_{\alpha_1} \subset E_{\alpha_2}$.
- $E_1 = \operatorname{noyau}(E)$ (voir [[Noyau d'un ensemble flou]]).
- $E_{\bar{0}} = \operatorname{supp}(E)$ (voir [[Support d'un ensemble flou]]).
- Avec le couple [[Norme et conorme de Zadeh]], les coupes sont compatibles avec l'intersection et l'union : $(E \cap F)_\alpha = E_\alpha \cap F_\alpha$ et $(E \cup F)_\alpha = E_\alpha \cup F_\alpha$.

# Interprétation
Les coupes de niveau sont **emboîtées** :

$$
E_1 \subset E_{0{,}9} \subset \ldots \subset E_{0{,}1}
$$

Un ensemble flou $E$ peut être **entièrement défini** par la collection de ses coupes de niveau. L'[[Interprétation de Yager par coupes de niveau α]] s'appuie sur cette propriété.

# Exemple
**Ensemble flou *young*.** Pour $\mu_{\text{young}}$ égale à $1$ jusqu'à $30$ ans, puis décroissant linéairement jusqu'à $0$ à $45$ ans, la coupe de niveau $\alpha = 0{,}5$ est $E_{0{,}5} = [0,\; 37{,}5]$ : $37{,}5$ est l'âge où le degré vaut $0{,}5$.

```chart
type: line
labels: ["0", "2.5", "5", "7.5", "10", "12.5", "15", "17.5", "20", "22.5", "25", "27.5", "30", "32.5", "35", "37.5", "40", "42.5", "45", "47.5", "50", "52.5", "55", "57.5", "60"]
series:
  - title: μ young
    data: [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0.83, 0.67, 0.5, 0.33, 0.17, 0, 0, 0, 0, 0, 0, 0]
  - title: α = 0,5
    data: [0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5]
beginAtZero: true
```

**Ensemble fini.** Avec $E = \{1/a,\; 0{,}7/c,\; 0{,}2/e,\; 0{,}3/f,\; 0{,}6/h,\; 0{,}7/j,\; 0{,}9/k\}$ :
- $E_{0{,}3} = \{a, c, f, h, j, k\}$
- $E_{0{,}5} = \{a, c, h, j, k\}$
- $E_{0{,}6} = \{a, c, h, j, k\}$ (l'inégalité est large : $\mu_E(h) = 0{,}6 \geq 0{,}6$)

La coupe **stricte** $E_{\bar{0{,}6}}$ vaut en revanche $\{a, c, j, k\}$.
