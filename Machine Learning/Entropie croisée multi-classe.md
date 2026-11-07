#ml-1

# Définition

Pour un échantillon $i$, le réseau produit $K$ probabilités en sortie par la [[Fonction softmax]], et l'on note $c_i$ la vraie classe de l'échantillon :

$$\hat{y}_i = \operatorname{softmax}(z_i)$$

Comme pour la [[Régression logistique|régression logistique]], la probabilité que le modèle donne la bonne réponse sur cet échantillon est la probabilité affectée à la vraie classe :

$$\hat{y}_{i,c_i}$$

L'**entropie croisée** est l'opposé du logarithme de cette probabilité, sommé sur tous les échantillons :

$$CE = -\sum_i \ln \hat{y}_{i,c_i} = -\sum_i \sum_{c=1}^K y_{i,c} \ln \hat{y}_{i,c}$$

où $y_i = (0, \dots, 1, \dots, 0)$ est la vérité écrite comme vecteur one-hot : seule la composante de la vraie classe vaut $1$, donc seule la probabilité affectée à la vraie classe subsiste dans la double somme.

# Exemple

Sur une photo montrant un chat, le modèle renvoie

$$\hat{y} = (0.24, 0.66, 0.10)$$

La perte de cet échantillon vaut

$$\ell = -\ln 0.24 = 1.42$$

Si le modèle donnait plutôt $\mathbb{P}(\text{chat}) = 0.9$, la perte tomberait à

$$\ell = -\ln 0.9 = 0.11$$

# Remarque

- Pour $K = 2$, la perte redonne l'[[Entropie croisée binaire|entropie croisée binaire]].
- En [[Classification binaire|classification binaire]], la probabilité de la bonne réponse s'écrit $\hat{y}_i^{y_i} (1 - \hat{y}_i)^{1 - y_i}$ : une seule expression couvre les deux classes, sans test conditionnel.
- Le gradient de la perte par rapport aux scores est traité dans [[Gradient du couple softmax et entropie croisée]].
- L'implémentation de cette perte est traitée dans [[Entropie croisée multi-classe avec PyTorch]].
