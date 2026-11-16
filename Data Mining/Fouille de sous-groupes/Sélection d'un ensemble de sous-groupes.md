#dmv-subgroup_discovery

# Définition

La sélection d'un ensemble de sous-groupes est la méthode qui, partant d'un ensemble de sous-groupes candidats, retient un ensemble divers de $k$ sous-groupes de haute qualité.

# Algorithme

```
entrée : un ensemble de sous-groupes candidats, un entier k
sortie : un ensemble divers de k sous-groupes de haute qualité

chercher dans l'ensemble candidat un ensemble divers de k sous-groupes
de haute qualité
retourner cet ensemble
```

# Interprétation

Les candidats se lisent comme une liste ordonnée par qualité décroissante ; les $k$ sous-groupes retenus ne sont pas les $k$ premiers de cette liste, mais $k$ sous-groupes répartis le long du classement, du meilleur candidat vers les moins bons.

La sélection porte donc sur un ensemble et non sur chaque sous-groupe isolément : deux candidats de qualité voisine qui décrivent la même population ne sont pas retenus tous les deux, ce qui laisse la place à des sous-groupes de qualité un peu plus faible mais porteurs d'une information différente. Le paramètre $k$ est le nombre de sous-groupes que l'ensemble retenu doit contenir.

# Exemple

Pour $k = 5$, cinq sous-groupes sont retenus parmi les candidats rangés par qualité décroissante. Les retenus sont dispersés sur toute l'étendue du classement au lieu d'être groupés en tête : la qualité décroît du premier au dernier retenu.

# Remarque

La méthode s'inspire des techniques de pattern set mining : elle raisonne sur un ensemble de motifs et non sur un motif à la fois.

Elle répond à la redondance du classement top-k : quand les $k$ premiers sous-groupes sont des variantes d'une même description, voir [[Limites du classement top-k]], un ensemble divers de même taille couvre davantage de cas et fait apparaître des [[Motif de sous-groupe|motifs]] qu'un classement strict laisse hors du résultat.

La démarche est analogue à la réduction par les [[Itemsets fréquents maximaux]] : dans les deux cas, la collection complète des motifs cède la place à un ensemble non redondant et bien plus compact. L'analogie s'arrête là : l'ensemble des itemsets maximaux est une représentation condensée équivalente de cette collection, alors que la sélection écarte des candidats pour n'en garder qu'un nombre fixé à l'avance.

Elle se distingue de la [[Recherche en faisceau diversifiée]], qui intègre la sélection directement dans la recherche au lieu de la faire porter sur un ensemble de candidats déjà formé, et se précise par les [[Degrés de diversité d'un ensemble de sous-groupes]], qui fixent ce que « divers » veut dire.
