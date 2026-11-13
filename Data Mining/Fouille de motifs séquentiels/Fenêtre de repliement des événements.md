#dmv-sequence_mining

# Définition

La fenêtre de repliement des événements (event folding window) est un prétraitement qui rend atomiques les transactions survenant dans un intervalle de temps donné : toutes les transactions d'un même intervalle forment un seul itemset.

# Interprétation

Le choix de l'unité de temps est une décision importante, qui dépend du domaine :

- épicerie : les ventes d'une semaine ;
- agence de voyage : les voyages achetés durant une année.

Comme la [[Durée des séquences]], la fenêtre de repliement règle la granularité temporelle des données avant la fouille ; elle borne aussi ce qui compte comme simultané, tandis que la [[Contrainte d'écart temporel]] borne l'écart entre itemsets successifs d'une occurrence.

Une [[Lecture informelle d'un motif séquentiel|lecture informelle]] du motif, du type « en un mois », se rattache en revanche à la [[Contrainte d'écart temporel]] : la fenêtre de repliement fixe la granularité, pas la portée temporelle des motifs.

# Exemple

Un intervalle trop court multiplie les itemsets et ne laisse subsister que des séquences de trop faible [[Support d'un motif séquentiel|support]] : on obtient

$$\langle A,B,C\rangle$$

ou

$$\langle B,A,C\rangle$$

au lieu de

$$\langle AB,C\rangle$$

Un intervalle trop long fait disparaître la séquentialité : on obtient

$$\langle AB\rangle$$

au lieu de

$$\langle A,B\rangle$$

l'ordre entre A et B n'étant plus distingué.
