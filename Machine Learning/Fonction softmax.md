#ml-1

# Définition

Pour $K$ classes, la couche de sortie du réseau compte $K$ neurones et produit un score par classe :

$$z = (z_1, \dots, z_K) = xA^\top + b$$

La probabilité d'une classe s'obtient en prenant l'exponentielle de son score, divisée par le total des exponentielles des scores :

$$\mathbb{P}(c \mid x) = \operatorname{softmax}(z)_c = \frac{e^{z_c}}{\sum_{k=1}^{K} e^{z_k}}$$

Chaque classe reçoit $e^{\text{son score}}$, divisé par le total. Les scores bruts $z$ s'appellent les logits.

# Propriétés

- Chaque probabilité est positive.
- Les probabilités somment à $1$ sur les classes : le softmax définit une distribution de probabilité sur les classes.
- L'ordre est conservé : le score le plus élevé reçoit la plus forte probabilité. Pour décider, il suffit donc de prendre l'argmax des scores, sans calculer le softmax.
- Ajouter la même constante à tous les scores ne change rien. D'où $K$ scores et $K - 1$ degrés de liberté seulement.
- Une différence de logits est un log-rapport de chances :

$$z_c - z_k = \ln \frac{\mathbb{P}(c \mid x)}{\mathbb{P}(k \mid x)}$$

# Exemple

La couche de sortie compte trois neurones et produit un score par classe :

$$z = (z_{\text{chat}}, z_{\text{chien}}, z_{\text{oiseau}}) = xA^\top + b$$

Les scores $z_c$, leurs exponentielles et les probabilités correspondantes valent :

| | chat | chien | oiseau | total |
| :--- | :---: | :---: | :---: | :---: |
| score $z_c$ | 1.0 | 2.0 | 0.1 | |
| $e^{z_c}$ | 2.72 | 7.39 | 1.11 | 11.21 |
| $\operatorname{softmax}(z)_c$ | 0.24 | 0.66 | 0.10 | 1 |

Ajouter $5$ à chaque score laisse les probabilités inchangées :

| | chat | chien | oiseau | total |
| :--- | :---: | :---: | :---: | :---: |
| score $z_c + 5$ | 6.0 | 7.0 | 5.1 | |
| $\operatorname{softmax}(z)_c$ | 0.24 | 0.66 | 0.10 | 1 |

Le chien garde la plus forte probabilité, et les probabilités ne dépendent pas des valeurs absolues des scores.

# Remarque

Pour deux classes, le softmax se réduit à la sigmoïde de la [[Régression logistique]]. Avec un score $z$ pour le chien et un score nul pour le chat :

$$\mathbb{P}(\text{chien}) = \frac{1}{1 + e^{-z}} = \frac{e^z}{e^z + 1} = \frac{e^z}{e^z + e^0}$$

Chaque classe reçoit l'exponentielle de son score divisée par le total :

$$\mathbb{P}(\text{chien}) = \frac{e^{z_{\text{chien}}}}{e^{z_{\text{chat}}} + e^{z_{\text{chien}}}}$$

$$\mathbb{P}(\text{chat}) = \frac{e^{z_{\text{chat}}}}{e^{z_{\text{chat}}} + e^{z_{\text{chien}}}}$$

Fixer $z_{\text{chat}} = 0$ ne coûte rien, puisque seul l'écart entre les deux scores compte :

$$\ln \frac{\mathbb{P}(\text{chien})}{\mathbb{P}(\text{chat})} = z_{\text{chien}} - z_{\text{chat}}$$

ce qui redonne le logit de la régression logistique.

La [[Régression logistique multinomiale]] est le modèle complet dont cette transformation fournit les probabilités a posteriori : un score linéaire par classe, normalisé sur l'ensemble des classes.

Le softmax est la transformation de sortie d'un classifieur multi-classe ; voir l'[[Entropie croisée multi-classe]] pour la perte associée et la [[Température d'un softmax]] pour l'effet d'un facteur d'échelle sur les scores.
