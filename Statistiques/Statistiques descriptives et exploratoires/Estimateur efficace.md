# Définition

Un [[Estimateur|estimateur]] $T$ [[Biais d'un estimateur|sans biais]] de $\theta$ est dit **efficace** s'il est le plus précis des estimateurs sans biais de $\theta$, c'est-à-dire s'il minimise la [[Distance en moyenne d'ordre p|distance en moyenne quadratique]] $\mathbb{E}\left[(T-\theta)^2\right]$.

# Remarque

Pour un estimateur $T$ sans biais de $\theta$, l'[[Erreur quadratique moyenne|erreur quadratique moyenne]] se confond avec la variance :

$$\mathbb{E}\left[(T-\theta)^2\right] = \mathbb{V}(T).$$

Par conséquent, un estimateur est efficace si sa variance est minimale parmi tous les estimateurs sans biais de $\theta$, autrement dit si sa variance atteint la borne $V_0 = \frac{1}{I_n(\theta)}$ du [[Théorème de Fréchet-Darmois-Cramér-Rao]]. On n'est pas sûr qu'un tel estimateur existe.

# Exemple

**Exemple 1 : loi de Poisson.**

On considère un [[Échantillon et échantillonnage|échantillon]] $(X_1, \dots, X_n)$ issu de la [[Loi de Poisson|loi de Poisson]] de paramètre $\lambda$ inconnu. L'[[Estimateur du maximum de vraisemblance|estimateur du maximum de vraisemblance]] de $\lambda$ est donné par

$$\hat{\lambda} = \overline{X},$$

où $\overline{X}$ est la [[Moyenne empirique|moyenne empirique]]. Cet estimateur est [[Estimateur fortement convergent|fortement convergent]] vers $\lambda$ d'après la [[Loi forte des grands nombres|loi forte des grands nombres]] et également sans biais. Par ailleurs,

$$\begin{aligned} \mathbb{V}(\hat{\lambda}) &= \mathbb{V}(\overline{X}) \\ &= \frac{\mathbb{V}(X_1)}{n} \\ &= \frac{\lambda}{n}. \end{aligned}$$

À présent, on remarque que le domaine de définition de la variable mère $X$ ne dépend pas du paramètre $\lambda$. On calcule alors la [[Théorème de Fréchet-Darmois-Cramér-Rao|borne de F.D.C.R.]] qui vaut, d'après l'additivité de l'[[Information de Fisher|information de Fisher]] :

$$\begin{aligned} V_0 &= \frac{1}{I_n(\lambda)} \\ &= \frac{1}{nI_1(\lambda)} \\ &= \frac{\lambda}{n}, \end{aligned}$$

car $I_1(\lambda) = 1/\lambda$. On conclut ainsi que $\overline{X}$ est un estimateur efficace de $\lambda$. C'est le meilleur estimateur de $\lambda$.

**Exemple 2 : loi exponentielle.**

De même que précédemment, on cherche à estimer le paramètre $\lambda$ de la [[Loi exponentielle|loi exponentielle]] à partir d'un échantillon $(X_1, \dots, X_n)$. L'[[Estimateur du maximum de vraisemblance|estimateur du maximum de vraisemblance]] de $\lambda$ est donné par

$$\hat{\lambda} = \frac{1}{\overline{X}}.$$

Étant donné que l'on dispose de propriétés de convergence pour $\overline{X}$, on cherche de préférence à estimer le paramètre $\theta = 1/\lambda$. Ainsi, $\hat{\theta} = \overline{X}$ est un [[Estimateur fortement convergent|estimateur fortement convergent]] de $\theta$ (car $\mathbb{E}[X] = \theta$) et de variance

$$\begin{aligned} \mathbb{V}(\hat{\theta}) &= \mathbb{V}(\overline{X}) \\ &= \frac{\mathbb{V}(X_1)}{n} \\ &= \frac{1}{n\lambda^2} \\ &= \frac{\theta^2}{n}. \end{aligned}$$

Le domaine de définition d'une loi exponentielle ne dépend pas du paramètre $\lambda$, et donc de $\theta$ non plus. Le [[Calcul de l'information de Fisher sous hypothèse de Cramér-Rao|théorème de Cramér-Rao]] et l'additivité de l'information peuvent s'appliquer pour simplifier le calcul de $I_n(\theta)$ :

$$\begin{aligned}
I_n(\theta) &= nI_1(\theta) \\
&= -n\mathbb{E}\left[\frac{\partial^2}{\partial\theta^2}\mathcal{L}\mathcal{L}(X_1;\theta)\right] \\
&= -n\mathbb{E}\left[\frac{\partial^2}{\partial\theta^2}\ln\left(\frac{e^{-X_1/\theta}}{\theta}\right)\right] \\
&= n\mathbb{E}\left[\frac{\partial^2}{\partial\theta^2}\left(\ln(\theta)+\frac{X_1}{\theta}\right)\right] \\
&= -\frac{n}{\theta^2}+\frac{2n}{\theta^3}\mathbb{E}[X_1] \\
&= -\frac{n}{\theta^2}+\frac{2n}{\theta^3}\mathbb{E}[X_1] \\
&= \frac{n}{\theta^2}
\end{aligned}
$$

car $\mathbb{E}[X_1] = \theta$. Ainsi

$$\mathbb{V}(\hat{\theta}) = \frac{1}{I_n(\theta)}$$

et on en conclut que $\hat{\theta} = \overline{X}$ est un estimateur efficace de $\theta = 1/\lambda$.
