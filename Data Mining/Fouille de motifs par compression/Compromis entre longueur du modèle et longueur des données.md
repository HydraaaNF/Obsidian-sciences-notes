#dmv-pattern_mining_with_information_theory

# Définition

Choisir un modèle, c'est arbitrer entre deux longueurs de description :

- $L(M)$, la longueur de description du modèle ;
- $L(D \mid M)$, la longueur de description des données encodées avec ce modèle.

Le compromis se lit sur la longueur totale

$$L(D, M) = L(M) + L(D \mid M)$$

et le meilleur modèle est celui qui minimise cette somme.

# Exemple

La base $D = a\,b\,c\,c\,a\,b\,c\,d\,a\,b\,c$ est décrite par trois modèles de plus en plus condensés.

- Le modèle $M''$ attribue un code propre à chaque item : $a$, $b$, $c$ et $d$ ont chacun le leur, et $D \mid M''$ compte 11 codes, un par symbole de la base.
- Le modèle $M$ réserve un code court au motif $abc$ et laisse un code propre à $c$ et à $d$ : $D \mid M$ ne compte plus que 5 codes, ceux des trois occurrences de $abc$, du $c$ isolé et du $d$ isolé.
- Le modèle $M'$ ramène la base à un unique motif de 11 symboles : $D \mid M'$ tient en 1 code, mais la table doit énumérer les onze symboles du motif, ce qui allonge la description du modèle.

| Modèle | Entrées de la table | Longueur de $D \mid M$ |
|---|---|---|
| $M''$ | un code par item : $a$, $b$, $c$, $d$ | 11 codes |
| $M$ | $abc$, $c$, $d$ | 5 codes |
| $M'$ | un motif unique de 11 symboles | 1 code |

# Remarque

Le meilleur compromis n'est ni le plus petit ni le plus grand des modèles : le modèle le plus fin a une table courte mais allonge les données encodées, tandis que le modèle le plus condensé réduit les données à un seul code au prix d'une table aussi longue que les données elles-mêmes.

Ce curseur est celui du [[Principe de la longueur minimale de description]] ; le calcul effectif des deux termes passe par la [[Longueur de description d'une table de codes]] et par la [[Taille totale d'un modèle et des données encodées]]. La borne idéale que ce compromis approxime est la [[Complexité de Kolmogorov]].
