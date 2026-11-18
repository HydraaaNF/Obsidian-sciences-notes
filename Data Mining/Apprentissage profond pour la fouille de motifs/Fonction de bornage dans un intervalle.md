#dmv-pattern_mining_vs_deep_learning

# Définition

Le bornage dans l'intervalle $[0,1]$ ramène un réel sur cet intervalle en écrêtant ses valeurs extrêmes :

$$\operatorname{clamp}(x) = \begin{cases} 0 & \text{si } x < 0 \\ x & \text{si } 0 \le x \le 1 \\ 1 & \text{si } x > 1 \end{cases}$$

La fonction est l'identité à l'intérieur de l'intervalle et constante sur chacune des deux zones extérieures.

# Interprétation

Le bornage sert de garde-fou avant une quantification : il garantit qu'une valeur quelconque, somme pondérée ou activation, tombe dans $[0,1]$, où l'arrondi qui suit la ramène sur $\{0,1\}$.

- entrée négative : ramenée à 0, le neurone reste éteint ;
- entrée entre 0 et 1 : conservée telle quelle, l'arrondi tranche ensuite ;
- entrée supérieure à 1 : ramenée à 1, le neurone est allumé.

Dans un [[Auto-encodeur de motifs]], c'est sur l'activation de l'[[Encodage d'une transaction en motifs|encodage]] et du [[Décodage d'une couche de motifs|décodage]] que ce bornage $[0,1]$ intervient : la quantification y est l'arrondi appliqué juste après lui, ce qui produit la [[Couche de motifs]] binaire. Les poids continus sont binarisés en une matrice $W_b$ ($W \to W_b$) ; les valeurs de l'exemple tiennent dans $[0,1]$, où l'arrondi suffit à les ramener sur $\{0,1\}$.

Le biais suit une discrétisation distincte, à maximum $-1$. Elle conserve des entiers négatifs plus petits que $-1$ : $b = [-1{,}1, -2{,}9, -1{,}0, -2{,}1]$ donne $b_d = [-1, -2, -1, -2]$. Un bornage dans $[0,1]$ suivi de l'arrondi donnerait $[0,0,0,0]$ : le bornage de cette note ne décrit donc pas la discrétisation du biais, réglée par un maximum à $-1$. Le détail des deux projections est dans [[Poids binaires et optimisation différentiable]].

# Propriétés

Ces propriétés portent sur le bornage dans $[0,1]$ lui-même, et non sur la discrétisation du biais.

- Image : $\operatorname{clamp}(x) \in [0,1]$ pour tout réel $x$.
- Point fixe : $\operatorname{clamp}(x) = x$ exactement pour $x \in [0,1]$.
- Idempotence : $\operatorname{clamp}(\operatorname{clamp}(x)) = \operatorname{clamp}(x)$.
- Croissance : $x \le y$ implique $\operatorname{clamp}(x) \le \operatorname{clamp}(y)$.
- Écriture condensée : $\operatorname{clamp}(x) = \min(1, \max(0, x))$.

# Remarque

Le bornage est bilatéral : il présente deux paliers constants, à 0 pour les entrées négatives et à 1 pour les entrées supérieures à 1. Un tracé réduit au seul palier haut, plat à 1 mais prolongeant la droite vers la gauche, décrit une troncature par le haut et non le bornage : la valeur 0 sur $x < 0$ est une borne atteinte, pas une absence de valeur.

Toute entrée négative est donc écrêtée à 0 avant l'arrondi, exactement comme l'entrée nulle : la sortie ne distingue pas les deux cas.
