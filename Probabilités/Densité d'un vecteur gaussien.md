# Théorème

**Densité d'un vecteur gaussien.** Soit $X$ un [[Vecteur gaussien|vecteur gaussien]] de $\mathbb{R}^n$. On suppose que sa [[Matrice de covariance|matrice de covariance]] $\mathbf{C}(X)$ est inversible. Alors $X$ admet une [[Loi d'un vecteur aléatoire|densité]], donnée par

$$\forall x \in \mathbb{R}^n \quad f_X(x) = (2\pi)^{-\frac{n}{2}} \left( \det \mathbf{C}(X) \right)^{-\frac{1}{2}} e^{-\frac{1}{2} (x - \mathbb{E}(X))^T \mathbf{C}(X)^{-1} (x - \mathbb{E}(X))}$$

Dans cette formule, les vecteurs $x$ et $\mathbb{E}(X)$ doivent bien entendu être interprétés comme des vecteurs colonnes.

# Remarque

1. L'hypothèse signifie que la matrice de covariance est non seulement symétrique positive, comme toute matrice de covariance, mais aussi *non dégénérée*, ce qui signifie que la forme quadratique associée est définie-positive. Pour cette raison, on dit d'un tel vecteur gaussien admettant une densité sur $\mathbb{R}^n$ qu'il est *non dégénéré*.

2. Pour que ce soit le cas, il faut et il suffit que toutes les valeurs propres de $\mathbf{C}(X)$ soient strictement positives (inversible signifie que $0$ n'est pas valeur propre).

3. En dimension $n = 1$, les vecteurs gaussiens dégénérés sont les variables aléatoires constantes, car dire que $\mathbf{C}(X) = (\sigma^2)$ est non inversible revient à dire que $\sigma^2 = 0$ (voir [[Vecteur gaussien]]).

4. Ce résultat est admis. La démonstration consisterait à calculer la transformée de Fourier inverse de la [[Fonction caractéristique d'un vecteur gaussien|fonction caractéristique]], qui est une gaussienne $n$-dimensionnelle pourvu que $\mathbf{C}(X)$ soit inversible : comme en dimension $1$, la transformée de Fourier d'une gaussienne est une autre gaussienne.

**Remarques pratiques.** Si le vecteur gaussien n'est pas centré, cela se traduit sur la fonction caractéristique par l'existence d'un terme en $e^{i\xi \cdot \mu}$, où $\mu$ est justement le [[Vecteur moyen|vecteur moyen]]. Sur la densité, cela se traduit par le fait que le polynôme du deuxième degré qui apparaît sous l'exponentielle est une forme quadratique en $x - \mu$ au lieu de $x$. Sous sa forme développée, ce polynôme du deuxième degré comporte des termes du premier degré si et seulement si le vecteur gaussien n'est pas centré.

# Exemple

**Couple gaussien centré en dimension $n = 2$.** Illustrons ces remarques dans le cas de la dimension $n = 2$. Soit $(X, Y)$ un couple gaussien *centré* de matrice de covariance

$$C = \begin{pmatrix} \mathbb{V}(X) & \operatorname{cov}(X, Y) \\ \operatorname{cov}(Y, X) & \mathbb{V}(Y) \end{pmatrix} = \begin{pmatrix} \sigma_1^2 & c \\ c & \sigma_2^2 \end{pmatrix}$$

La forme quadratique associée est

$$q(u) = u^T C u = \sigma_1^2 u_1^2 + 2cu_1u_2 + \sigma_2^2 u_2^2$$

La [[Fonction caractéristique d'un vecteur gaussien|fonction caractéristique]] est

$$\Phi_{(X,Y)}(u_1, u_2) = e^{-\frac{1}{2}q(u)}$$

La condition d'existence d'une densité est

$$\det C = \sigma_1^2 \sigma_2^2 - c^2 \neq 0$$

En fait, $\det C \geq 0$ en vertu de l'[[Inégalité de Cauchy-Schwarz pour des variables aléatoires|inégalité de Cauchy-Schwarz]], donc on pourrait tout aussi bien dire que la condition d'existence d'une densité est $\det C > 0$. Donc, il existe une densité si et seulement si $|c| < \sigma_1 \sigma_2$. Cette condition étant supposée réalisée, la densité vaut

$$f_{(X,Y)}(x_1, x_2) = \frac{1}{2\pi\sqrt{\sigma_1^2\sigma_2^2 - c^2}} e^{-\frac{1}{2} x^T C^{-1} x}$$

où $x = (x_1, x_2)^T$.
