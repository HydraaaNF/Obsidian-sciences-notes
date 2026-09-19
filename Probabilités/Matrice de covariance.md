# Définition
Soit $X = (X_1, ..., X_n)$ un vecteur aléatoire de $\mathbb{R}^n$ tel que chaque variable aléatoire réelle $X_j$ soit de carré intégrable. On appelle matrice de covariance de $X$ la matrice de carrée d'ordre $n$ dont le coefficient d'indices $i, j$ est $cov(X_i, X_j)$. On la note $C(X)$.

# Intuition géométrique de la Matrice de Covariance

Lorsqu'on étudie un [[Vecteur gaussien]] en plusieurs dimensions, le nuage de points a généralement la forme d'un hyper-ellipsoïde. La [[Matrice de covariance]] $\Sigma$ contient toute l'information sur la forme de cette densité.

La diagonalisation, qui s'écrit $\Sigma = V D V'$, est une astuce géométrique pour séparer **l'orientation** de son **étirement**[cite: 2]. 

- **La matrice $V$ (Vecteurs propres) :** Représente l'orientation[cite: 2]. Ce sont les axes principaux du nuage de points[cite: 2].
- **La matrice $D$ (Valeurs propres) :** Représente la dispersion[cite: 2]. Une grande valeur propre étire le nuage le long de son axe, une petite le concentre[cite: 2].

---

## Cas 1 : Pas de rotation, fort étirement
- **$V$ (Orientation) :** $\theta = 0$, signifiant que le nuage est aligné avec les axes classiques[cite: 2].
- **$D$ (Dispersion) :** Les valeurs propres sont de $4$ et $1$[cite: 2]. 

```tikz
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
```

## Cas 2 : Nuage incliné, fort étirement
- **$V$ (Orientation) :** $\theta = \pi/6$, les axes principaux subissent donc une rotation de 30 degrés[cite: 2].
- **$D$ (Dispersion) :** Les valeurs propres sont de $4$ et $1$[cite: 2]. La forme du nuage reste identique au cas 1, mais elle est inclinée[cite: 2].

```tikz
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
```

## Cas 3 : Dispersion symétrique (Cercle parfait)
- **$V$ (Orientation) :** $\theta = \pi/6$, soit une rotation de 30 degrés[cite: 2].
- **$D$ (Dispersion) :** Les valeurs propres sont de $2$ et $2$[cite: 2]. Comme l'étalement est identique dans toutes les directions, le nuage forme un cercle parfait[cite: 2]. Visuellement, la rotation n'a plus d'impact sur la forme de la densité[cite: 2].

```tikz
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
```
