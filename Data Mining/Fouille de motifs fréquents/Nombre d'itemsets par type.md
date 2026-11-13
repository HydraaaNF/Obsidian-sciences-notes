#dmv-frequent_itemsets_mining

# Propriétés

Pour un seuil de support minimum fixé, les trois familles d'[[Itemset fréquent|itemsets fréquents]] d'une base s'emboîtent par inclusion, de la plus condensée à la plus détaillée :

$$MFI \subseteq CFI \subseteq FI$$

où $FI$ est l'ensemble des itemsets fréquents, $CFI$ celui des [[Itemsets fréquents fermés|itemsets fréquents fermés]] et $MFI$ celui des [[Itemsets fréquents maximaux|itemsets fréquents maximaux]].

Une inclusion ne peut qu'augmenter le nombre d'éléments, d'où l'encadrement des cardinaux :

$$|MFI| \le |CFI| \le |FI|$$

Ces cardinaux restent bornés par la taille du [[Treillis des itemsets|treillis]] : une base de $n$ items n'admet que $2^n$ itemsets, itemset vide compris.

L'écart entre $|FI|$ et $|CFI|$ mesure la redondance éliminée par le passage aux fermés : tout itemset fréquent qui n'est pas fermé partage son tidlist, donc son [[Support d'un itemset|support]], avec un itemset strictement plus grand. Comme $CFI$ contient exactement un itemset par classe d'équivalence de tidlist non vide, le rapport $|FI| / |CFI|$ s'interprète comme la taille moyenne d'une classe.

# Exemple

Base de six transactions sur cinq items, au seuil de support minimum $\varepsilon = 2$ :

| Tid | Transaction |
| :--- | :--- |
| 1 | A B C D E |
| 2 | A B C E |
| 3 | C |
| 4 | B C |
| 5 | A B C D |
| 6 | A B C |

Le treillis compte $32$ itemsets, l'itemset vide servant de racine, et $23$ itemsets non vides sont fréquents. La répartition par taille montre que la fréquence se raréfie à mesure que les itemsets s'allongent :

| Taille $k$ | Itemsets de taille $k$ | Itemsets fréquents de taille $k$ |
| :---: | :---: | :---: |
| 1 | 5 | 5 |
| 2 | 10 | 9 |
| 3 | 10 | 7 |
| 4 | 5 | 2 |
| 5 | 1 | 0 |
| Total des itemsets non vides | 31 | 23 |

Les $23$ itemsets fréquents se répartissent en cinq classes de tidlist, une par itemset fermé, et deux seulement sont maximaux :

- $|FI| = 23$ : tous les itemsets non vides de support au moins $2$ ;
- $|CFI| = 5$ : $C$, $BC$, $ABC$, $ABCD$ et $ABCE$ ;
- $|MFI| = 2$ : $ABCD$ et $ABCE$.

Le passage de $FI$ à $CFI$ divise le nombre d'itemsets par $4{,}6$ environ, et celui de $FI$ à $MFI$ par $11{,}5$ environ : $MFI$ ne retient plus que $2{,}5$ fois moins d'itemsets que $CFI$.

```chart
type: bar
labels: ["FI", "CFI", "MFI"]
series:
  - title: Itemsets fréquents
    data: [23, 5, 2]
```

# Interprétation

Le cardinal d'une famille mesure le volume de résultats que la fouille doit produire et que l'analyste doit ensuite parcourir :

- $FI$ énumère toutes les combinaisons fréquentes, sous-ensembles d'un même motif compris, ce qui accumule une forte redondance aux faibles seuils ;
- $CFI$ ne conserve qu'un représentant par classe de tidlist, soit un motif par ensemble d'occurrences distinct, ce qui élimine la redondance sans perdre aucun support ;
- $MFI$ ne conserve que les motifs sans sur-ensemble fréquent, d'où le volume le plus faible des trois.

Le phénomène se vérifie sur des bases réelles : en portant le logarithme décimal du nombre d'itemsets en fonction du support minimum absolu, sur quatre bases, les trois courbes décroissent et ne se croisent jamais, la courbe de $FI$ restant au-dessus de celle de $CFI$, elle-même au-dessus de celle de $MFI$. L'écart entre les familles s'étend de moins d'un ordre de grandeur aux seuils élevés à plus de trois ordres de grandeur aux seuils faibles, et c'est entre $FI$ et $MFI$ qu'il est le plus large.

Le choix d'une famille est donc un arbitrage entre volume et information : $FI$ seul donne tous les supports mais son volume croît très vite quand le seuil baisse, $MFI$ réduit ce volume au prix de la perte des supports, $CFI$ se place entre les deux en restituant le support de chaque itemset. Voir [[Limites des itemsets fréquents]].

# Remarque

Sur l'exemple, les trois inclusions sont strictes, $2 < 5 < 23$. Elles peuvent dégénérer en égalités quand tout itemset fréquent est maximal, situation atteinte à seuil très élevé ou sur une base dont les motifs fréquents sont deux à deux incomparables : les cardinaux se rejoignent alors et la compression ne rapporte plus rien.

Les trois cardinaux dépendent du seuil retenu et non de la seule base : baisser $minsup$ fait croître $|FI|$ beaucoup plus vite que $|MFI|$, puisqu'un itemset nouveau y entre souvent accompagné de tous ses sous-ensembles déjà présents dans $FI$.
