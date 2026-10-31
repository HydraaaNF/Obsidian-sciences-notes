# Définition
L'opérateur **OWA** (*Ordered Weighted Averaging*), proposé par Ronald Yager, affecte les poids **dynamiquement**. On construit le vecteur des valeurs $\mu_{E_1}(x), \ldots, \mu_{E_n}(x)$ trié par ordre **décroissant** : $w_1$ s'applique à la plus grande valeur, $w_2$ à la deuxième plus grande, …, $w_n$ à la plus petite.

$$
\mu_{\operatorname{OWA}(E_1, \ldots, E_n;\, W)}(x) = \sum_{i=1}^{n} w_i \, \mu'_{i}(x)
$$

où $\mu'_{i}(x)$ est la $i$-ème plus grande valeur parmi $\mu_{E_1}(x), \ldots, \mu_{E_n}(x)$.

# Propriétés
- L'opérateur est **croissant** par rapport à chaque argument $\mu_{E_i}(x)$.
- Son résultat est compris entre le **minimum** et le **maximum** des valeurs en entrée.
- Le minimum, le maximum et la moyenne arithmétique s'obtiennent avec des poids appropriés :
  - $W_{\min} = \langle 0, \ldots, 0, 1 \rangle$
  - $W_{\max} = \langle 1, 0, \ldots, 0 \rangle$
  - $W_{\operatorname{moy}} = \langle 1/n, \ldots, 1/n \rangle$

# Exemple
Soient $E_1 = \{0{,}4/a,\; 0{,}8/b\}$, $E_2 = \{1/a,\; 0{,}2/b\}$, $E_3 = \{1/b\}$ et $W = \langle 0{,}2,\; 0{,}5,\; 0{,}3 \rangle$.

| | moyenne pondérée | OWA |
| --- | --- | --- |
| $a$ | $0{,}58$ | $0{,}4$ |
| $b$ | $0{,}56$ | $0{,}66$ |

Détail :
- moyenne pondérée, $a$ : $0{,}2 \times 0{,}4 + 0{,}5 \times 1 + 0{,}3 \times 0 = 0{,}58$
- moyenne pondérée, $b$ : $0{,}2 \times 0{,}8 + 0{,}5 \times 0{,}2 + 0{,}3 \times 1 = 0{,}56$
- OWA, $a$ : valeurs triées $(1,\; 0{,}4,\; 0)$, donc $0{,}2 \times 1 + 0{,}5 \times 0{,}4 + 0{,}3 \times 0 = 0{,}4$
- OWA, $b$ : valeurs triées $(1,\; 0{,}8,\; 0{,}2)$, donc $0{,}2 \times 1 + 0{,}5 \times 0{,}8 + 0{,}3 \times 0{,}2 = 0{,}66$

# Remarque
À comparer avec la [[Moyenne pondérée d'ensembles flous]]. C'est un cas d'[[Opérateur de compromis]].
