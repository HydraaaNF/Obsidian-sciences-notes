# Définition

Soit un caractère quantitatif $X$ observé sur $n$ [[Population statistique et caractère|individus]], donnant les observations $x_1, \dots, x_n$. La **fonction de répartition empirique** se construit à partir du tableau des fréquences cumulées des observations.

**Caractère quantitatif discret.** Les observations prennent les valeurs $m_1 < \dots < m_k$, d'effectifs $n_1, \dots, n_k$. La fréquence de la valeur $m_j$ est

$$f_j = \frac{n_j}{n}$$

son effectif cumulé est

$$N_j = \sum_{i=1}^j n_i$$

et sa fréquence cumulée vaut

$$F_j = \sum_{i=1}^j f_i = \frac{N_j}{n}.$$

À partir du tableau des fréquences cumulées, on définit la fonction de répartition empirique, notée $\overline{F}$ : pour tout $x$ réel,

$$\overline{F}(x) = \begin{cases} 0 & \text{si } x < m_1 \\ F_j & \text{si } m_j \leq x < m_{j+1} \\ 1 & \text{si } x \geq m_k \end{cases}$$

**Caractère quantitatif continu discrétisé.** Les observations d'un [[Caractère quantitatif continu|caractère quantitatif continu]] sont regroupées en classes $[m_j, m_{j+1}[$. De même que pour un [[Caractère quantitatif discret|caractère discret]], on peut établir le tableau des fréquences et des fréquences cumulées par classe : pour la classe $[m_j, m_{j+1}[$, la fréquence est définie par

$$f_j = \frac{n_j}{n}$$

et la fréquence cumulée par

$$F_j = \sum_{i=1}^j f_i .$$

À partir des fréquences cumulées, on définit la fonction

$$F(x) = \begin{cases} 0 & \text{si } x \leq m_1 \\ F_{j-1} + f_j * \frac{x - m_{j-1}}{m_j - m_{j-1}} & \text{si } m_{j-1} < x \leq m_j \\ 1 & \text{si } x > m_l. \end{cases}$$

dont le graphe donne le *polygone des fréquences cumulées*.

**Échantillon.** Soient $(x_1, \dots, x_n)$ les observations d'un [[Échantillon et échantillonnage|échantillon]] $(X_1, \dots, X_n)$ dont la loi mère a pour fonction de répartition $F$. On range les observations par ordre croissant et on note $(x_{(1)}, \dots, x_{(n)})$ le $n$-uplet ainsi obtenu. La fonction de répartition empirique $F_n$ associée à $(x_1, \dots, x_n)$ est définie par

$$F_n = \begin{cases} 0 & \text{si } x < x_{(1)} \\ \frac{1}{n} & \text{si } x = x_{(1)} \\ \frac{i}{n} & \text{si } x_{(i-1)} < x \leq x_{(i)} \text{ pour } i \in \{2, \dots, n\} \\ 1 & \text{si } x > x_{(n)} \end{cases}$$

# Interprétation

La fonction de répartition empirique est une approximation de la fonction de répartition de $X$ : elle se construit à partir du tableau des fréquences cumulées des observations. Pour un caractère quantitatif continu discrétisé, son graphe est le *polygone des fréquences cumulées* ; pour un échantillon, $F_n$ est une fonction discontinue.

# Remarque

La fonction de répartition empirique est l'analogue empirique de la [[Fonction de répartition]] : construite à partir des observations, elle approche la fonction de répartition de la loi de $X$. Dans le cadre du [[Test de Kolmogorov-Smirnov]], elle est comparée à une fonction de répartition théorique $F_0$.
