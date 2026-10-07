# Théorème

Si la suite $(X_n)_{n \in \mathbb{N}}$ converge en [[Convergence en loi|loi]] vers $X$, alors la suite $(\Phi_{X_n}(\xi))_{n \in \mathbb{N}}$ des [[Fonction caractéristique|fonctions caractéristiques]] converge vers $\Phi_X(\xi)$ :

$$\forall \xi \in \mathbb{R}, \quad \lim_{n \to +\infty} \Phi_{X_n}(\xi) = \Phi_X(\xi)$$

Réciproquement, si pour tout réel $\xi \in \mathbb{R}$ la suite $(\Phi_{X_n}(\xi))_{n \in \mathbb{N}}$ converge simplement vers une fonction $\phi(\xi)$ et cette fonction $\phi$ est continue à l'origine, alors $\phi$ est la fonction caractéristique d'une certaine [[Variable aléatoire réelle|variable aléatoire réelle]] $X$ vers laquelle la suite $(X_n)$ converge en loi.

# Interprétation

La réciproque est énoncée sous une forme directement utile en pratique : pour établir qu'une suite de variables aléatoires converge en loi, il n'est pas nécessaire d'avoir une idée a priori de la variable aléatoire limite $X$. Il suffit de montrer que la suite $(\Phi_{X_n}(\xi))$ converge simplement vers une fonction $\phi$ continue à l'origine ; $\phi$ est alors automatiquement la fonction caractéristique d'une variable aléatoire, et la [[Convergence en loi|convergence en loi]] s'ensuit.
