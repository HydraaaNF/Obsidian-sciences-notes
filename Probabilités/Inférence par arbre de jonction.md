#adm-7

# Algorithme

L'inférence par arbre de jonction applique l'[[Algorithme somme-produit]] à un [[Arbre de jonction]] de $\mathcal{G}$ pour mener l'inférence sur $\mathcal{G}$.

L'arbre de jonction n'est pas donné au départ : il se construit à partir de $\mathcal{G}$, et la méthode se décompose en cinq étapes.

1. Calculer le graphe moralisé lorsque l'entrée est un graphe orienté, par [[Moralisation d'un graphe orienté]].
2. Trianguler le graphe pour supprimer ses cycles sans corde.
3. Construire l'arbre de jonction du graphe triangulé, selon [[Construction d'un arbre de jonction]].
4. Faire passer les messages sur l'arbre de jonction, par somme-produit ou par max-produit.
5. Calculer les [[Lois marginales|marges]] des variables de $\mathcal{G}$ à partir de ces messages.

# Interprétation

Les deux premières étapes changent la topologie du graphe : ce sont des transformations du modèle, pas des détails de mise en œuvre.

- La moralisation transforme un [[Réseau bayésien|réseau bayésien]] en graphe non dirigé, dont la loi jointe se lit comme un produit de facteurs portés par les cliques.
- La triangulation ajoute des arêtes pour que chaque cycle de longueur au moins quatre possède une corde, ce qui rend les cliques maximales organisables en arbre.
- Les clusters de l'arbre portent alors les facteurs du graphe, et chaque nœud de $\mathcal{G}$ appartient à au moins un cluster.

Le graphe ramené à un arbre, chaque arête est parcourue une fois dans chaque sens : deux parcours suffisent pour que chaque cluster ait reçu un message de chacun de ses voisins. L'[[Algorithme somme-produit]] fournit ainsi la marge de chaque cluster, et les marges des variables de $\mathcal{G}$ s'en déduisent en sommant, dans le message d'un cluster, sur les autres variables de ce cluster.

La méthode réorganise l'[[Élimination de variables]] : le travail d'élimination n'est plus repris pour chaque variable dont on veut la marge, mais mutualisé sur l'arbre au profit de toutes les variables à la fois.

La variante max-produit ne calcule pas de marge : elle fournit la configuration la plus probable de l'ensemble des variables.

# Remarque

L'algorithme est générique : il s'applique à tout réseau bayésien et à tout graphe non dirigé, sans hypothèse sur leur structure, et il reste efficace pour des réseaux bayésiens ou des graphes raisonnablement bien formés.

Il devient en revanche rapidement intraitable quand la topologie du graphe se complexifie : la largeur de l'arbre de jonction explose, autrement dit la taille des clusters augmente, et le coût du calcul croît avec elle. La triangulation est donc l'étape critique, puisqu'elle détermine la largeur de l'arbre et, par là, le coût de toute l'inférence.

La méthode relève de l'[[Inférence dans un modèle graphique|inférence exacte]] : elle donne des marges exactes, contrairement aux approches de Monte-Carlo et aux méthodes variationnelles.
