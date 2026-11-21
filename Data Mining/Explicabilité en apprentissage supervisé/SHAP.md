#dmv-xai

# Définition

SHAP, pour SHapley Additive exPlanations, applique la théorie des jeux pour quantifier l'importance des variables d'un modèle entraîné : chaque variable reçoit sa valeur de Shapley, contribution marginale moyenne sur toutes les coalitions de variables possibles.

C'est donc une application de la [[Valeur de Shapley]] à un modèle déjà entraîné, et une méthode d'[[Explication locale]] d'une prédiction.

$$\phi_i = \sum_{S \subseteq F \setminus \{i\}} \frac{|S|! \, \left(|F| - |S| - 1\right)!}{|F|!} \left[ f_{S \cup \{i\}}\left(x_{S \cup \{i\}}\right) - f_S(x_S) \right]$$

# Modèle

Un modèle d'apprentissage ne sait pas évaluer une instance dont certaines variables sont absentes.

La convention retenue consiste à remplacer les variables absentes par une valeur de référence : la fonction $f_S$ est alors définie pour toute coalition $S$ de variables, et $f_S(x_S)$ désigne la prédiction obtenue en ne conservant que les variables de $S$.

La prédiction se décompose autour d'une valeur de base, l'espérance $\mathbb{E}[f(X)]$ de la prédiction, à laquelle s'ajoutent les contributions des variables.

# Propriétés

Le modèle d'attribution de SHAP garantit :

- l'exactitude locale (local accuracy) ;
- la nullité de la contribution d'une variable absente de l'instance (missingness) ;
- la linéarité (linearity) ;
- l'effet nul des variables sans influence (null effects).

L'exactitude locale s'écrit comme une décomposition additive de la prédiction, la somme des contributions et de la valeur de base redonnant la prédiction du modèle :

$$f(x) = \phi_0 + \sum_{i \in F} \phi_i$$

avec $\phi_0 = \mathbb{E}[f(X)]$.

# Algorithme

KernelSHAP, version agnostique du modèle :

- échantillonner des coalitions de variables ;
- ajuster une régression linéaire pondérée sur les valeurs de $f_S$ ainsi obtenues.

Des variantes dédiées existent, DeepSHAP et TreeSHAP.

# Exemple

**Influence de Gender=♂ sur une prédiction de survie.** Les coalitions ne contenant pas la variable étudiée sont comparées aux coalitions qui l'ajoutent ; la contribution marginale $\Delta$ vaut la différence des deux prédictions, et la valeur de Shapley en est la moyenne pondérée par l'ordre d'arrivée des joueurs.

| Coalition $S$ | $f(S)$ | $f(S \cup \{i\})$ | $\Delta$ |
|---|---|---:|---:|
| $\varnothing$ | survit | décède | 1 |
| $\{\text{PClass}=3^{\text{rd}}\}$ | décède | décède | 0 |
| $\{\text{Age}=14\}$ | survit | survit | 0 |
| $\{\text{Age}=14,\ \text{PClass}=3^{\text{rd}}\}$ | survit | décède | 1 |

La valeur de Shapley de Gender=♂ est la moyenne pondérée de ces contributions : elle vaut $2/3 \approx 0{,}67$.

La coalition complète réunit Gender=♂, PClass=$3^{\text{rd}}$ et Age=14 ; évaluée par la boîte noire, elle prédit la survie.

**Attribution d'un prix de maison.** Les contributions des variables s'ajoutent à la valeur de base pour former la prédiction.

| Variable | Valeur | Contribution SHAP |
|---|---:|---:|
| MedInc | 8.325 | $+1.83$ |
| Longitude | −122.23 | $+0.64$ |
| Latitude | 37.88 | $-0.29$ |
| AveRooms | 6.984 | $+0.14$ |
| HouseAge | 41 | $+0.09$ |
| Population | 322 | $-0.07$ |
| AveOccup | 2.556 | $+0$ |
| AveBedrms | 1.024 | $-0$ |

Valeur de base :

$$\mathbb{E}[f(X)] = 2.068$$

Prédiction :

$$f(x) = 4.413$$

**Graphique en cascade sur le prix de logements.** Chaque barre horizontale porte la valeur de la variable et sa contribution, positives et négatives se compensant de la valeur de base jusqu'à la prédiction.

| Variable | Valeur | Contribution |
|---|---:|---:|
| LSTAT | 4.98 | $+5.79$ |
| RM | 6.575 | $-2.17$ |
| NOX | 0.538 | $-0.73$ |
| RAD | 1 | $-0.49$ |
| TAX | 296 | $-0.47$ |
| CRIM | 0.006 | $-0.43$ |
| DIS | 4.09 | $-0.41$ |
| PTRATIO | 15.3 | $+0.26$ |
| AGE | 65.2 | $+0.19$ |
| 4 autres variables | | $-0.04$ |

Prédiction :

$$f(x) = 24.019$$

Valeur de base :

$$\mathbb{E}[f(X)] = 22.533$$

**Graphique de dépendance.** Une variable est portée en abscisse et sa contribution SHAP en ordonnée, une observation par point ; le nuage obtenu montre comment la contribution varie avec la valeur prise par la variable.

**Graphique de résumé.** Les variables sont rangées par importance décroissante, chaque observation étant un point placé sur l'axe de sa contribution et coloré selon la valeur de la variable ; il condense les attributions d'un échantillon d'instances.

# Remarque

D'autres méthodes d'attribution reposent sur moins de coalitions ou moins d'hypothèses. Dans les formules qui suivent, $\mathcal{N}$ et $F$ désignent le même ensemble de variables.

Equal Surplus :

$$\varphi_j^{ES}(\mathbf{x}, f_i) = f_i(\{j\}) + \frac{f_i(N) - \sum_{k=1}^{N} f_i(\{k\})}{N}$$

Extreme Feature Coalitions :

$$\varphi_j(\mathbf{x}, f_i) = w_i f_i(\{j\}) + (1 - w_i)\left(-f_i(\mathcal{N} \setminus \{j\})\right)$$

Layer-1 SHAP$^{(+)}$ :

$$\phi_j = \tilde{\phi}_j + \frac{1}{M}\left(f(N) - f(\varnothing) - \sum_{i=1}^{M} \tilde{\phi}_i\right)$$

où, pour tout $i$,

$$\tilde{\phi}_i = \frac{f(\{i\}) - f(\varnothing) + f(N) - f(N \setminus \{i\})}{2}$$

Les valeurs de Hamiache-Navarro s'ajoutent à ces alternatives.

Ces variantes n'emploient qu'un petit nombre de coalitions. Extreme Feature Coalitions se restreint à la coalition complète $\mathcal{N}$, à son complément $\mathcal{N} \setminus \{j\}$ et au singleton $\{j\}$.

Autour de l'instance à expliquer, les couches de coalitions se lisent ainsi : la couche 1 réunit le singleton $\{i\}$ et son complément $\mathcal{N} \setminus \{i\}$, la couche 2 les paires $\{i, j\}$ et $\mathcal{N} \setminus \{i, j\}$. La formule de Layer-1 SHAP$^{(+)}$ n'emploie que les coalitions de la couche 1, complétées par les coalitions extrêmes $\varnothing$ et $\mathcal{N}$.

La valeur de Shapley est une moyenne pondérée des contributions marginales, pas leur moyenne arithmétique : sur trois variables, la coalition vide et la coalition des deux autres variables pèsent chacune $1/3$, contre $1/6$ pour les coalitions d'une seule variable. Prendre la moyenne arithmétique des quatre contributions, soit $0{,}5$ ici, donne un nombre différent de $2/3$ : les coalitions de tailles différentes ne comptent pas pour le même nombre d'ordres d'arrivée. Le calcul pondéré est détaillé dans [[Valeur de Shapley]].

L'approche contrefactuelle atteint le même but par une modification d'entrée plutôt que par une attribution, voir l'[[Explication contrefactuelle]] ; les attributions obtenues par rétropropagation du gradient en sont une autre voie, voir les [[Méthodes d'attribution par gradients]].
