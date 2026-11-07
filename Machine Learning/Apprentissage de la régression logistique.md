#ml-1

# Modèle

Entraîner la [[Régression logistique|régression logistique]], c'est chercher le triplet de paramètres $(a^*, b^*, c^*)$ qui minimise l'erreur sur les données observées :

$$(a^*, b^*, c^*) = \operatorname*{argmin}_{(a,b,c)} \left( -LL(a, b, c) \right)$$

où $LL$ désigne la log-vraisemblance du modèle. Le problème reste un problème d'optimisation, toujours résolu par la [[Descente de gradient]] : c'est le même algorithme que pour la [[Régression linéaire]], seule la perte change.

# Algorithme

À chaque pas, deux éléments entrent en jeu :

- le taux d'apprentissage $\alpha$ ;
- le gradient de la perte, une dérivée partielle par paramètre.

Pour la régression logistique, le gradient de l'opposé de la log-vraisemblance au point courant s'écrit

$$\nabla(-LL)(a_t, b_t, c_t) = \left( \frac{\partial(-LL)}{\partial a}, \frac{\partial(-LL)}{\partial b}, \frac{\partial(-LL)}{\partial c} \right)(a_t, b_t, c_t)$$

et la mise à jour déplace tous les paramètres à la fois :

$$(a_{t+1}, b_{t+1}, c_{t+1}) = (a_t, b_t, c_t) - \alpha \times \nabla(-LL)(a_t, b_t, c_t)$$

Le vecteur complet est calculé par `autograd`, sans dériver chaque composante à la main : voir [[Différenciation automatique]].

# Remarque

- Avec un seul paramètre, la règle se réduit à $a_{t+1} \leftarrow a_t - \alpha \times \frac{\partial L}{\partial a}(a_t)$. Plus la pente est raide, plus le déplacement est grand ; le signe moins est ce qui en fait une descente ; $\alpha$ règle la vitesse globale de l'apprentissage.
- La perte retenue ici n'est pas la perte quadratique : c'est l'opposé de la log-vraisemblance, dont la forme est détaillée dans [[Entropie croisée binaire]]. Changer de perte ne change pas l'algorithme, seulement les dérivées à calculer.
