# Loi

Une [[Variable aléatoire continue|variable aléatoire continue]] suit la loi uniforme continue sur un intervalle $[a, b]$ ($a < b$) lorsque sa [[Probabilité à densité|densité de probabilité]] y est constante :

$$f(x) = \frac{1}{b-a} \quad \text{pour } x \in [a, b]$$

$$f(x) = 0 \quad \text{sinon.}$$

# Interprétation

La loi uniforme continue est la loi a priori que l'on utilise lorsque rien n'est connu sur la variable aléatoire.

# Propriétés

Son [[Espérance d'une variable aléatoire|espérance]] et sa [[Variance|variance]] valent

$$\mathbb{E}(X) = \frac{a+b}{2}$$

$$\mathbb{V}(X) = \frac{(b-a)^2}{12}.$$

Sa [[Fonction caractéristique|fonction caractéristique]] vaut

$$\Phi_X(\xi) = \frac{e^{ib\xi} - e^{ia\xi}}{i(b-a)\xi}.$$

# Liens avec d'autres lois

La loi uniforme continue est le cas particulier de la [[Loi uniforme sur un domaine|loi uniforme sur un domaine]] où le domaine est un intervalle de la droite réelle.

- C'est la loi de la transformée affine de la loi uniforme sur $[0, 1]$ : si $U$ suit la loi uniforme sur $[0, 1]$, alors $a + (b-a)U$ suit la loi uniforme sur $[a, b]$.