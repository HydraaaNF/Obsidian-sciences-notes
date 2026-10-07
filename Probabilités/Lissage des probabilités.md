# Définition

Le **lissage des probabilités** (*discounting*) consiste à emprunter de la masse de probabilité aux événements observés et à la redistribuer aux événements non observés, de la façon la plus astucieuse possible.

# Propriétés

Méthodes de discounting :

- lissage de Laplace (add-one) : $c^*(hw) = c(hw) + 1$ ;
- absolute discounting : $c^*(hw) = \max(c(hw) - \delta, 0)$ ;
- lissage de Kneser-Ney : $c^*(hw) = \max(c(hw) - \delta_h, 0)$ ;
- discounting de Good-Turing : $c^*(hw) = (c(hw) + 1) \frac{n_{c(hw)+1}}{n_{c(hw)}}$ ;
- et autres méthodes.

# Interprétation

Le passage du lissage de Laplace à la loi de Dirichlet équivaut à une estimation [[Estimateur du maximum a posteriori|au maximum a posteriori]] (MAP) :

$$\mathbb{P}[w; d] = \frac{c(w, d) + 1}{\sum_v (c(v, d) + 1)} \longrightarrow \frac{c(w, d) + \lambda \mathbb{P}[w]}{\sum_v (c(v, d) + \lambda \mathbb{P}[v])}$$

# Remarque

Le lissage complète l'[[Estimation par maximum de vraisemblance d'un modèle de Markov|estimation par maximum de vraisemblance d'un modèle de Markov]] en redistribuant de la masse de probabilité aux événements non observés. Il est nécessaire en pratique pour les distributions de fréquences qui suivent la [[Loi de Zipf]].
