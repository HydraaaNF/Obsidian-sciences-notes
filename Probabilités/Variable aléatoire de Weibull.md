# Loi
Soit $k > 0$ et $\lambda > 0$. $X \sim \mathcal{W}(k, \lambda)$ si $X$ admet pour densité $f_X(x) = \dfrac{k}{\lambda}\left(\dfrac{x}{\lambda}\right)^{k-1} e^{-(x/\lambda)^k}$ pour $x \geq 0$, et $f_X(x) = 0$ pour $x < 0$

Fonction de répartition : $F_X(x) = 1 - e^{-(x/\lambda)^k}$ pour $x \geq 0$

# Interprétation
X modélise une durée de vie ou un temps jusqu'à un évènement (défaillance, panne, décès), avec un taux de risque instantané $h(x) = f_X(x)/(1-F_X(x))$ qui peut évoluer dans le temps.

* $\lambda$ est un paramètre d'échelle (fixe l'ordre de grandeur temporel)
* $k$ est un paramètre de forme, qui gouverne l'évolution du taux de risque :
  * $k < 1$ : risque décroissant (mortalité infantile)
  * $k = 1$ : risque constant
  * $k > 1$ : risque croissant (usure, vieillissement)

# Propriétés
Soit $X \sim \mathcal{W}(k, \lambda)$, alors

* $\mathbb{E}(X) = \lambda \, \Gamma\!\left(1 + \dfrac{1}{k}\right)$
* $\mathbb{V}(X) = \lambda^2 \left[ \Gamma\!\left(1 + \dfrac{2}{k}\right) - \Gamma\!\left(1 + \dfrac{1}{k}\right)^{\!2} \right]$
* $G_X$ et $\varphi_X$ n'ont pas de forme close élémentaire pour $k$ quelconque : elles s'expriment comme une série faisant intervenir la fonction $\Gamma$ (voir [[Fonction Gamma]])

# Caractérisation par la loi exponentielle
Soit $Y \sim \mathcal{E}(1)$. Alors $X = \lambda \, Y^{1/k} \sim \mathcal{W}(k, \lambda)$

Démonstration : pour $x \geq 0$, comme $t \mapsto t^k$ est strictement croissante sur $\mathbb{R}_+$

$$\mathbb{P}(X > x) = \mathbb{P}\left(Y^{1/k} > \frac{x}{\lambda}\right) = \mathbb{P}\left(Y > \left(\frac{x}{\lambda}\right)^k\right) = e^{-(x/\lambda)^k}$$

d'où $F_X(x) = 1 - e^{-(x/\lambda)^k}$, ce qui est bien la fonction de répartition de $\mathcal{W}(k, \lambda)$

Réciproque : $X^k \sim \mathcal{E}(1/\lambda^k)$ — une variable de Weibull élevée à la puissance $k$ redonne une exponentielle

Application (méthode d'inversion) : si $U \sim \mathcal{U}([0,1])$, alors $X = \lambda(-\ln(1-U))^{1/k} \sim \mathcal{W}(k, \lambda)$ — méthode standard de simulation de la loi de Weibull

# Cas particuliers
* $k = 1$ : [[Variable aléatoire exponentielle|loi exponentielle]] $\mathcal{E}(1/\lambda)$ — risque constant, absence de mémoire
* $k = 2$ : loi de Rayleigh de paramètre $\sigma = \lambda/\sqrt{2}$ — loi du module d'un vecteur gaussien centré 2D $\sqrt{U^2+V^2}$ ; utilisée pour la vitesse du vent, l'amplitude d'un signal radio bruité
* $k \approx 3{,}4$ : approximation visuelle d'une [[Variable aléatoire gaussienne|loi normale]] — coïncidence de forme, pas une identité mathématique (Weibull reste asymétrique, support $[0,+\infty[$)
* $k \to +\infty$ : dégénérescence vers une masse de Dirac en $\lambda$ ($\mathbb{V}(X) \to 0$)
* $k = 1/2$ : $X = \lambda Y^2$ avec $Y \sim \mathcal{E}(1)$ — risque très fortement décroissant, utilisé en analyse de survie