#adm-7

# Définition

Dans un [[Modèle graphique]], les variables $x_1, \dots, x_n$ se répartissent en variables observées et variables non observées. L'inférence consiste à déterminer les lois a posteriori de toutes les variables non observées sachant celles qui sont observées, c'est-à-dire les quantités

$$
\mathbb{P}[x_i \mid \mathbf{x}_{\text{obs}}]
$$

pour chaque variable non observée $x_i$, où $\mathbf{x}_{\text{obs}}$ désigne le vecteur des variables observées.

Ces lois a posteriori se déduisent de la loi jointe $\mathbb{P}[\mathbf{x}]$ du modèle : les variables non observées autres que $x_i$ sont marginalisées, puis le résultat est normalisé.

# Remarque

L'objectif est de disposer d'algorithmes génériques, qui tirent parti de la structure non dirigée du graphe. Le [[Graphe de facteurs]] fournit cette structure de travail ; un [[Réseau bayésien]] s'y ramène par [[Moralisation d'un graphe orienté|moralisation]].

Les approches d'inférence se rangent en trois familles.

- **Inférence exacte** : calcul exact des lois a posteriori, qui fonctionne bien dans des cas particuliers ou sur des structures assez simples ; voir [[Élimination de variables]], [[Passage de messages sur une chaîne]], [[Algorithme somme-produit]] et [[Inférence par arbre de jonction]].
- **Approches de Monte-Carlo** : recours à l'échantillonnage pour calculer les lois a posteriori et les marginalisations, l'échantillonnage de Gibbs étant l'usage courant dans ce cadre.
- **Méthodes variationnelles** : simplifications du modèle, qui conduisent à une solution approchée.
