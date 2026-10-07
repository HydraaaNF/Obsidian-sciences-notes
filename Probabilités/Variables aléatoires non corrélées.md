# Définition

Soient $X$ et $Y$ deux [[Variable aléatoire réelle|variables aléatoires réelles]] de carré intégrable (c'est-à-dire admettant un [[Moment d'ordre k|moment d'ordre 2]]). On dit que $X$ et $Y$ sont **non corrélées** lorsque leur [[Covariance|covariance]] est nulle :

$$\operatorname{cov}(X, Y) = 0$$

Cette situation correspond à l'annulation du [[Coefficient de corrélation linéaire|coefficient de corrélation linéaire]] de $X$ et de $Y$.

# Propriétés

Si $X$ et $Y$ sont deux variables aléatoires réelles de carré intégrable et [[Indépendance de variables aléatoires|indépendantes]], alors elles sont non corrélées :

$$\operatorname{cov}(X, Y) = 0$$

### Démonstration

Pour $X$ et $Y$ indépendantes, l'[[Espérance d'un produit de variables aléatoires indépendantes|espérance du produit]] vaut $\mathbb{E}(XY) = \mathbb{E}(X)\mathbb{E}(Y)$. En reportant dans la formule de la covariance $\operatorname{cov}(X, Y) = \mathbb{E}(XY) - \mathbb{E}(X)\mathbb{E}(Y)$, les deux termes s'annulent :

$$\operatorname{cov}(X, Y) = 0$$

# Remarque

La réciproque est fausse : il arrive que $X$ et $Y$ soient non corrélées et pourtant non [[Indépendance de variables aléatoires|indépendantes]]. L'exemple ci-dessous en fournit une illustration.

# Exemple

**Des variables non corrélées mais non indépendantes.** Soit $(X, Y)$ un couple de [[Loi uniforme sur un domaine|loi uniforme]] sur le disque $D_R$ de centre $(0, 0)$ et de rayon $R$. Pour un tel couple, $X$ et $Y$ ne sont pas [[Indépendance des coordonnées d'un vecteur aléatoire|indépendantes]]. Par ailleurs, $\mathbb{E}(X) = \mathbb{E}(Y) = 0$, de sorte que $\operatorname{cov}(X, Y) = \mathbb{E}(XY)$. Or, grâce au [[Théorème de transfert pour un vecteur aléatoire|théorème de transfert]] :

$$\begin{aligned}
\mathbb{E}(XY) &= \iint_{\mathbb{R}^2} xy\, f_{(X,Y)}(x,y)\,dx\,dy \\
&= \frac{1}{\pi R^2} \iint_{D_R} xy\,dx\,dy \\
&= \frac{1}{\pi R^2} \int_0^R \int_0^{2\pi} r\cos\theta\,r\sin\theta\,r\,d\theta\,dr \\
&= \frac{1}{\pi R^2} \int_0^R r^3\,dr \int_0^{2\pi} \sin\theta\cos\theta\,d\theta \\
&= \frac{1}{\pi R^2}\frac{R^4}{4}\left[\frac{1}{2}(\sin\theta)^2\right]_0^{2\pi} \\
&= 0
\end{aligned}$$

donc $\operatorname{cov}(X, Y) = 0$ : $X$ et $Y$ sont non corrélées, et pourtant non indépendantes.
