# Énoncé
Trois portes ferment un studio de jeu : derrière l'une se trouve une voiture, derrière les deux autres une chèvre. Le candidat choisit une porte. L'animateur, qui connaît l'emplacement de la voiture, ouvre alors une des deux portes restantes en montrant systématiquement une chèvre, puis propose au candidat de changer de porte.

**Question** : le candidat a-t-il intérêt à changer de porte ?

# Résolution
En changeant de porte, la probabilité de gagner la voiture est $\dfrac{2}{3}$, contre $\dfrac{1}{3}$ en conservant son choix initial.

# Interprétation
L'erreur intuitive classique consiste à croire que les deux portes restantes ont une probabilité $\dfrac{1}{2}$ chacune une fois qu'une chèvre a été révélée. Ce raisonnement ignore que le choix de l'animateur n'est **pas aléatoire** : il est contraint par la connaissance de l'emplacement de la voiture, ce qui apporte de l'information et rompt la symétrie apparente entre les deux portes restantes.

# Remarque
Le **paradoxe de la boîte de Bertrand** est structurellement identique : trois boîtes contiennent chacune deux pièces (or/or, argent/argent, or/argent) ; on tire une pièce d'une boîte au hasard, elle est en or ; quelle est la probabilité que l'autre pièce de la même boîte soit également en or ? La réponse ($\frac{2}{3}$, et non $\frac{1}{2}$) repose sur exactement le même type de raisonnement conditionnel.