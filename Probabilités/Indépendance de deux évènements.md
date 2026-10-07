# Définition

Deux [[Évènement|évènements]] $A$ et $B$ sont **indépendants** si et seulement si la [[Probabilité conditionnelle|probabilité conditionnelle]] de $A$ sachant $B$ est égale à la probabilité de $A$ :

$$\mathbb{P}[A|B] = \mathbb{P}[A].$$

La définition suivante est équivalente : deux évènements $A$ et $B$ sont indépendants si

$$\mathbb{P}[A \cap B] = \mathbb{P}[A]\mathbb{P}[B].$$

# Interprétation

La réalisation de $B$ ne modifie pas la probabilité de $A$ : savoir que $B$ s'est produit n'apporte aucune information sur la réalisation de $A$.

# Propriétés

- Si $A$ et $B$ sont indépendants, alors $\overline{A}$ et $B$ sont indépendants, $A$ et $\overline{B}$ sont indépendants, et $\overline{A}$ et $\overline{B}$ sont indépendants.
- L'indépendance n'est pas transitive : $A$ et $B$ peuvent être indépendants et $B$ et $C$ indépendants sans que $A$ et $C$ soient indépendants.

# Remarque

L'[[Indépendance mutuelle d'évènements|indépendance mutuelle]] généralise cette notion au cas de plus de deux évènements.
