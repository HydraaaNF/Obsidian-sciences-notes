# Définition
## Cas général
Soit $(\Omega, \mathcal{F}, \mathbb{P})$ un espace probabilisé. On a $$X : \Omega \to \mathbb{R}, \quad \omega \mapsto X(\omega)$$telle que $$\forall B \in \mathcal{B}(\mathbb{R}), [X \in B] \in \mathcal{F}$$
## Cas discret
Soit $(\Omega, \mathcal{F}, \mathbb{P})$ un espace probabilisé et $E$ un ensemble **fini ou dénombrable**. Toute application $X$ de $\Omega$ dans $E$ : $$X : \Omega \to E, \quad \omega \mapsto X(\omega)$$  vérifiant $$\forall k \in E, X^{-1}(\{k\}) \in \mathcal{F}$$ est appelée **variable aléatoire discrète**. L'ensemble $X(\Omega) \subset E$ est appelé **espace des états** de $X$.

## Cas continu
Soit $(\Omega, \mathcal{F}, \mathbb{P})$ un espace probabilisé. On a $$X : \Omega \to \mathbb{R}, \quad \omega \mapsto X(\omega)$$telle que $$\forall B \in \mathcal{B}(\mathbb{R}), [X \in B] \in \mathcal{F}$$
# Interprétation
Pour $x \in \mathbb{R}$, l'image réciproque $A_x = X^{-1}(\{x\}) = \{\omega \in \Omega : X(\omega)=x\}$ vérifie $A_x \cap A_y = \emptyset$ si $x \neq y$ et $\bigcup_{x \in \mathbb{R}} A_x = \Omega$. Travailler dans l'espace des évènements $(A_x)_x$ plutôt que dans $\Omega$ directement est souvent bien plus économique (ex. $2^n$ éléments de $\Omega$ ramenés à $n+1$ évènements pour $n$ épreuves de Bernoulli).