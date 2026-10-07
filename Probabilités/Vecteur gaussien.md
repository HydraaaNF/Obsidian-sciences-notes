# Définition

Un [[Vecteur aléatoire|vecteur aléatoire]] $X$ de dimension $p$ est un **vecteur gaussien** si toute combinaison linéaire de ses composantes, notée $a'X$, est une [[Loi gaussienne|variable aléatoire gaussienne]] de dimension 1.

Sa [[Densité d'un vecteur gaussien|densité]] s'écrit

$$f(x) = \frac{1}{(2\pi)^{p/2}|\Sigma|^{1/2}} \exp \left\{ -\frac{1}{2}(x - \mu)^\top\Sigma^{-1}(x - \mu) \right\}$$

où $\mu$ est le [[Vecteur moyen|vecteur moyen]] et $\Sigma$ la [[Matrice de covariance|matrice de covariance]] du vecteur.

# Interprétation géométrique

Les courbes d'isodensité d'un vecteur gaussien sont des hyper-ellipsoïdes : voir [[Ellipsoïdes d'isodensité]]. Les vecteurs propres de $\Sigma$ définissent les axes principaux (orientation de la densité) et ses valeurs propres la dispersion le long de ces axes. Si $\Sigma$ est diagonale, les composantes sont [[Indépendance des coordonnées d'un vecteur gaussien|indépendantes]].

# Propriétés

- La [[Fonction caractéristique d'un vecteur gaussien|fonction caractéristique]] d'un vecteur gaussien s'écrit $\Phi_X(\xi) = e^{i\xi \cdot \mathbb{E}(X)} e^{-\frac{1}{2}\xi^\top \mathbf{C}(X)\xi}$.
- Une [[Fonction affine d'un vecteur gaussien|fonction affine]] d'un vecteur gaussien reste gaussienne.
- Les composantes d'un vecteur gaussien sont indépendantes si et seulement si sa matrice de covariance est diagonale.

# Procédé de décorrélation

Pour trouver une base orthonormée $\{v_1, \dots, v_n\}$ de $\mathbb{R}^n$ dans laquelle les coordonnées d'un vecteur gaussien $X$ de matrice de covariance $\mathbf{C}(X)$ sont des variables aléatoires réelles indépendantes, on diagonalise $\mathbf{C}(X)$ :

- deux vecteurs propres associés à deux valeurs propres distinctes sont automatiquement orthogonaux, car $\mathbf{C}(X)$ est symétrique réelle ;
- si toutes les valeurs propres sont simples, il suffit de normer les vecteurs propres ;
- sinon, on applique le procédé de Gram-Schmidt au sein de chaque sous-espace propre associé à une valeur propre multiple.

Les colonnes représentant, dans la base initiale, ces vecteurs propres formant une base orthonormée constituent la matrice de passage orthogonale $P$, et l'on pose $Y = P^\top X$.

# Liens avec d'autres lois

Le vecteur gaussien généralise la [[Loi gaussienne]] : en dimension $p = 1$, les deux notions coïncident.

# Exemple

Un vecteur gaussien multivarié avec $m = [21]$ et $\theta = \pi/6$ : un ensemble de 1 000 échantillons tirés de ce vecteur et la fonction de densité correspondante.

# Remarque

La densité d'un vecteur gaussien de dimension $p$ fait intervenir $(2\pi)^{p/2}$ : l'exposant est la moitié de la dimension du vecteur, de sorte que l'intégrale de la densité sur $\mathbb{R}^p$ vaut 1. L'écriture $(2\pi)^{n/2}$ avec un $n$ qui ne désigne pas la dimension est une erreur fréquente.
