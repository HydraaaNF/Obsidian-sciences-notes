# Définition

Une **chaîne de Markov à temps discret** est un [[Propriété de Markov|processus de Markov]] dont la variable $X_t$ est discrète ; $X_t$ indique l'état du processus. L'ensemble des valeurs possibles de $X_t$, noté $[1, N]$, est l'**espace d'états** (voir [[Espaces d'états et d'indices d'un processus]]).

Pour une chaîne de Markov homogène (d'ordre 1), les paramètres du modèle se résument dans une matrice de transition $A$ où

$$\mathbb{P}[X_t = j \mid X_{t-1} = i] = a_{ij} \qquad \forall t$$

avec $\sum_j a_{ij} = 1$.

# Exemple

Trois états : pluvieux, nuageux et ensoleillé, numérotés respectivement $1$, $2$ et $3$. Le temps de demain ne dépend que de celui d'aujourd'hui, selon la matrice de transition

$$A = \begin{pmatrix} 0{,}4 & 0{,}3 & 0{,}3 \\ 0{,}2 & 0{,}6 & 0{,}2 \\ 0{,}1 & 0{,}1 & 0{,}8 \end{pmatrix}$$

Initialement, les trois états sont équiprobables :

$$\pi = \{1/3,\ 1/3,\ 1/3\}$$

Quelle est la probabilité de la séquence « ensoleillé ensoleillé ensoleillé pluvieux pluvieux nuageux ensoleillé », c'est-à-dire $\mathbf{x} = \{3, 3, 3, 1, 1, 2, 3\}$ ?

$$\begin{aligned} \mathbb{P}[\mathbf{x}] &= \mathbb{P}[3]\mathbb{P}[3 \mid 3]^2\mathbb{P}[1 \mid 3]\mathbb{P}[1 \mid 1]\mathbb{P}[2 \mid 1]\mathbb{P}[3 \mid 2] \\ &= \pi_3 a_{33}^2 a_{31} a_{11} a_{12} a_{23} \\ &= 0{,}000512 \end{aligned}$$

Sachant qu'aujourd'hui est ensoleillé, la probabilité que le temps reste ensoleillé pendant $d$ jours est

$$\mathbf{x} = \underbrace{\{i, \dots, i, j \neq i\}}_{d \text{ fois}}$$

$$\begin{aligned} \mathbb{P}[\mathbf{x} \mid X_1 = i] &= \mathbb{P}[i \mid i]^{d-1} \left( \sum_{j \neq i} \mathbb{P}[j \mid i] \right) \\ &= a_{ii}^{d-1} (1 - a_{ii}) \end{aligned}$$

# Remarque

Une chaîne de Markov à temps discret est l'équivalent à temps discret de la [[Chaîne de Markov à temps continu]]. La matrice de transition et la loi initiale déterminent la loi de toute trajectoire ; la [[Génération d'une chaîne de Markov]] en décrit la simulation. Lorsque les états de la chaîne ne sont pas observables directement, le modèle s'étend au [[Modèle de Markov caché]].

La valeur exacte de la probabilité de la séquence ci-dessus est $0{,}000512$, et non $0{,}0004608$ : le produit $\pi_3 a_{33}^2 a_{31} a_{11} a_{12} a_{23}$ vaut $\frac{1}{3} \times 0{,}001536 = 0{,}000512$.
