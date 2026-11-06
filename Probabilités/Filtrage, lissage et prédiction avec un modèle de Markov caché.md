# Définition

Dans un [[Modèle de Markov caché|modèle de Markov caché]], de nombreux problèmes, souvent traités en temps réel, se ramènent à prédire l'état $S_k$ à un instant donné $k$ connaissant seulement une partie des observations. La loi correspondante se note

$$\pi_{k\mid n} \doteq \mathbb{P}[S_k \mid O_1, \ldots, O_n]$$

Elle porte sur l'état de l'instant $k$ et conditionne par les $n$ premières observations : $k$ repère l'instant de l'état, $n$ le nombre d'observations retenues. Cette loi s'exprime à partir des quantités forward et backward, les [[Probabilités forward et backward|probabilités forward et backward]] $\alpha_i(k)$ et $\beta_i(k)$, où $i$ repère la valeur de l'état et $k$ l'instant ; selon le régime, l'une ou l'autre suffit, ou le produit des deux est nécessaire.

# Propriétés

Le régime de calcul est déterminé par la position de $n$ par rapport à $k$.

**Filtrage** ($n = k$) : les observations retenues vont jusqu'à l'instant de l'état,

$$\pi_{k\mid k} \doteq \mathbb{P}[S_k \mid O_1, \ldots, O_k] \propto \alpha_i(k)$$

**Lissage** ($n = k + l > k$, avec $l > 0$) : les observations retenues dépassent l'instant de l'état,

$$\pi_{k\mid n} \doteq \mathbb{P}[S_k \mid O_1, \ldots, O_{k+l}]$$

Le cas extrême est celui où toutes les observations sont disponibles ($n = T$) ; la loi lissée s'écrit alors avec la quantité notée $\gamma_i(t)$,

$$\pi_{k\mid T} = \gamma_i(t) \propto \alpha_i(k)\,\beta_i(k)$$

**Prédiction** ($n = k - l < k$, avec $l > 0$) : les observations retenues s'arrêtent avant l'instant de l'état,

$$\pi_{k\mid n} \doteq \mathbb{P}[S_k \mid O_1, \ldots, O_{k-l}]$$

Pour ces trois cas, les récurrences se dérivent directement de celles des quantités forward et backward.

# Interprétation

Les trois régimes se distinguent par la partie de la séquence utilisée pour estimer un même état.

- Le filtrage estime l'état courant au vu des observations passées et présentes, sans attendre la suite : c'est le régime du traitement en temps réel.
- Le lissage estime un état passé en exploitant les observations jusqu'à l'instant $k + l$, observations postérieures à $k$ comprises ; le cas $n = T$, qui retient toute la séquence, en est la forme complète.
- La prédiction estime un état futur à partir des seules observations déjà disponibles.

Chacune de ces lois est normalisée sur les valeurs possibles de l'état ; la quantité forward, seule dans le filtrage, cède la place au produit de la quantité forward et de la quantité backward dès que des observations postérieures à $k$ entrent en jeu.

# Remarque

- La constante de proportionnalité du filtrage est la probabilité de la séquence d'observations retenue, $\mathbb{P}[O_1, \ldots, O_k]$ ; celle du lissage au cas $n = T$ est $\mathbb{P}[O_1, \ldots, O_T]$. La loi $\gamma_i(t)$ est donc la loi conditionnelle de l'état $i$ à l'instant $t$ sachant la séquence complète, c'est-à-dire la [[Statistiques d'occupation d'un état|statistique d'occupation de l'état]].
- Dans $\gamma_i(t)$, l'instant est noté $t$ alors qu'il est noté $k$ dans $\alpha_i(k)$ et $\beta_i(k)$ : les deux écritures désignent la même loi, à la lettre près. L'indice $i$ repère toujours la valeur de l'état, et l'argument l'instant auquel cette valeur est considérée ; l'écriture $\gamma_k(i)$, qui place l'instant en indice et la valeur d'état en argument, est la même quantité avec les deux positions interverties.
- La même famille de messages se rencontre dans le formalisme du [[Passage de messages sur une chaîne|passage de messages sur une chaîne]], où l'écriture $\alpha_{i-1}(x_i)$ fait porter l'indice sur la position de la variable dont part le message et l'argument sur la valeur de la variable destinataire. Les quantités forward et backward indexent au contraire par la valeur de l'état et argumentent par l'instant : ce sont les mêmes messages, seuls changent ce que désignent l'indice et l'argument.
- Les récurrences du filtrage sont celles de l'[[Algorithme forward|algorithme forward]] ; le lissage mobilise en plus l'[[Algorithme backward|algorithme backward]], qui résume les observations postérieures à l'instant considéré.
