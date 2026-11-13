#dmv-frequent_itemsets_mining

# Interprétation

Le calcul des [[Itemsets fréquents fermés|itemsets fermés]] ne consiste pas seulement à définir $CFI$, mais à l'engendrer à partir de la [[Items, itemsets et base de transactions|base de transactions]] et du seuil $minsup$. Deux voies s'opposent sur ce point : énumérer l'ensemble $FI$ des [[Itemset fréquent|itemsets fréquents]] puis filtrer, ou n'engendrer que les fermés au moyen d'opérations de fermeture.

**Approche par force brute.** L'approche par force brute s'appuie sur la base des motifs fréquents :

- énumérer tous les motifs fréquents de la base, par un algorithme d'extraction quelconque ;
- ne sortir que ceux qui sont fermés, c'est-à-dire écarter tout motif dont un sur-ensemble fréquent partage le même [[Support d'un itemset|tidlist]] ;
- payer le coût de l'énumération complète alors que la sortie ne retient qu'une partie des motifs trouvés.

Cette voie est inefficace la plupart du temps, parce que le travail porte sur $FI$ tout entier : l'énumération et le filtrage coûtent ce que coûte l'extraction de tous les motifs fréquents, alors que le résultat n'en garde qu'un sous-ensemble. Elle ne devient acceptable que dans un cas limite, lorsque $|FI|$ est très petit.

**Base de fermeture.** La base de fermeture renverse la démarche :

- ne calculer que les motifs fermés ;
- les engendrer par des opérations de fermeture, sans jamais énumérer les motifs non fermés ;
- explorer directement l'espace de ces motifs, décrit dans [[Fermeture d'un itemset et extension par fermeture]].

Cette voie peut être très efficace, puisque le parcours se restreint aux fermés : $CFI \subseteq FI$, donc $|CFI| \le |FI|$. Elle s'attaque ainsi à la redondance de $FI$, décrite dans [[Limites des itemsets fréquents]].

# Remarque

L'efficacité de la base de fermeture dépend de la stratégie d'énumération retenue, non du seul principe de fermeture. Les premières méthodes, telles que Closet et Charm, sont des méthodes à candidats, et suivent l'une des deux branches :

- calculer le plus possible d'itemsets fréquents non fermés ;
- faire une extension par fermeture, c'est-à-dire ajouter un item à un itemset fermé existant et prendre sa fermeture.

Ces méthodes doivent conserver en mémoire tous les itemsets fermés trouvés jusque-là, ce qui demande beaucoup de mémoire pendant l'exécution. La [[Recherche inverse des itemsets fermés|recherche inverse]], celle de [[Algorithme LCM|LCM]], parcourt le même espace en profondeur d'abord et n'a besoin d'aucune mémoire globale : le temps de calcul est rapide et l'usage mémoire faible. Ces variantes sont comparées dans [[Calcul efficace des itemsets fermés]].

Le choix entre les deux voies ne se réduit donc pas à un choix de principe. La force brute reste un point de comparaison utile, parce qu'elle montre que la difficulté vient de l'énumération des motifs fréquents eux-mêmes, et non du filtrage final : c'est cette énumération que la base de fermeture cherche à éviter.
