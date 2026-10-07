# Définition

Un **champ aléatoire de Markov** est un [[Processus stochastique|champ aléatoire]] indexé par un ensemble de sites $S$, à valeurs dans $E$, pour lequel la [[Propriété de Markov|propriété de Markov]] prend la forme suivante :

$$\mathbb{P}[X_s = x_s \mid X_{S \setminus s} = x_{S \setminus s}] = \mathbb{P}[X_s = x_s \mid X_{V_s} = x_{V_s}]$$

- pour tout $s \in S$, $x_s \in E$ ;
- espace d'échantillonnage : $\Omega = E^{|S|}$ ;
- système de voisinage : $V$, où $V_s$ désigne le voisinage du site $s$ ;
- ensemble des cliques : $c \in \mathcal{C}$.

# Interprétation

Conditionnellement aux valeurs prises par tous les autres sites du champ, la valeur d'un site ne dépend que de celles de son voisinage : la propriété de Markov traduit des interactions locales entre sites. Sur une grille, le voisinage d'un site est formé de ses quatre plus proches voisins (nord, sud, est, ouest).

# Exemple

Un exemple de champ aléatoire de Markov est donné par la probabilité conditionnelle d'un site sachant son voisinage :

$$\mathbb{P}[X_s \mid X_{V_s}] = \frac{\exp\left(\alpha x_s + \sum_{r \in V_s} \beta x_s x_r\right)}{1 + \exp\left(\alpha x_s + \sum_{r \in V_s} \beta x_s x_r\right)}$$

Les simulations d'un tel champ sur une grille montrent une réalisation du champ ainsi que l'évolution de son aimantation au cours de la simulation.

# Remarque

La loi d'un champ aléatoire de Markov s'écrit sous la forme d'une [[Distribution de Gibbs]], définie à partir d'une fonction d'énergie décomposée sur les cliques $\mathcal{C}$.
