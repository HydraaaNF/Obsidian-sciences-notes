La **coupe de niveau $\alpha$** (ou **$\alpha$-coupe**) d'un [[Ensemble flou]]
$E$ est l'ensemble **classique** des éléments dont le degré d'appartenance
atteint au moins $\alpha$ :

$$
E_\alpha = \{x \mid x \in X \text{ et } \mu_E(x) \geq \alpha\}
$$

La **coupe de niveau $\alpha$ stricte** utilise une inégalité stricte :

$$
E_{\bar{\alpha}} = \{x \mid x \in X \text{ et } \mu_E(x) > \alpha\}
$$

### Propriétés
- **Décroissance pour l'inclusion** :
  $\alpha_1 > \alpha_2 \implies E_{\alpha_1} \subset E_{\alpha_2}$
- $E_1 = \text{noyau}(E)$ — voir [[Noyau d'un ensemble flou]]
- $E_{\bar{0}} = \text{supp}(E)$ — voir [[Support d'un ensemble flou]]

### Emboîtement
Les coupes de niveau sont **emboîtées** les unes dans les autres :

$$
E_1 \subset E_{0{,}9} \subset \ldots \subset E_{0{,}1}
$$

> [!important]
> Un ensemble flou $E$ peut être **entièrement défini** par la collection de ses
> coupes de niveau. C'est un moyen de ramener un ensemble flou à une famille
> d'ensembles classiques, et donc d'y appliquer les résultats de la théorie
> classique.