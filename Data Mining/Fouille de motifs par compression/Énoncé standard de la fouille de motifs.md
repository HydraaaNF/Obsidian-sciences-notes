#dmv-pattern_mining_with_information_theory

# Définition

Soit une base de données $db$, un langage de motifs $L$ et un ensemble de contraintes $C$. Le but de la fouille de motifs est l'ensemble de motifs $P \subseteq L$ tel que :
- chaque motif $p \in P$ satisfasse chaque contrainte $c \in C$ sur $db$ ;
- $P$ soit maximal.

Autrement dit, il s'agit de trouver tous les motifs qui satisfont les contraintes :

$$P = \{p \in L \mid \forall c \in C,\ p \text{ satisfait } c \text{ sur } db\}$$

# Interprétation

La maximalité porte sur l'ensemble $P$, non sur les motifs qui le composent : $P$ est maximal lorsqu'aucun motif de $L$ satisfaisant les contraintes ne peut y être ajouté, ce qui revient à exiger l'exhaustivité, tous les motifs conformes et rien qu'eux.

Le cadre se particularise aux [[Itemset fréquent|itemsets fréquents]] en prenant pour $L$ l'ensemble des itemsets construits sur les items de la base et pour $C$ la seule contrainte de [[Support d'un itemset|support]] minimal ; l'ensemble $P$ est alors celui de tous les itemsets dont le support atteint le seuil.

L'exhaustivité demandée est à l'origine des difficultés pratiques : elle produit un nombre de motifs qui croît très vite quand les contraintes se relâchent, ce qui est l'[[Explosion du nombre de motifs|explosion du nombre de motifs]], et elle ne coïncide pas avec ce que l'utilisateur attend, comme le montre l'[[Écart entre les motifs demandés et les motifs utiles|écart entre les motifs demandés et les motifs utiles]].

# Remarque

« Maximal » qualifie ici l'ensemble de motifs, au sens de l'inclusion des ensembles, et non les motifs eux-mêmes : un [[Itemsets fréquents maximaux|itemset maximal]] est un motif sans sur-ensemble fréquent, propriété d'un motif pris isolément, alors que la maximalité de $P$ interdit seulement d'oublier un motif conforme.
