# Définition

Une **chaîne de Markov d'ordre N** est un [[Processus stochastique|processus]] $(X_t)_{t = 1, \ldots, T}$ dont la loi de chaque état, conditionnellement à tout le passé, ne dépend que des $N$ états précédents :

$$\mathbb{P}[X_t \mid X_{t-1}, \ldots, X_1] = \mathbb{P}[X_t \mid X_{t-1}, \ldots, X_{t-N}]$$

# Propriétés

**Probabilité jointe.** La probabilité d'une trajectoire $(X_1, \ldots, X_T)$ se factorise en produit de probabilités conditionnelles successives :

$$\mathbb{P}[X_1, \ldots, X_T] = \mathbb{P}[X_1]\mathbb{P}[X_2 \mid X_1]\mathbb{P}[X_3 \mid X_2, X_1] \cdots \mathbb{P}[X_T \mid X_{T-1}, \ldots, X_1]$$

**Processus de Markov d'ordre N.** La factorisation s'écrit alors :

$$\mathbb{P}[X_1, \ldots, X_T] = \mathbb{P}[X_1]\mathbb{P}[X_2 \mid X_1]\mathbb{P}[X_3 \mid X_2, X_1] \cdots \mathbb{P}[X_T \mid X_{T-1}, \ldots, X_{T-N}]$$

# Remarque

Cette définition généralise la [[Propriété de Markov]] : le conditionnement porte non plus sur le seul dernier état, mais sur les $N$ états précédents. Pour $N = 1$, le conditionnement se réduit à l'état précédent et l'on retrouve une [[Chaîne de Markov à temps discret]]. Le [[Modèle de Markov pour les textes]] en est une application.
