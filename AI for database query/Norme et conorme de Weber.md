# Définition
La **t-norme de Weber** est :

$$
\top_W(x, y) =
\begin{cases}
y & \text{si } x = 1 \\
x & \text{si } y = 1 \\
0 & \text{sinon}
\end{cases}
$$

La **t-conorme de Weber** est :

$$
\bot_W(x, y) =
\begin{cases}
y & \text{si } x = 0 \\
x & \text{si } y = 0 \\
1 & \text{sinon}
\end{cases}
$$

# Propriétés
$\top_W$ est la **plus petite** [[Norme triangulaire]] et $\bot_W$ la **plus grande** [[Conorme triangulaire]].

### Démonstration
Toute t-norme $\top$ vérifie $\top(x, 1) = x$, $\top(1, y) = y$ et $\top(x, y) \geq 0$. Elle est donc supérieure ou égale à $\top_W$ en tout point.

# Remarque
Les extrêmes sont donc : [[Minimum et maximum]] pour la plus grande t-norme et la plus petite t-conorme, Weber pour la plus petite t-norme et la plus grande t-conorme.
