#dmv-pattern_mining_with_information_theory

# Définition

La **complexité de Kolmogorov** d'une chaîne est la longueur du plus petit programme qui génère cette chaîne puis s'arrête.

$$K(s) = \min \big\{ |p| \mid p \text{ génère } s \text{ puis s'arrête} \big\}$$

# Propriétés

La complexité de Kolmogorov est la compression ultime :

- elle reconnaît et exploite toute structure présente dans la chaîne ;
- elle n'est pas calculable.

# Remarque

Parce qu'elle n'est pas calculable, elle ne peut pas servir de critère directement applicable : elle désigne la longueur de description idéale, pas un moyen de l'atteindre.

Les approches par compression s'en approchent avec des longueurs de description effectivement calculables, en minimisant $L(M) + L(D \mid M)$ sur une famille de modèles fixée : c'est le [[Compromis entre longueur du modèle et longueur des données]] du [[Principe de la longueur minimale de description]].
