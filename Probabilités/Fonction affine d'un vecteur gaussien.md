# Propriétés

**Fonction affine d'un vecteur gaussien.** Soit $X$ un [[Vecteur gaussien|vecteur gaussien]] de $\mathbb{R}^n$, $A \in \mathcal{M}_{m,n}(\mathbb{R})$, et $B$ un vecteur colonne de $\mathbb{R}^m$. Alors $AX + B$ est un vecteur gaussien de $\mathbb{R}^m$ de [[Vecteur moyen|vecteur moyen]] $A\mathbb{E}(X) + B$ et de [[Matrice de covariance|matrice de covariance]] $A\mathbf{C}(X)A^T$.

Le caractère gaussien est donc conservé par changement de variable affine.

### Démonstration

Il est clair que $\mathbb{E}(AX + B) = A\mathbb{E}(X) + B$, par linéarité de l'[[Espérance d'une variable aléatoire|espérance]]. Mais on veut démontrer quelque chose de beaucoup plus fort : le type de la loi est conservé par changement de variable affine.

On calcule la [[Fonction caractéristique d'un vecteur aléatoire|fonction caractéristique]] de $AX + B$, qui est à valeurs dans $\mathbb{R}^m$, en utilisant la [[Fonction caractéristique d'un vecteur gaussien|fonction caractéristique du vecteur gaussien]] $X$. Soit $\xi \in \mathbb{R}^m$, considéré comme un vecteur colonne. On a

$$\begin{aligned}
\Phi_{AX+B}(\xi) &= \mathbb{E}(e^{i\xi \cdot (AX+B)}) \\
&= e^{i\xi \cdot B} \mathbb{E}(e^{i\xi \cdot (AX)}) \\
&= e^{i\xi \cdot B} \mathbb{E}(e^{i(A^T \xi) \cdot X}) \\
&= e^{i\xi \cdot B} \Phi_X(A^T \xi) \\
&= e^{i\xi \cdot B} e^{i(A^T \xi) \cdot \mathbb{E}(X)} e^{-\frac{1}{2}(A^T \xi)^T \mathbf{C}(X)(A^T \xi)} \\
&= e^{i\xi \cdot (A\mathbb{E}(X)+B)} e^{-\frac{1}{2}\xi^T A \mathbf{C}(X) A^T \xi}
\end{aligned}$$

ce qui est exactement la fonction caractéristique d'un vecteur gaussien de vecteur moyen $A\mathbb{E}(X) + B$ et de matrice de covariance $A\mathbf{C}(X)A^T$.
