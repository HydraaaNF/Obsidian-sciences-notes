# Définition

La fiabilité temporelle est notée $R(t) = P[X > t] = 1 - F(t)$, où $F(t)$ est la [[Fonction de répartition]].

## Taux de défaillance (Failure rate)
Le taux de défaillance $h(t)$ est la [[Probabilité conditionnelle]] de défaillance dans l'intervalle $[t, t+\Delta t[$, sachant que le composant a survécu jusqu'à l'instant $t$.
$$ h(t) = \frac{f(t)}{R(t)} $$

## Mean Time To Failure (MTTF)
Le temps moyen avant défaillance correspond à l'[[Espérance d'une variable aléatoire|espérance]] de la durée de vie $X$ du composant :
$$ MTTF = E[X] = \int_0^{\infty} R(t) dt $$

*Exemple :*
Pour une [[Variable aléatoire exponentielle]], $R(t) = e^{-\lambda t} \implies h(t) = \lambda \text{ et } MTTF = \frac{1}{\lambda}$

*Voir aussi : [[Fiabilité des systèmes]]*