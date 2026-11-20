#ml-3

# Définition

Une loi d'échelle (*scaling law*) est une loi de puissance qui relie la perte de test d'un modèle à la quantité de ressource engagée dans son entraînement : données, paramètres ou puissance de calcul.

$$y(x) = a x^{-\gamma} + b$$

où $y$ est la perte de test, $x$ la quantité de données (ou le nombre de paramètres, ou la puissance de calcul), $\gamma$ la pente de la décroissance en échelle logarithmique et $b$ la perte qu'aucune quantité de données ne supprime.

# Loi

La perte de test décroît comme une loi de puissance de la ressource : plus on entraîne sur des données, plus le modèle en sait et mieux il généralise. La même forme vaut pour les paramètres et pour la puissance de calcul.

Le phénomène se vérifie dans six domaines, sur la perte réductible en fonction de la puissance de calcul en PF-days, chaque couleur dénotant la taille du modèle.

| Domaine | Panneau | Loi de puissance |
|---|---|---|
| Images | 8×8, loss per image | $\approx (C_c)^{-0.19}$ |
| Texte → Image | Text → Image | $\approx (C_c)^{-0.15}$ |
| Vidéo | Video | $\approx (C_c)^{-0.14}$ |
| Mathématiques | Math | $\approx (C_c)^{-0.14}$ |
| Image → Texte | Image → Text | $\approx (C_c)^{-0.16}$ |
| Langage | Language | $L = 2{,}57 \cdot C^{-0.048}$ |

Trois régularités se lisent sur ces courbes.

- En échelle log-log, la perte décroît linéairement : chaque modalité suit une loi de puissance en la puissance de calcul.
- Le langage est la courbe la plus plate, avec un exposant de $-0.048$, les images la plus pentue, avec $-0.19$.
- Les courbes saturent vers un plateau irréductible à mesure que la taille du modèle augmente.

# Interprétation

L'exposant $\gamma$ mesure la vitesse à laquelle une modalité convertit du calcul supplémentaire en perte gagnée : les images, à $-0.19$, profitent bien plus vite du calcul que le langage, à $-0.048$. Le plateau $b$ fixe la limite que la ressource ne repousse pas.

Ces exposants fournissent le cadre quantitatif que mobilise la [[Loi de Chinchilla]] pour arbitrer entre taille du modèle et volume de données. Ils éclairent aussi la frontière entre [[Surapprentissage et sous-apprentissage]] : sous la pente, ajouter des données améliore la généralisation, au-delà elle ne fait plus que suivre le plateau. L'écart entre les pentes explique enfin pourquoi un même budget de calcul ne se traduit pas de la même façon selon la modalité, dans le paysage que décrit l'[[État de l'art des grands modèles de langage]].

# Remarque

Le tableau récapitulatif note $C_c$ la puissance de calcul, alors que les panneaux l'écrivent $C$, sauf celui des images qui écrit $x$ ; le panneau du langage nomme en outre $L$ la perte. La variable $x$ de la loi générale couvre indifféremment les trois lectures possibles de la ressource.

Sur la vidéo, deux relevés diffèrent d'un exposant, $-0.16$ et $-0.14$ ; la note retient $-0.14$, valeur portée par la légende du panneau.
