# Propriétés
Il est **impossible** de trouver un couple (t-norme, t-conorme) qui préserve toutes les propriétés de l'algèbre de Boole. En particulier, d'une part l'**idempotence**, d'autre part la **non-contradiction** et le **tiers exclu**, sont incompatibles.

# Exemple
Le minimum est idempotent ($\min(x, x) = x$) : pour $\mu_E(x) = 0{,}5$, on obtient $\mu_{E \cap \bar{E}}(x) = \min(0{,}5,\; 1 - 0{,}5) = 0{,}5 \neq 0$. La non-contradiction $E \cap \bar{E} = \emptyset$ n'est donc pas vérifiée avec le couple min / max.

# Interprétation
Le choix d'un couple est un **compromis** entre les propriétés conservées. Le couple [[Norme et conorme de Zadeh]] est celui qui préserve le plus grand nombre de propriétés usuelles.
