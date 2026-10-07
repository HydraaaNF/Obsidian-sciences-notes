# Algorithme

L'[[Analyse en composantes principales|analyse en composantes principales]] (ACP) s'applique à $n$ observations décrites par $p$ variables chacune, rassemblées dans la matrice de données $\mathbf{X}$ ($n \times p$) :

$$\mathbf{X} = \begin{pmatrix} x_{11} & \dots & x_{1i} & \dots & x_{1p} \\ \vdots & \ddots & \vdots & & \vdots \\ x_{j1} & \dots & x_{ij} & \dots & x_{jp} \\ \vdots & & \vdots & \ddots & \vdots \\ x_{n1} & \dots & x_{ni} & \dots & x_{np} \end{pmatrix}$$

Par souci de simplification, on suppose que :

1. les données ont une moyenne empirique nulle (elles sont centrées) ;
2. toutes les observations ont la même importance, avec un poids $1/n$.

On a alors $\mathbf{V} \propto \mathbf{X}^\top\mathbf{X}$ et $\mathbf{R} \propto \tilde{\mathbf{X}}^\top\tilde{\mathbf{X}}$.

L'algorithme se déroule en quatre étapes :

1. Calculer la matrice de covariance $\mathbf{V}_{p \times p} = \frac{1}{n} \mathbf{X}^\top\mathbf{X}$ (ou la matrice de corrélation $\mathbf{R}$).
2. Calculer le système propre :

$$\mathbf{V}_{p \times p} = \mathbf{U}_{p \times p} \mathbf{\Lambda}_{p \times p} \mathbf{U}_{p \times p}^{-1} = \mathbf{U} \mathbf{\Lambda} \mathbf{U}^\top$$

Pour des données de très grande dimension, le système propre est calculé par l'algorithme NIPALS.
3. Trier les valeurs propres et retenir les plus grandes, en triant $\mathbf{U}_{p \times p}$ en conséquence pour obtenir $\overline{\mathbf{U}}_{q \times p}$ ; le choix du nombre $q$ de composantes retenues s'appuie sur l'[[Éboulis des valeurs propres]].
4. Reconstruire ou projeter les données $\mathbf{X}$ :

$$\mathbf{Y}_{q \times n} = \overline{\mathbf{U}}_{q \times p} \mathbf{X}_{p \times n}$$

Le recours aux vecteurs propres de $\mathbf{V}$ est justifié par les [[Théorèmes de l'analyse en composantes principales]].
