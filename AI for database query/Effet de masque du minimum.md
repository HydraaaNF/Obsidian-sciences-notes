# Définition
Le minimum a un **effet de masque** : le degré global est fixé par le critère le moins bien satisfait, et le reste est ignoré.

# Exemple
Requête : *voiture d'occasion bon marché et puissante*.

| | prix | puissance |
| --- | --- | --- |
| $t_1$ | $0{,}4$ | $1$ |
| $t_2$ | $0{,}4$ | $0{,}4$ |

- Avec $\min$ : $t_1$ et $t_2$ obtiennent le même degré $0{,}4$.
- Avec le produit : $t_1$ obtient $0{,}4$ et $t_2$ obtient $0{,}16$, donc $t_1$ est meilleur.

# Remarque
Le produit ([[Produit et somme probabiliste]]) évite cet effet. Le minimum reste néanmoins attractif pour d'autres raisons (voir [[Minimum et maximum]]).
