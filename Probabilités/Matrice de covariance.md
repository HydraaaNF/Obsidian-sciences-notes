# Définition
Soit $X = (X_1, ..., X_n)$ un vecteur aléatoire de $\mathbb{R}^n$ tel que chaque variable aléatoire réelle $X_j$ soit de carré intégrable. On appelle matrice de covariance de $X$ la matrice carrée d'ordre $n$ dont le coefficient d'indices $i, j$ est $cov(X_i, X_j)$. On la note $C(X)$.

# Intuition géométrique de la Matrice de Covariance

Lorsqu'on étudie un [[Vecteur gaussien]] en plusieurs dimensions, le nuage de points a généralement la forme d'un hyper-ellipsoïde. La [[Matrice de covariance]] $\Sigma$ contient toute l'information sur la forme de cette densité.

La diagonalisation, qui s'écrit $\Sigma = V D V'$, est une astuce géométrique pour séparer **l'orientation** de son **étirement**. 

- **La matrice $V$ (Vecteurs propres) :** Représente l'orientation. Ce sont les axes principaux du nuage de points.
- **La matrice $D$ (Valeurs propres) :** Représente la dispersion. Une grande valeur propre étire le nuage le long de son axe, une petite le concentre.

## Lire $V$, $D$, $\lambda_i$, $v_i$ et $\theta$ en 2D

Dans le cas 2D, la diagonalisation

$$  
\Sigma = VDV^\top  
$$

sépare clairement **l'orientation** de la distribution et sa **dispersion** :

$$  
D = \begin{pmatrix}  
\lambda_1 & 0\\
0 & \lambda_2  
\end{pmatrix},  
\qquad  
V = \begin{pmatrix}  
\vert & \vert\  \\
v_1 & v_2\  \\
\vert & \vert  
\end{pmatrix}.  
$$

### Que représente chaque quantité ?

- **$\lambda_i$** : valeur propre associée à la direction $v_i$. Elle mesure la **variance (dispersion)** dans cette direction. Pour les ellipses d'isodensité, la longueur du demi-axe est proportionnelle à $\sqrt{\lambda_i}$.
    
- **$v_i$** : vecteur propre unitaire. C'est une **direction principale** de l'ellipse.
    
- **$V$** : matrice dont les colonnes sont les vecteurs propres $v_1,v_2$. Elle décrit donc l'**orientation** de la base principale.
    
- **$\theta$** : angle entre l'axe $x$ et le premier axe principal $v_1$ (dans le cas 2D non dégénéré).
    

On peut aussi retenir la décomposition

$$  
\Sigma = \lambda_1 v_1v_1^\top + \lambda_2 v_2v_2^\top.  
$$

Autrement dit : **$D$ indique combien on étire, $V$ indique dans quelles directions, et $\theta$ indique comment ces directions sont orientées par rapport à $(x,y)$.**

### Écriture explicite de $V$ avec l'angle $\theta$

Pour une base propre orthonormée, la matrice de rotation standard s'écrit

$$  
V = R(\theta)  
= \begin{pmatrix}  
\cos\theta & -\sin\theta\  \\
\sin\theta & \cos\theta  
\end{pmatrix}.  
$$

Ses colonnes donnent directement les vecteurs propres :

$$  
v_1 = \begin{pmatrix}\cos\theta\ \sin\theta\end{pmatrix},  
\qquad  
v_2 = \begin{pmatrix}-\sin\theta\ \cos\theta\end{pmatrix}.  
$$

### Calcul explicite de $\Sigma$ en 2D

Les slides donnent aussi l'écriture de la matrice de covariance du point de vue des **variances** et de la **corrélation** :

$$  
\Sigma =  
\begin{pmatrix}  
\sigma_1^2 & \rho\sigma_1\sigma_2\  \\
\rho\sigma_1\sigma_2 & \sigma_2^2  
\end{pmatrix}.  
$$

On peut retrouver exactement ces coefficients à partir de la diagonalisation

$$  
\Sigma = VDV^\top,  
\qquad  
D = \begin{pmatrix}
\lambda_1& 0\\
0&\lambda_2
\end{pmatrix},  
\qquad  
V = \begin{pmatrix}  
\cos\theta & -\sin\theta\  \\
\sin\theta & \cos\theta  
\end{pmatrix}.  
$$

En développant le produit matriciel :

$$  
VD =  
\begin{pmatrix}  
\lambda_1\cos\theta & -\lambda_2\sin\theta\  \\
\lambda_1\sin\theta & \lambda_2\cos\theta  
\end{pmatrix},  
$$

puis$$
\begin{pmatrix}  
\lambda_1\cos^2\theta + \lambda_2\sin^2\theta  
&  
(\lambda_1-\lambda_2)\sin\theta\cos\theta  \\
(\lambda_1-\lambda_2)\sin\theta\cos\theta  
&  
\lambda_1\sin^2\theta + \lambda_2\cos^2\theta  
\end{pmatrix}.  
$$On lit donc directement les coefficients de la matrice de covariance :

$$  
\boxed{\sigma_1^2 = \lambda_1\cos^2\theta + \lambda_2\sin^2\theta}  
$$

$$  
\boxed{\sigma_2^2 = \lambda_1\sin^2\theta + \lambda_2\cos^2\theta}  
$$

$$  
\boxed{\rho\sigma_1\sigma_2  
= (\lambda_1-\lambda_2)\sin\theta\cos\theta}  
$$

et donc, lorsque $\sigma_1\sigma_2\neq0$,

$$  
\boxed{\rho  
= \frac{(\lambda_1-\lambda_2)\sin\theta\cos\theta}  
{\sqrt{\left(\lambda_1\cos^2\theta+\lambda_2\sin^2\theta\right)  
\left(\lambda_1\sin^2\theta+\lambda_2\cos^2\theta\right)}}}  
$$

### Application aux trois configurations des slides
#### Cas 1 : Pas de rotation, fort étirement
- **$V$ (Orientation) :** $\theta = 0$, signifiant que le nuage est aligné avec les axes classiques.
- **$D$ (Dispersion) :** Les valeurs propres sont de $4$ et $1$. 

```tikz
\begin{document}
\begin{tikzpicture}
  % Grille et axes
  \draw[step=1cm,gray,very thin,dashed] (-4,-3) grid (4,3);
  \draw[->, thick] (-4.5,0) -- (4.5,0) node[right] {$x$};
  \draw[->, thick] (0,-3.5) -- (0,3.5) node[above] {$y$};
  
  % Ellipses d'isodensité sans opacity (qui fait crasher TikzJax)
  \draw[blue, thick, fill=blue!10] (0,0) ellipse (2cm and 1cm);
  \draw[blue, thick, dashed] (0,0) ellipse (4cm and 2cm);
  
  % Vecteurs propres
  \draw[->, red, very thick] (0,0) -- (2,0) node[below right] {$v_1 (\lambda=4)$};
  \draw[->, red, very thick] (0,0) -- (0,1) node[above left] {$v_2 (\lambda=1)$};
\end{tikzpicture}
\end{document}
```

#### Cas 2 : Nuage incliné, fort étirement
- **$V$ (Orientation) :** $\theta = \pi/6$, les axes principaux subissent donc une rotation de 30 degrés.
- **$D$ (Dispersion) :** Les valeurs propres sont de $4$ et $1$. La forme du nuage reste identique au cas 1, mais elle est inclinée.

```tikz
\begin{document}
\begin{tikzpicture}
  % Grille et axes
  \draw[step=1cm,gray,very thin,dashed] (-4,-3) grid (4,3);
  \draw[->, thick] (-4.5,0) -- (4.5,0) node[right] {$x$};
  \draw[->, thick] (0,-3.5) -- (0,3.5) node[above] {$y$};
  
  % Rotation globale de 30 degrés pour l'ellipse et les vecteurs
  \begin{scope}[rotate=30]
      \draw[blue, thick, fill=blue!10] (0,0) ellipse (2cm and 1cm);
      \draw[blue, thick, dashed] (0,0) ellipse (4cm and 2cm);
      
      % Vecteurs propres
      \draw[->, red, very thick] (0,0) -- (2,0) node[below right] {$v_1$};
      \draw[->, red, very thick] (0,0) -- (0,1) node[above left] {$v_2$};
  \end{scope}
\end{tikzpicture}
\end{document}
```

#### Cas 3 : Dispersion symétrique (Cercle parfait)
- **$V$ (Orientation) :** $\theta = \pi/6$, soit une rotation de 30 degrés.
- **$D$ (Dispersion) :** Les valeurs propres sont de $2$ et $2$. Comme l'étalement est identique dans toutes les directions, le nuage forme un cercle parfait. Visuellement, la rotation n'a plus d'impact sur la forme de la densité.
```tikz
\begin{document}
\begin{tikzpicture}
  % Grille et axes
  \draw[step=1cm,gray,very thin,dashed] (-4,-3) grid (4,3);
  \draw[->, thick] (-4.5,0) -- (4.5,0) node[right] {$x$};
  \draw[->, thick] (0,-3.5) -- (0,3.5) node[above] {$y$};
  
  % Rotation de 30 degrés
  \begin{scope}[rotate=30]
      \draw[blue, thick, fill=blue!10] (0,0) circle (1.41cm);
      \draw[blue, thick, dashed] (0,0) circle (2.82cm);
      
      % Vecteurs propres
      \draw[->, red, very thick] (0,0) -- (1.41,0) node[below right] {$v_1$};
      \draw[->, red, very thick] (0,0) -- (0,1.41) node[above left] {$v_2$};
  \end{scope}
\end{tikzpicture}
\end{document}
```
