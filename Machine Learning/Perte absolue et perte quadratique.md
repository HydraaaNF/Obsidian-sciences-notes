#ml-1

# Définition

Pour un échantillon $(x, y)$ et la prédiction $\hat{y} = f(x)$ d'un modèle de régression, deux [[Fonction de perte|pertes]] par échantillon sont d'usage :

- perte absolue : $\ell(\hat{y}, y) = |\hat{y} - y|$ ;
- perte quadratique : $\ell(\hat{y}, y) = (\hat{y} - y)^2$.

La perte totale sur un jeu de données est la somme des pertes par échantillon :

$$L = \sum_i \ell\left(f(x_i), y_i\right)$$

Elle est fonction des paramètres du modèle, non des données.

# Exemple

Trois échantillons :

| $i$ | $x_i$ | $y_i$ |
| :--- | :---: | :---: |
| 0 | 1 | 1 |
| 1 | 2 | 4 |
| 2 | 4 | 7 |

Avec les valeurs initiales $(a_0, b_0) = (1, 1)$ du modèle affine $f_{a,b}(x) = ax + b$ de la [[Régression linéaire]], les prédictions valent :

- $f(x_0) = 1 \times 1 + 1 = 2$ ;
- $f(x_1) = 1 \times 2 + 1 = 3$ ;
- $f(x_2) = 1 \times 4 + 1 = 5$.

Les pertes correspondantes, échantillon par échantillon puis au total :

| perte | absolue | quadratique |
| :--- | :---: | :---: |
| $\ell(\hat{y}_0, y_0)$ | 1 | 1 |
| $\ell(\hat{y}_1, y_1)$ | 1 | 1 |
| $\ell(\hat{y}_2, y_2)$ | 2 | 4 |
| $L$ | **4** | **6** |

Deux pertes, deux nombres, et bientôt deux optimums différents.

# Modèle

Simplification à un seul paramètre $a$ : le modèle s'écrit $f_a(x) = ax$, et la perte totale devient une fonction de $a$ seul, ce qui permet d'observer comment $L$ varie avec ce paramètre.

Perte absolue :

$$L(a) = |a - 1| + |2a - 4| + |4a - 7|$$

Perte quadratique :

$$L(a) = (a - 1)^2 + (2a - 4)^2 + (4a - 7)^2$$

La courbe de la perte absolue est linéaire par morceaux ; celle de la perte quadratique est une parabole.

# Remarque

- Les deux courbes n'ont pas le même minimum : pour la perte absolue $a^* = 1{,}75$ et $L = 1{,}25$, pour la perte quadratique $a^* \approx 1{,}76$ et $L \approx 0{,}81$.
- Choisir la perte change donc le modèle obtenu.
- Il faut regarder la forme, pas seulement le minimum :
  - la perte absolue présente un coin à l'optimum, où elle n'est pas dérivable ;
  - la perte quadratique est lisse partout, et sa dérivée s'annule à l'optimum.
- Une perte doit être différentiable, ce qui rend la perte quadratique le choix par défaut en régression et permet à la [[Descente de gradient]] de suivre sa pente.
- Le prix à payer : la perte quadratique est la plus sensible aux valeurs aberrantes.
- Moyennée sur les échantillons, la perte absolue donne l'[[Écart absolu moyen]] et la perte quadratique l'[[Erreur quadratique moyenne]] de prédiction, à ne pas confondre avec l'erreur quadratique moyenne d'un estimateur.
