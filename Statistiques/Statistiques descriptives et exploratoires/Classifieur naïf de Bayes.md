# Définition

La classification (l'un des [[Problèmes d'apprentissage statistique|problèmes d'apprentissage statistique]]) consiste à prédire un label discret $y$ à partir de données observées $x$. La décision bayésienne (optimale) associe à $x$ le label

$$\hat{y} = \arg \max_y p(y|x) = \arg \max_y p(x,y) = \arg \max_y p(x|y)p(y)$$

Le **classifieur naïf de Bayes** suppose que toutes les observations $(x_1, \dots, x_n)$ sont (conditionnellement) indépendantes sachant le label :

$$p(\mathbf{x}, y) = p(y) \prod_{i=1}^n p(x_i|y)$$

# Modèle

Pour un label $y$ et trois observations $x_1, x_2, x_3$, la règle de décision du classifieur naïf de Bayes s'écrit

$$\arg \max_c \mathbb{P}[Y = c | x_1, x_2, x_3] = \arg \max_c \mathbb{P}[Y = c] \prod_{i=1}^3 \mathbb{P}[X_i = x_i | Y = c]$$

# Interprétation

Sous l'hypothèse d'indépendance conditionnelle, la loi jointe $p(\mathbf{x}, y)$ se factorise en la loi du label $p(y)$ et les lois conditionnelles $p(x_i|y)$ : le graphe de dépendances prend la forme d'une structure en étoile, où le label $Y$ est relié directement à chaque observation $X_i$.

# Exemple

On souhaite prévoir la météo du jour. Le label $y$ est la météo du jour (ensoleillé, pluvieux, nuageux) et les observations $x$ sont la température, l'humidité, etc. La météo du jour peut dépendre de la météo de la veille ; il reste à choisir un modèle (une loi) pour $p(y)$ et pour $p(x|y)$.

# Remarque

Le classifieur naïf de Bayes est un cas particulier de la [[Règle de décision de Bayes]] : il applique la décision bayésienne optimale sous l'hypothèse d'indépendance conditionnelle des observations. Voir aussi les [[Règles de décision optimales]].
