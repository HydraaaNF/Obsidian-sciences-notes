#dmv-pattern_mining_with_information_theory

# Interprétation

Le nombre de motifs extraits dépend du seuil de [[Support d'un itemset|support]] retenu :
- un seuil élevé ne laisse que peu de motifs, mais ce sont les motifs bien connus, ceux qu'une analyse manuelle aurait déjà repérés ;
- un seuil bas fait apparaître une myriade de motifs.

Le seuil ne règle pas seulement ce qui compte comme motif récurrent : il gouverne aussi le coût de l'extraction, et trois difficultés apparaissent à mesure qu'il baisse :
- le temps de calcul devient important ;
- le nombre de motifs devient énorme ;
- le résultat contient une masse d'information redondante.

# Exemple

Le jeu de données Wine compte 178 lignes et 14 colonnes, et suffit à faire apparaître le phénomène : le nombre de motifs reste quasi nul tant que le support minimal est élevé, puis croît très vite quand le seuil baisse.

```chart
type: line
labels: ["120", "100", "80", "60", "50", "40", "30", "25", "20", "16", "13"]
series:
  - title: Nombre de motifs
    data: [0, 0, 1, 2, 20, 100, 360, 710, 1400, 2700, 4900]
```

Valeurs approximatives ; au-delà de 5000 motifs, la courbe sort du domaine représenté.

# Remarque

L'explosion ne tient pas qu'au nombre : beaucoup de motifs sont redondants. La fréquence est héréditaire, tout sous-ensemble d'un [[Itemset fréquent|itemset fréquent]] est fréquent, et un sous-ensemble porte souvent exactement le même support que son sur-ensemble, donc la même information. Énumérer tous les itemsets fréquents revient alors à répéter plusieurs fois la même information, ce qui est le constat développé dans [[Limites des itemsets fréquents]]. Deux représentations condensées suppriment cette redondance : les [[Itemsets fréquents fermés]], qui conservent le support des membres de chaque classe, et les [[Itemsets fréquents maximaux]], plus compacts mais sans cette information ; ces réductions relèvent des [[Familles d'approches pour maîtriser le nombre de motifs|familles d'approches pour maîtriser le nombre de motifs]].
