# Loi
Soit $(N, n) \in \mathbb{N}$ avec $n \leq N$ et $p \in \left[0,1 \right]$. Soit $X \sim \mathcal{H}(N, n, p)$ alors $$\forall k \in X(\Omega), \mathbb{P}(X = k) = \frac{\binom{P}{k} \binom{N - P}{n-k}}{\binom{N}{n}}$$avec
- $k \in \mathbb{N}, k \leq P, k \leq n, k \geq n - (N - P)$
- si $n \leq N - P, X(\Omega) = [\![0, min(P, n)]\!]$
- si $n > N - P, X(\Omega) = [\![n - (N - P), min(P, n)]\!]$

# Interprétation
- On propose $N$ objets dont une proportion $p = \frac{P}{N}$ vérifie une certaine propriété. On prélève **sans remise** $n$ objets. $X$ modélise le nombre d'objets prélevés possédant la propriété
- Si on prélève plus d'objets qu'il n'y a d'objets sans la propriété, alors on prélève obligatoirement le nombre d'objets prélevés moins celles n'ayant pas la propriété. D'où la 4e contrainte.
- Pour prélever $k$ objets ayant la propriété, il faut choisir $k$ objets parmi les $P$ ayant la propriété, puis $n − k$ parmi les $N − P$ n'ayant pas la propriété, d'où la formule de la loi.

# Propriétés
Soit $X \sim \mathcal{H}(N, n, p)$ alors
- $\mathbb{E}(X) = np$
