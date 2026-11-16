#dmv-subgroup_discovery

# Définition

Un sélecteur est la condition élémentaire d'un [[Motif de sous-groupe|motif de sous-groupe]] : il porte sur un seul attribut et restreint les individus retenus.

Sa forme dépend du [[Attribut et types d'attributs|type de l'attribut]].

Sur un attribut nominal, un sélecteur est une égalité à une valeur :
$$\text{attribut} = \text{valeur}$$

Sur un attribut ordinal ou numérique, un sélecteur est une appartenance à un intervalle :
$$\text{attribut} \in [\text{minValue}, \text{maxValue}]$$

# Interprétation

Un sélecteur décrit un sous-ensemble d'individus par une seule caractéristique : ceux dont l'attribut vaut la valeur fixée, ou ceux dont l'attribut tombe entre les deux bornes.

Le choix de la forme suit la nature de l'ordre porté par l'attribut :

- un attribut nominal n'a pas d'ordre, une valeur ne peut qu'être atteinte ou non, d'où l'égalité ;
- un attribut ordinal ou numérique est ordonné, deux valeurs voisines se ressemblent, d'où l'intervalle.

# Remarque

Un motif de sous-groupe combine plusieurs sélecteurs par conjonction, puis vise une propriété sur un attribut cible : voir [[Motif de sous-groupe]].
