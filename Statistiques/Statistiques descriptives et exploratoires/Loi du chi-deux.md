# Définition

La **loi du chi-deux** à $n$ degrés de liberté, notée $\chi_n^2$, est la loi de la variable aléatoire

$$ Y = X_1^2 + \dots + X_n^2, $$

où $X_1, \dots, X_n$ sont des variables aléatoires indépendantes et identiquement distribuées de [[Loi gaussienne|loi normale centrée réduite]] $\mathcal{N}(0,1)$.

# Propriétés

La loi du chi-deux à $n$ degrés de liberté est également une [[Loi gamma|loi Gamma]] $\Gamma\left(\frac{n}{2}, \frac{1}{2}\right)$. Son [[Espérance d'une variable aléatoire|espérance]] et sa [[Variance|variance]] valent alors

$$\mathbb{E}[Y] = n$$

$$\mathbb{V}(Y) = 2n.$$

La somme de deux variables aléatoires indépendantes distribuées respectivement selon une loi $\chi_p^2$ et une loi $\chi_q^2$ suit une loi $\chi_{p+q}^2$.

Sa [[Fonction caractéristique|fonction caractéristique]] vaut

$$\Phi_Y(\xi) = (1 - 2i\xi)^{-n/2}.$$

# Liens avec d'autres lois

Pour un échantillon gaussien de variance $\sigma^2$, la statistique $\frac{(n-1)S'^2}{\sigma^2}$ suit une loi du chi-deux à $n-1$ degrés de liberté : voir [[Loi de la variance empirique corrigée|loi de la variance empirique corrigée]].

Elle intervient également dans la construction de la [[Loi de Student|loi de Student]] et de la [[Loi de Fisher|loi de Fisher]], et dans le [[Test d'ajustement du chi-deux|test d'ajustement du chi-deux]].