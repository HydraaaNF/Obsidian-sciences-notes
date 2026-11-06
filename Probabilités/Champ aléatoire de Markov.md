# Définition

Un **champ aléatoire de Markov** est un [[Processus stochastique|champ aléatoire]] indexé par les sites $s$ d'un ensemble $S$, à valeurs dans un espace d'états $E$, pour lequel la [[Propriété de Markov|propriété de Markov]] prend la forme **locale** suivante : pour tout site $s \in S$,

$$\mathbb{P}[X_s = x_s \mid X_{S \setminus s} = x_{S \setminus s}] = \mathbb{P}[X_s = x_s \mid X_{V_s} = x_{V_s}]$$

Les notations sont les suivantes :
- $s \in S$ : un site du réseau, $S$ étant l'ensemble des sites ;
- $x_s \in E$ : l'état du site $s$, à valeurs dans l'espace d'états $E$ ;
- $x_{S \setminus s}$ : les états de tous les sites autres que $s$ ;
- $\Omega = E^{|S|}$ : l'espace d'états du champ, une configuration $x$ du champ étant un point de $\Omega$ ;
- $V$ : le système de voisinage, $V_s$ étant l'ensemble des sites voisins de $s$ ;
- $c \in \mathcal{C}$ : une clique du réseau, c'est-à-dire un ensemble de sites deux à deux voisins, $\mathcal{C}$ désignant l'ensemble des cliques.

# Interprétation

La propriété est **locale** : sachant les états de ses voisins, l'état d'un site ne dépend plus du reste du réseau. Connaître en plus les états des sites éloignés n'apporte aucune information supplémentaire sur $X_s$, toute la dépendance passe par le voisinage $V_s$. Conditionnellement aux valeurs prises par tous les autres sites du champ, la valeur d'un site ne dépend donc que de celles de son voisinage.

Le voisinage dépend du réseau considéré. Sur une grille, le site $s$ a pour voisins les quatre sites adjacents horizontalement et verticalement, soit nord, sud, est et ouest ; les sites placés en diagonale, plus éloignés, ne font pas partie de $V_s$.

# Exemple

Un exemple de champ aléatoire de Markov sur un réseau à deux états prend pour loi conditionnelle de chaque site une régression logistique sur les états de ses voisins :

$$\mathbb{P}[X_s \mid X_{V_s}] = \frac{\exp\left(\alpha x_s + \sum_{r \in V_s} \beta x_s x_r\right)}{1 + \exp\left(\alpha x_s + \sum_{r \in V_s} \beta x_s x_r\right)}$$

Le terme $\alpha x_s$ traduit l'effet propre du site, et chaque terme $\beta x_s x_r$ le couplage avec un voisin $r$ : plus le coefficient $\beta$ est grand en valeur absolue, plus l'état d'un site est fortement lié à celui de ses voisins.

Les simulations d'un tel champ sur une grille montrent une réalisation du champ ainsi que l'évolution de son aimantation au cours de la simulation, avec un curseur de température et une courbe de magnétisation moyenne. D'une capture à l'autre, la configuration passe d'un arrangement désordonné des deux états à un arrangement où se forment des domaines de sites voisins de même état, la magnétisation moyenne restant proche de zéro.

# Remarque

La loi d'un champ aléatoire de Markov se factorise sur les cliques du réseau : elle s'écrit comme une [[Distribution de Gibbs]], définie à partir d'une fonction d'énergie décomposée sur les cliques $\mathcal{C}$, dont le facteur de normalisation assure que la probabilité totale sur $\Omega$ vaut $1$.

La propriété de Markov locale ne suppose aucune direction dans le réseau, et une clique peut regrouper plus de deux sites : la dépendance n'est pas limitée à des paires de voisins.

# Liens avec d'autres lois

Le champ aléatoire de Markov est la version spatiale de la [[Propriété de Markov]] : la loi conditionnelle en un site n'y dépend que d'un voisinage, là où celle d'un processus de Markov ne dépend que de son état présent. Contrairement à une [[Chaîne de Markov à temps discret]], dont l'indice est un instant, l'indice est ici un site du réseau.

Un champ aléatoire de Markov observé à travers une version bruitée de ses états donne un [[Champ de Markov caché]] : le champ latent y suit la loi d'un champ aléatoire de Markov, et les observations sont conditionnellement indépendantes sachant ce champ.
