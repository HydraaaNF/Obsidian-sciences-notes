#dmv-frequent_itemsets_mining

# Algorithme

LCM (Linear time Closed itemset Miner) énumère les [[Itemsets fréquents fermés|itemsets fermés fréquents]] d'une base de transactions par [[Recherche inverse des itemsets fermés|recherche inverse]] : un parcours en profondeur de l'arbre couvrant des fermés, où la fonction de transition d'un nœud recalcule ses fils par ajout d'un item puis [[Fermeture d'un itemset et extension par fermeture|fermeture]].

Les objets du parcours :

- $D$ : la base de transactions, chaque transaction $T \in D$ étant un ensemble d'items ;
- $\varepsilon$ : le seuil de [[Support d'un itemset|support]] minimum ;
- $\bot_{\mathrm{closed}}$ : le plus petit itemset fermé de $D$, intersection de toutes ses transactions ;
- $I$ : l'itemset fermé courant, c'est-à-dire le nœud visité ;
- $i$ : l'item d'extension, celui dont l'ajout à $I$ définit le fils à engendrer ;
- $D_I$ : la base conditionnelle du nœud, restriction de $D$ aux transactions qui contiennent $I$ ;
- $D_I[\{i\}]$ : les transactions de $D_I$ qui contiennent $i$, dont le cardinal est le support de $i$ dans cette base ;
- $J$ : l'itemset fermé fils engendré par le nœud courant.

```
begin
    ⊥closed ← ∩_{T ∈ D} T
    output ⊥closed
    foreach i ∈ I | i ∉ ⊥closed do
        expand(⊥closed, i, D, ε)

Function expand(I, i, D_I, ε)
begin
    if support_{D_I}({i}) ≥ ε then
        I_ext ← ∩_{T ∈ D_I[{i}]} T
        if maxItem(I_ext) = i then
            J ← I ∪ I_ext
            output (J, support_{D_I}({i}))
            D_J = {T \ J | T ∈ D_I[{i}]}
            foreach j ∈ I \ J | j < i do
                expand(J, j, D_J, ε)
```

Lecture des instructions :

- L'intersection de toutes les transactions ne retient que les items présents partout : c'est la fermeture de l'ensemble vide, point de départ du parcours.
- La boucle initiale prend chaque item absent de ce fermé comme item d'extension et lance une expansion depuis la racine.
- Le test `support_{D_I}({i}) ≥ ε` vérifie la fréquence de l'item d'extension dans la base conditionnelle : un item trop rare ne peut appartenir à aucun fermé fréquent, par [[Propriété d'anti-monotonie du support|anti-monotonie du support]].
- $I_{\mathrm{ext}}$ est la fermeture de $I \cup \{i\}$, obtenue en intersectant les transactions de $D_I$ qui contiennent $i$ ; elle contient $i$ et tous les items qui accompagnent $i$ dans chacune de ces transactions.
- Le test du premier parent exige que l'item d'extension soit le plus grand item de cette fermeture.
- $J$ réunit l'itemset courant et sa fermeture : c'est le fils engendré, dont le support est celui de $i$ dans $D_I$.
- $D_J$ restreint la base conditionnelle du fils aux transactions contenant $i$, chacune privée des items de $J$.
- La boucle d'augmentation relance l'expansion depuis le fils pour les items encore candidats.

# Interprétation

Le parcours descend d'un fermé à un de ses fils tant qu'une expansion est possible, puis remonte et essaie l'item d'extension suivant : la liste des itemsets fermés déjà énumérés n'est jamais tenue à jour. Seul le chemin courant est conservé, chaque nœud recalculant ses fils à partir de sa base conditionnelle. C'est le propre de la recherche inverse, qui remplace la mémoire globale des méthodes à candidats par ce recalcul local, comme exposé dans [[Calcul efficace des itemsets fermés]].

La base conditionnelle est réduite à chaque niveau :

$$D_J = \{T \setminus J \mid T \in D_I[\{i\}]\}$$

- Les transactions sont restreintes à celles qui contiennent l'item d'extension, ce qui élimine les branches sans rapport avec le nœud courant.
- Les items de $J$ sont retirés des transactions, donc les items déjà absorbés dans le fermé courant disparaissent de la base des niveaux suivants.
- Les items universellement présents dans la base conditionnelle sont absorbés dans $I_{\mathrm{ext}}$, donc dans $J$, et quittent eux aussi la base.
- Les items dont le support passe sous le seuil sont écartés par le test de fréquence.

La base rétrécit ainsi de niveau en niveau, ce qui rend le traitement des niveaux profonds possible : les fermés y sont pourtant les plus longs et les plus coûteux à tester sur la base complète. Le détail des filtres appliqués est traité dans [[Réductions de la base de transactions]].

# Remarque

Le test du premier parent garantit l'unicité de l'engendrement. Un même fermé peut être atteint depuis plusieurs parents par ajout d'items différents, mais la condition $\mathrm{maxItem}(I_{\mathrm{ext}}) = i$ impose que l'item d'extension soit le plus grand item du fermé obtenu : un fermé n'est donc engendré que pour un seul item d'extension, et le parcours ne produit aucun doublon sans avoir à mémoriser les itemsets déjà sortis. Ce test applique l'ordre d'exploration qui transforme le treillis des fermés en arbre couvrant, décrit dans [[Arbre des itemsets fermés et ordre d'exploration]].

La boucle d'augmentation est écrite sur $I \setminus J$ avec la condition $j < i$. Comme $J = I \cup I_{\mathrm{ext}}$ contient $I$, la différence $I \setminus J$ est vide et aucune récursion ne serait lancée. Les items candidats à l'augmentation sont ceux qui subsistent dans la base conditionnelle $D_J$ : c'est sur les items non encore ajoutés au fermé courant, et non sur une différence d'ensembles dont $J$ est un sur-ensemble, que portent les implémentations. La condition de support exacte à appliquer à ces items n'est pas donnée par l'algorithme tel qu'il est écrit.
