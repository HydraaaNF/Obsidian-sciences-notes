# Énoncé
Soit $(\Omega, \mathcal{F}, p)$ un espace probabilisé et $\{A_i; i \in I\}$ un [[Système complet d'évènements|système complet d'évènements]] tel que $\forall i \in I, p(A_i) > 0$ alors $\forall A \in \mathcal{F}, \forall j \in I, p(A_j|A) = \frac{p(A|A_j)p(A_j)}{\sum_{i \in I} p(A|A_i)p(A_i)}$

# Exemple
Trois machines $M_1$, $M_2$ et $M_3$ produisent des vis. $M_1$ produit en moyenne 0,3 % de vis défectueuses, $M_2$ 0,8 %, et $M_3$ 1 %. On mélange 1000 vis dans un sac : 500 de $M_1$, 350 de $M_2$, 150 de $M_3$. On tire une vis au hasard dans le sac : elle est défectueuse ! Quelle est la probabilité qu'elle provienne de $M_1$ ?

$$\mathbb{P}[M_1] = 0{,}5 \qquad \mathbb{P}[M_2] = 0{,}35 \qquad \mathbb{P}[M_3] = 0{,}15$$
$$\mathbb{P}[D|M_1] = 0{,}003 \qquad \mathbb{P}[D|M_2] = 0{,}008 \qquad \mathbb{P}[D|M_3] = 0{,}15$$

$$\mathbb{P}[M_1|D] = \frac{\mathbb{P}[D|M_1]\mathbb{P}[M_1]}{\mathbb{P}[D|M_1]\mathbb{P}[M_1] + \mathbb{P}[D|M_2]\mathbb{P}[M_2] + \mathbb{P}[D|M_3]\mathbb{P}[M_3]} \approx 5{,}6\%$$

