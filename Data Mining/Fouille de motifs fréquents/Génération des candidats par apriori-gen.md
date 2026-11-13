#dmv-frequent_itemsets_mining

# Algorithme

`apriori-gen` engendre l'ensemble $C_k$ des candidats $k$-itemsets à partir de l'ensemble $F_{k-1}$ des $(k-1)$-itemsets [[Itemset fréquent|fréquents]]. Il procède en deux étapes : une jointure, qui forme les candidats, puis un élagage, qui en retire une partie.

Les items d'un [[Items, itemsets et base de transactions|itemset]] sont rangés dans un ordre fixe, ce qui donne un sens à ses premiers items. Le candidat $c$ recherché a pour taille $k$, tandis que $p$ et $q$ appartiennent tous deux à $F_{k-1}$ et ont donc pour taille $k-1$.

**Étape de jointure.** La jointure n'apparie que des itemsets qui coïncident sur leurs $k-2$ premiers items :

$$p.item_i = q.item_i,\ i \in \{1, \dots, k-2\}$$

et dont les derniers items sont distincts, celui de $p$ venant en premier :

$$p.item_{k-1} < q.item_{k-1}$$

Le candidat engendré réunit alors les $k-1$ items de $p$ et le dernier item de $q$ :

$$c = \{p.item_1, \dots, p.item_{k-1}, q.item_{k-1}\}$$

**Étape d'élagage.** Un candidat $c$ de $C_k$ est supprimé dès qu'il possède un $(k-1)$-sous-ensemble $s$ qui n'est pas fréquent :

$$\exists\, s \subset c,\ |s| = k-1,\ s \notin F_{k-1} \implies c \notin C_k$$

L'algorithme complet s'écrit :

```
apriori-gen(F_{k-1}) :
    // étape de jointure
    pour chaque paire (p, q) d'itemsets de F_{k-1} telle que
        p.item_i = q.item_i pour i allant de 1 à k-2
        et p.item_{k-1} plus petit que q.item_{k-1} :
        insérer dans C_k l'itemset
            {p.item_1, ..., p.item_{k-1}, q.item_{k-1}}

    // étape d'élagage
    pour chaque itemset c de C_k :
        pour chaque (k-1)-sous-ensemble s de c :
            si s n'est pas dans F_{k-1} :
                supprimer c de C_k

    retourner C_k
```

# Interprétation

La jointure ne construit que des candidats qui ont une chance d'être fréquents. Un $k$-itemset fréquent $F$ possède en effet deux $(k-1)$-sous-ensembles particuliers : celui obtenu en retirant son dernier item et celui obtenu en retirant son avant-dernier item. Ces deux sous-ensembles sont fréquents, partagent les $k-2$ premiers items de $F$ et ne diffèrent que par leur dernier item, placé dans le bon ordre : leur jointure redonne donc $F$. Aucun $k$-itemset fréquent n'échappe à la génération.

L'inégalité stricte entre les derniers items évite de plus d'engendrer deux fois le même candidat, puisque la paire $(q, p)$ est rejetée quand la paire $(p, q)$ est retenue.

L'élagage intervient ensuite, avant tout comptage : un candidat dont un seul $(k-1)$-sous-ensemble manque dans $F_{k-1}$ est écarté sans être confronté à la base. Le raisonnement ne peut pas rejeter un itemset fréquent, car un itemset fréquent a tous ses $(k-1)$-sous-ensembles dans $F_{k-1}$ ; il ne fait donc que retirer des candidats dont le support est nécessairement inférieur au seuil.

Les candidats survivants passent au comptage de leur support sur les transactions : voir [[Arbre de hachage et comptage du support]].

# Remarque

L'élagage repose entièrement sur la [[Propriété d'anti-monotonie du support|propriété d'anti-monotonie]] : un itemset dont un sous-ensemble n'est pas fréquent ne peut pas être fréquent lui-même, ce qui autorise à supprimer le candidat au lieu de le compter. C'est l'étape qui distingue cette génération d'une énumération aveugle des itemsets, et le coût de `apriori-gen` y est concentré : chaque candidat exige l'examen de ses $(k-1)$-sous-ensembles, au nombre de

$$\binom{k}{k-1} = k$$

pour un $k$-itemset, chacun demandant une recherche dans $F_{k-1}$ (voir [[Complexité de l'algorithme Apriori]]).

Le nombre de paires que la jointure peut examiner est au plus le nombre de paires d'itemsets de $F_{k-1}$ :

$$\binom{|F_{k-1}|}{2}$$

Cette borne est très grossière : seules les paires qui partagent leur préfixe de taille $k-2$ fusionnent réellement, et le seuil $minsup$ réduit fortement $|F_{k-1}|$ aux niveaux élevés.

`apriori-gen` est appelé à chaque niveau de l'itération qui construit les itemsets fréquents un niveau après l'autre : voir [[Algorithme Apriori]]. C'est ce parcours niveau par niveau qui rend l'élagage possible, puisqu'il suppose $F_{k-1}$ entièrement connu avant d'engendrer $C_k$.
