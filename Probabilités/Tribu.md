# Définition
Soit $\Omega \neq \emptyset$. On dit que $\mathcal{F} \subset \mathcal{P}(E)$ est une tribu de parties de $\Omega$ si:
- $\Omega \in \mathcal{F}$
- $A \in \mathcal{F} \implies \bar{A} \in \mathcal{F}$
- $((\forall n \in \mathbb{N}) (A_n \in \mathcal{F})) \implies \bigcup_{n \in \mathcal{N}} A_n \in \mathcal{F}$

# Remarques
- Pour toute tribu $\mathcal{F}$ de parties de $\Omega$ on a $\mathcal{F} \subset \mathcal{P}(\Omega)$ et $\mathcal{P}(\Omega)$ est la plus grande tribu de parties de $\Omega$.
- La plus petite tribu de parties de $\Omega$ est $\{\emptyset, \Omega \}$.
- Lorsque $\Omega$ est fini ou dénombrable, on prendra $\mathcal{F} = \mathcal{P}(\Omega)$.
- Si $\Omega$ contient au moins 2 éléments, alors il existe un sous ensemble de A distinct de $\Omega$ et $\{\emptyset, A, \bar{A}, \Omega \}$ est la tribu engendrée par A.