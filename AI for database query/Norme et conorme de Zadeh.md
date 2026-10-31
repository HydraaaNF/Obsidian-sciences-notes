# Définition
Le couple de **Zadeh** est formé du minimum et du maximum :

$$
\top(x, y) = \min(x, y) \qquad \bot(x, y) = \max(x, y)
$$

Le minimum est la **plus grande** [[Norme triangulaire]] et le maximum la **plus petite** [[Conorme triangulaire]]. Cette extrémalité découle du bornage $\top(x, y) \leq \min(x, y)$ et $\bot(x, y) \geq \max(x, y)$.

# Propriétés
Le couple de Zadeh préserve le plus grand nombre de propriétés usuelles :
- **idempotence** ;
- **double distributivité** :
  - $E \cap (F \cup G) = (E \cap F) \cup (E \cap G)$
  - $E \cup (F \cap G) = (E \cup F) \cap (E \cup G)$
- **distributivité des [[Coupe de niveau alpha|coupes de niveau]]** :
  - $(E \cap F)_\alpha = E_\alpha \cap F_\alpha$
  - $(E \cup F)_\alpha = E_\alpha \cup F_\alpha$

# Interprétation
Avantages :
- calcul **facile** ;
- fonctionne sur une échelle **purement qualitative (ordinale)**.

Inconvénient : le minimum a un **effet de masque**. Le degré global est fixé par le critère le moins bien satisfait, et le reste est ignoré.

# Exemple
**Échelle ordinale.** Sur l'échelle *mauvais < médiocre < moyen < bon < excellent* :
- $\min(\text{médiocre}, \text{excellent}) = \text{médiocre}$
- $\max(\text{moyen}, \text{bon}) = \text{bon}$

**Effet de masque.** Requête : *voiture d'occasion bon marché et puissante*.

| | prix | puissance |
| --- | --- | --- |
| $t_1$ | $0{,}4$ | $1$ |
| $t_2$ | $0{,}4$ | $0{,}4$ |

- Avec $\min$ : $t_1$ et $t_2$ obtiennent le même degré $0{,}4$.
- Avec le produit ([[Norme et conorme probabilistes]]) : $t_1$ obtient $0{,}4$ et $t_2$ obtient $0{,}16$, donc $t_1$ est meilleur.

# Variante pondérée
Une version pondérée du couple de Zadeh a été proposée : $\operatorname{wmin}$ et $\operatorname{wmax}$.

Soient des poids (importances) $w_1, \ldots, w_n$ avec $\max_i w_i = 1$, associés aux ensembles flous $E_1, \ldots, E_n$ :

$$
\mu_{\operatorname{wmin}(E_1, \ldots, E_n;\, w_1, \ldots, w_n)}(x) = \min\big(\max(1 - w_1, \mu_{E_1}(x)),\; \ldots,\; \max(1 - w_n, \mu_{E_n}(x))\big)
$$

$$
\mu_{\operatorname{wmax}(E_1, \ldots, E_n;\, w_1, \ldots, w_n)}(x) = \max\big(\min(w_1, \mu_{E_1}(x)),\; \ldots,\; \min(w_n, \mu_{E_n}(x))\big)
$$

Pour $\operatorname{wmin}$, un poids $w_i = 1$ conserve le degré $\mu_{E_i}(x)$, alors qu'un poids $w_i = 0$ donne $\max(1, \mu_{E_i}(x)) = 1$, qui est neutre pour le minimum : le critère est ignoré.
