# Définition
Pour obtenir un histogramme plus lisse qu'un simple découpage en classes, on peut utiliser :

**Fenêtre glissante** : compter la population dans tous les intervalles $[x - \frac{\Delta}{2}, x + \frac{\Delta}{2}[$ en faisant glisser $x$.

**Estimation à noyau** : pondérer différemment les échantillons de l'intervalle par une fonction noyau $K$ :
$$f(x) = \frac{1}{n\Delta}\sum_{i=1}^{n} K\left(\frac{x - x_i}{\Delta}\right)$$

# Interprétation
$\Delta$ contrôle le lissage : plus $\Delta$ est grand, plus l'estimation est lisse (mais risque de masquer des détails) ; plus $\Delta$ est petit, plus elle est fidèle aux données (mais bruitée).
