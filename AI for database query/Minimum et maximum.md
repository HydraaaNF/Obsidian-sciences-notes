# Définition
Le couple $(\min, \max)$ est le couple de **Zadeh** :

$$
\top(x, y) = \min(x, y) \qquad \bot(x, y) = \max(x, y)
$$

Le minimum est la **plus grande** [[Norme triangulaire]] et le maximum la **plus petite** [[Conorme triangulaire]]. Cette extrémalité découle du bornage $\top(x, y) \leq \min(x, y)$ et $\bot(x, y) \geq \max(x, y)$.

# Propriétés
Le couple min / max préserve le plus grand nombre de propriétés usuelles :
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

# Exemple
Sur l'échelle ordinale *mauvais < médiocre < moyen < bon < excellent* :
- $\min(\text{médiocre}, \text{excellent}) = \text{médiocre}$
- $\max(\text{moyen}, \text{bon}) = \text{bon}$

# Remarque
Inconvénient du minimum : l'[[Effet de masque du minimum]]. Pondération : [[Minimum et maximum pondérés]].
