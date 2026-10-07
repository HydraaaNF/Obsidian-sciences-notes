# Définition

L'**estimation non biaisée du risque** consiste à découper les données en deux ensembles distincts :

- le premier ensemble sert à déterminer $\hat{\theta}$, le modèle obtenu par [[Principe de minimisation du risque empirique|minimisation du risque empirique]] ;
- le second ensemble sert à estimer le [[Risque et risque empirique|risque]] de ce modèle :

$$\mathbb{E}_z[L(z, \hat{\theta})]$$

où $L$ est la [[Fonction de perte]].

Si l'objectif est à la fois d'obtenir le meilleur modèle et d'estimer sa performance espérée, trois ensembles de données sont nécessaires.

# Interprétation

Le second ensemble étant distinct du premier, il n'a pas participé à la détermination de $\hat{\theta}$ : c'est ce découpage qui rend l'estimation du risque non biaisée.

# Remarque

La [[Sélection de modèle et estimation de la performance]] exige une estimation du risque. Le découpage des données en ensembles séparés est également le principe de la [[Méthode de validation]] et de la [[Validation croisée]].
