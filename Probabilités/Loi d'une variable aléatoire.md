# Définition

La **loi** d'une [[Variable aléatoire]] $X$ décrit la répartition des probabilités de ses valeurs possibles. Pour une variable aléatoire [[Variable aléatoire discrète|discrète]], elle est donnée par sa **fonction de masse** (pmf, *probability mass function*) :

$$p_X(x) = \mathbb{P}[X = x] = \mathbb{P}[A_x] = \mathbb{P}[\{\omega \in \Omega \text{ tel que } X(\omega) = x\}] = \sum_{X(\omega)=x} \mathbb{P}[\omega]$$

La fonction de masse associe à chaque valeur $x$ la probabilité que $X$ prenne cette valeur : elle détermine entièrement la loi de $X$.

# Exemple

Sur l'exemple du nombre de 1 obtenus en trois tirages (voir [[Variable aléatoire]]), la fonction de masse prend quatre valeurs :

```chart
type: bar
labels: ["0", "1", "2", "3"]
series:
  - title: p(x)
    data: [0.125, 0.375, 0.375, 0.125]
```

# Remarque

- Les probabilités $p_X(x)$ forment une [[Probabilité discrète]] sur l'ensemble des valeurs possibles de $X$.
- Pour une [[Variable aléatoire continue|variable aléatoire continue]], la loi est décrite par une [[Probabilité à densité|densité de probabilité]] et non par une fonction de masse.
- La [[Fonction de répartition]] est une autre description de la loi d'une variable aléatoire.
