# Définition
Toute [[Norme triangulaire]] est associée à une [[Conorme triangulaire]] par des relations de **dualité**, analogues aux lois de De Morgan et fondées sur le [[Complément d'un ensemble flou|complément]] $x \mapsto 1 - x$ :

$$
\top(x, y) = 1 - \bot(1 - x,\; 1 - y)
$$

$$
\bot(x, y) = 1 - \top(1 - x,\; 1 - y)
$$

# Interprétation
Ces relations correspondent aux **lois de De Morgan** pour les ensembles flous :

$$
\overline{E \cap F} = \bar{E} \cup \bar{F} \qquad\text{et}\qquad \overline{E \cup F} = \bar{E} \cap \bar{F}
$$

# Remarque
Un couple $(\top, \bot)$ vérifiant ces relations est dit **dual**.

# Exemple
Couples duaux usuels :

| t-norme | t-conorme duale | Nom |
| --- | --- | --- |
| $\min(x, y)$ | $\max(x, y)$ | Zadeh ([[Minimum et maximum]]) |
| $xy$ | $x + y - xy$ | probabiliste ([[Produit et somme probabiliste]]) |
| $\max(x + y - 1,\; 0)$ | $\min(x + y,\; 1)$ | Łukasiewicz ([[Norme et conorme de Łukasiewicz]]) |
| $\top_W$ | $\bot_W$ | Weber ([[Norme et conorme de Weber]]) |
