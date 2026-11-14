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

# Exemple
Sur l'univers $X = \{x_1, x_2, \ldots, x_7\}$, soit $Q$ = « au moins 4 » (quantificateur booléen) et

$$
A = \{0{,}7/x_1,\; 0{,}3/x_2,\; 1/x_3,\; 0{,}3/x_4,\; 0{,}8/x_5,\; 0{,}7/x_6,\; 0{,}3/x_7\}
$$

| $\alpha$ | $\operatorname{card}(A_\alpha)$ | $\mu_Q(\operatorname{card}(A_\alpha))$ | $\min(\alpha,\; \mu_Q(\operatorname{card}(A_\alpha)))$ |
| --- | --- | --- | --- |
| $0{,}3$ | $7$ | $1$ | $0{,}3$ |
| $0{,}7$ | $4$ | $1$ | $0{,}7$ |
| $0{,}8$ | $2$ | $0$ | $0$ |
| $1$ | $1$ | $0$ | $0$ |

Donc $v = 0{,}7$. Conformément au cas du quantificateur booléen, $0{,}7$ est la 4ᵉ plus grande valeur parmi les $\mu_A(x)$.

# Remarque
Technique d'interprétation d'un [[Énoncé quantifié flou]], fondée sur l'intégrale de Sugeno. À comparer avec l'[[Interprétation de Zadeh d'un énoncé quantifié flou]].
