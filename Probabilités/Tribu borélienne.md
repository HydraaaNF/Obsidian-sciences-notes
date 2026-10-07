# Définition

On appelle **tribu borélienne** de $\mathbb{R}^{d}$ la [[Tribu]] engendrée par les ouverts de $\mathbb{R}^{d}$, c'est-à-dire la plus petite tribu de parties de $\mathbb{R}^{d}$ contenant les ouverts de $\mathbb{R}^{d}$. On la note $\mathcal{B}(\mathbb{R}^{d})$. Tout élément de cette tribu est appelé **borélien** de $\mathbb{R}^{d}$.

Si $A$ est un borélien de $\mathbb{R}^{d}$, on appelle **tribu borélienne de $A$** l'ensemble des intersections de $A$ avec un borélien de $\mathbb{R}^{d}$. Elle est notée $\mathcal{B}(A)$.

# Exemple

Considérons l'expérience aléatoire consistant à mesurer la durée de vie d'un composant électronique. L'ensemble $\Omega$ des résultats possibles de l'expérience est $\mathbb{R}^{+} = [0, +\infty[$. C'est un intervalle : il n'est pas dénombrable, on dit qu'on est dans le cas continu des probabilités, celui des [[Probabilité à densité|probabilités à densité]].

La tribu $\mathcal{F}$ associée à l'[[Espace probabilisé]] modélise l'ensemble des évènements : elle doit contenir au moins les intervalles inclus dans $\mathbb{R}^{+}$, afin de pouvoir considérer des évènements tels que « le composant a une durée de vie supérieure à $t$ », soit $[t, +\infty[$, ou « le composant a une durée de vie comprise entre $t_1$ et $t_2$ », soit $[t_1, t_2]$. On choisit donc comme tribu la plus petite tribu sur $\Omega = \mathbb{R}^{+}$ contenant les intervalles inclus dans $\mathbb{R}^{+}$ : c'est la tribu engendrée par les intervalles de $\mathbb{R}^{+}$.

Cette tribu contient tout sous-ensemble de $\mathbb{R}^{+}$ pouvant s'obtenir par une suite d'opérations prises parmi la réunion ou l'intersection dénombrable et le passage au complémentaire à partir d'intervalles de $\mathbb{R}^{+}$. Elle est en réalité engendrée par les seuls intervalles **ouverts** de $\mathbb{R}^{+}$ : par exemple,

$$]t_1, t_2] = \bigcap_{n \in \mathbb{N}^{*}} ]t_1, t_2 + \frac{1}{n}[.$$

C'est cette tribu, engendrée par les intervalles ouverts de $\mathbb{R}^{+}$, que l'on appelle par définition la **tribu borélienne de $\mathbb{R}^{+}$** :

$$\mathcal{F} = \mathcal{B}(\mathbb{R}^{+}).$$
