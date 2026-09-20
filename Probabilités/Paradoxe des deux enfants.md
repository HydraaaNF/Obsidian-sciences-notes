# Énoncé
M. Smith a deux enfants. Au moins l'un des deux est un garçon. Quelle est la probabilité que les deux enfants soient des garçons ?

# Résolution
En modélisant l'univers par $\Omega = \{GG, GF, FG, FF\}$ équiprobable, et en conditionnant par l'évènement "au moins un garçon" ($GG, GF, FG$), on obtient
$$\mathbb{P}(GG \mid \text{au moins un garçon}) = \frac{1}{3}$$

# Interprétation
La réponse intuitive erronée est $\dfrac{1}{2}$, en assimilant à tort la question à "sachant que le premier (ou un enfant particulier, déjà identifié) est un garçon, quelle est la probabilité que l'autre le soit aussi ?" — ce qui donnerait bien $\dfrac{1}{2}$. La formulation initiale ("au moins un") conditionne sur un évènement plus large, qui inclut les deux ordres $GF$ et $FG$, d'où le résultat différent.

# Remarque
Ce paradoxe illustre, comme le [[Paradoxe de Monty Hall]], que la formulation exacte de l'évènement conditionnant change fondamentalement le résultat — une source d'erreur classique en dénombrement/[[Probabilité conditionnelle]].