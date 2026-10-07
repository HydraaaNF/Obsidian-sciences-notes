# Loi

La loi de Weibull est une [[Probabilité à densité|loi à densité]] utilisée en [[Fiabilité]] pour modéliser des durées de vie.

Pour une [[Variable aléatoire continue|variable aléatoire continue]] $X$ suivant une loi de Weibull de paramètre de forme $k > 0$ et de paramètre d'échelle $\lambda > 0$, la densité $f$ et la [[Fonction de répartition|fonction de répartition]] $F$ s'écrivent, pour $x \geq 0$,

$$f(x) = \frac{k}{\lambda} \left(\frac{x}{\lambda}\right)^{k-1} e^{-(x/\lambda)^k}$$

$$F(x) = 1 - e^{-(x/\lambda)^k},$$

avec $f(x) = 0$ et $F(x) = 0$ pour $x < 0$.

# Propriétés

- Son [[Espérance d'une variable aléatoire|espérance]] est

$$\mathbb{E}[X] = \lambda\, \Gamma\left(1 + \frac{1}{k}\right),$$

où $\Gamma$ désigne la [[Fonction Gamma]].

- Sa [[Variance|variance]] est

$$\mathbb{V}[X] = \lambda^2 \left[\Gamma\left(1 + \frac{2}{k}\right) - \left(\Gamma\left(1 + \frac{1}{k}\right)\right)^2\right].$$

- Sa [[Fonction caractéristique|fonction caractéristique]] n'admet pas d'expression élémentaire simple ; elle s'écrit sous forme de série :

$$\Phi_X(\xi) = \mathbb{E}\left[e^{i\xi X}\right] = \sum_{n=0}^{+\infty} \frac{(i\xi)^n \lambda^n}{n!}\, \Gamma\left(1 + \frac{n}{k}\right).$$

Cette série converge pour tout $\xi \in \mathbb{R}$ lorsque $k > 1$.

# Interprétation

La loi de Weibull modélise des durées de vie ou des temps avant défaillance, par exemple le temps avant la panne d'un composant, ce qui en fait un modèle usuel de [[Fiabilité]].

La fiabilité à l'instant $t$ est la probabilité que le composant soit encore en fonctionnement :

$$R(t) = \mathbb{P}[X > t] = e^{-(t/\lambda)^k}.$$

Le taux de défaillance $h(t) = \frac{f(t)}{R(t)}$ s'écrit alors

$$h(t) = \frac{k}{\lambda} \left(\frac{t}{\lambda}\right)^{k-1}.$$

Le paramètre de forme $k$ commande son évolution :

- si $k < 1$, le taux de défaillance décroît, ce qui décrit des défaillances de jeunesse (mortalité infantile) ;
- si $k = 1$, il est constant : c'est le cas de la [[Loi exponentielle|loi exponentielle]], sans usure ni vieillissement ;
- si $k > 1$, il croît, ce qui décrit une usure ou un vieillissement.

# Liens avec d'autres lois

- La loi de Weibull généralise la [[Loi exponentielle|loi exponentielle]] : pour $k = 1$, elle coïncide avec la loi exponentielle de taux $1/\lambda$.
- C'est la loi de la transformée puissance d'une loi exponentielle : si $Y$ suit la loi exponentielle de paramètre $1$, alors $\lambda\, Y^{1/k}$ suit la loi de Weibull de paramètres $k$ et $\lambda$.
- Le minimum de variables aléatoires [[Indépendance de variables aléatoires|indépendantes]] de lois de Weibull de même paramètre de forme $k$ et de paramètres d'échelle $\lambda_1, \dots, \lambda_n$ suit une loi de Weibull de paramètres $k$ et $\left(\sum_{i=1}^{n} \lambda_i^{-k}\right)^{-1/k}$.
