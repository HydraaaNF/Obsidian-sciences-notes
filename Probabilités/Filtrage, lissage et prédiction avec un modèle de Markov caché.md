# Définition

Dans un [[Modèle de Markov caché]], de nombreux problèmes, notamment en temps réel, se ramènent à prédire l'état $S_k$ connaissant une partie des observations, c'est-à-dire à calculer

$$\pi_{k|n} \doteq \mathbb{P}[S_k|O_1, \dots, O_n]$$

Cette quantité s'exprime à partir des [[Probabilités forward et backward|quantités forward et/ou backward]].

# Propriétés

Trois cas se distinguent selon la position de $n$ par rapport à $k$.

### Filtrage ($n = k$)

$$\pi_{k|k} \doteq \mathbb{P}[S_k|O_1, \dots, O_k] \propto \alpha_i(k)$$

### Lissage ($n = k + l > k$)

$$\pi_{k|n} \doteq \mathbb{P}[S_k|O_1, \dots, O_{k+l}]$$

Cas extrême $n = T$ :

$$\pi_{k|T} = \gamma_k(i) \propto \alpha_i(k)\beta_i(k)$$

### Prédiction ($n = k - l < k$)

$$\pi_{k|n} \doteq \mathbb{P}[S_k|O_1, \dots, O_{k-l}]$$

# Interprétation

- **Filtrage** ($n = k$) : estimer l'état $S_k$ à partir des observations disponibles jusqu'à cet instant, $O_1, \dots, O_k$.
- **Lissage** ($n = k + l > k$) : estimer l'état $S_k$ en tenant compte d'observations postérieures à $k$ ; au cas extrême $n = T$, toute la séquence est utilisée.
- **Prédiction** ($n = k - l < k$) : anticiper l'état $S_k$ à partir d'observations antérieures à $k$.

# Remarque

Les récurrences de ces trois quantités se déduisent directement de celles de l'[[Algorithme forward|algorithme forward]] et de l'[[Algorithme backward|algorithme backward]].

La [[Statistiques d'occupation d'un état|statistique d'occupation]] s'écrit $\gamma_k(i)$ : l'instant $k$ en indice, l'état $i$ en argument. La notation $\gamma_i(t)$, qui intervertit ces deux positions, est une inversion d'indices.
