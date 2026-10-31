# Définition
**Hypothèse :** $Q$ est un [[Quantificateurs flous absolus et relatifs|quantificateur absolu]] **croissant** (extensible aux autres types).

Pour interpréter « $Q\ X$ sont $A$ », on considère les différentes [[Coupe de niveau alpha|coupes de niveau $\alpha$]] de $A$ et on calcule, pour chacune, $\mu_Q(\operatorname{card}(A_\alpha))$. Grâce à l'inclusion des coupes et à la monotonie de $Q$ : quand $\alpha$ diminue, $\mu_Q(\operatorname{card}(A_\alpha))$ ne peut pas diminuer.

Finalement :

$$
v = \max_{\alpha \in [0, 1]}\; \min\big(\alpha,\; \mu_Q(\operatorname{card}(A_\alpha))\big)
$$

# Interprétation
Cette formule cherche le **meilleur compromis** entre la qualité du représentant choisi pour $A$ ($\alpha$ le plus élevé possible) et son adéquation au quantificateur $Q$.

# Propriétés
- Cette approche garantit que $\forall \alpha \in [0, v],\; \mu_Q(\operatorname{card}(A_\alpha)) \geq v$.
- Elle généralise deux cas particuliers :
  - si $A$ est un ensemble booléen, la valeur de vérité de « $Q\ X$ sont $A$ » est $\mu_Q(\operatorname{card}(A))$ ;
  - si $Q$ est un quantificateur booléen « au moins $p$ », la valeur de vérité est la $p$-ième plus grande valeur parmi les $\mu_A(x)$.

# Remarque
Technique d'interprétation d'un [[Énoncé quantifié flou]], fondée sur l'intégrale de Sugeno. À comparer avec l'[[Interprétation de Zadeh d'un énoncé quantifié flou]].
