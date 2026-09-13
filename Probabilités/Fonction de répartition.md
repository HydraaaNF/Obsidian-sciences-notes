# Définition
Soit $X$ une variable aléatoire réelle. On appelle fonction de répartition de $X$ la fonction $F_X$ définie par $$\forall t \in \mathbb{R}, F_X(t) = \mathbb{P}(X \leq t)$$
# Propriétés
Soit $X$ une variable aléatoire réelle, alors
- La fonction $F_X$ est croissante sur $\mathbb{R}$.
- On a $lim_{t \to +\infty} F_X(t) = 0$ et $lim_{t \to +\infty} F_X(t) = 1$.
- Pour tout réel $t$, on a $F_X(t^-) = \mathbb{P}(X < t)$ et $F_X(t^+) = \mathbb{P}(X \leq t)$.
- La fonction $F_X$ est continue à droite sur $\mathbb{R}$.
- Pour tout réel $t$, le saut de $F_X$ en $t$ vaut $\mathbb{P}(X = t)$
- Si $X$ est discrète, alors $F_X$ est une fonction en escalier et l'ensemble de ses points de discontinuité est l'ensemble $X(\Omega)$ des valeurs prises par $X$.
- Si $X$ est une variable aléatoire continue, alors $F_X$ est continue sur $\mathbb{R}$.
- Si $X$ est une variable aléatoire continue et si sa densité $f_X$ est continue par morceaux, alors $F_X$ est dérivable en tout point de continuité de $f_X$, et l'on a $F'_X(t) = f_X(t)$ en un tel point.
- Soit $F$ une fonction croissante sur $\mathbb{R}$, continue à droite sur $\mathbb{R}$ et vérifiant
	- $lim_{t \to -\infty} F(t) = 0$
	- $lim_{t \to +\infty} F(t) = 1$
	Il existe un espace probabilisé $(\Omega, \mathcal{F}, \mathbb{P})$ et une variable aléatoire réelle $X$ définie sur $\Omega$ tels que l'on ait $F_X = F$.
- Deux variables aléatoires ont même loi ssi elles ont même fonction de répartition.