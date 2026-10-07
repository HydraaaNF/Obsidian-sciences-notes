# Définition

Pour obtenir un histogramme plus régulier, on peut recourir à deux techniques de lissage : la fenêtre glissante et, éventuellement, la pondération par un noyau. Il s'applique à l'histogramme d'un [[Caractère quantitatif continu|caractère quantitatif continu]].

**Fenêtre glissante.** Pour chaque valeur $x$, on compte la population (le nombre d'observations) dans l'intervalle

$$[x - \frac{\Delta}{2}, x + \frac{\Delta}{2}]$$

où $\Delta$ est la largeur de la fenêtre.

**Noyau.** On peut éventuellement pondérer différemment les observations de l'intervalle au moyen d'un noyau $K$ :

$$f(x) = \frac{1}{n\Delta} \sum_{i=1}^{n} K\left(\frac{x - x_i}{\Delta}\right)$$

où $x_1, \dots, x_n$ sont les observations.

# Interprétation

Le lissage remplace l'allure irrégulière de l'histogramme en classes par une courbe régulière : il met en évidence la forme d'ensemble de la distribution, par exemple deux sommets séparés par un creux.

Le paramètre $\Delta$ contrôle le lissage : plus $\Delta$ est grand, plus l'estimation est lisse (au risque de masquer des détails) ; plus $\Delta$ est petit, plus elle est fidèle aux données (mais bruitée).

# Remarque

L'histogramme lissé décrit la distribution le long de l'axe des valeurs ; la [[Fonction de répartition empirique]] en donne une autre lecture, par cumul des fréquences.
