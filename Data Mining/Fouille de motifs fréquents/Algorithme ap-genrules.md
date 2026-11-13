#dmv-frequent_itemsets_mining

# Algorithme

`ap-genrules` engendre les [[Règle d'association et confiance|règles d'association]] issues d'un même [[Itemset fréquent|itemset fréquent]] $f_k$, en faisant croître la taille du conséquent. Il reçoit $f_k$ et un ensemble $H_m$ de conséquents de taille $m$ déjà retenus, produit les conséquents de taille $m+1$ par [[Génération des candidats par apriori-gen|apriori-gen]], teste leur [[Règle d'association et confiance|confiance]] et s'appelle lui-même sur les seuls conséquents conservés.

```text
Input: f_k, H_m   // H_m : ensemble des conséquents de taille m

if (k > m+1) then begin
    H_{m+1} = apriori-gen(H_m) ;   // engendre tous les itemsets possibles de taille m+1
    foreach h_{m+1} ∈ H_{m+1} do begin
        conf = support(f_k) / support(f_k - h_{m+1}) ;
        if conf ≥ minconf then
            output rule f_k - h_{m+1} → h_{m+1} ;
        else
            delete h_{m+1} from H_{m+1} ;   // élagage par anti-monotonie
    end
    ap-genrules(f_k, H_{m+1}) ;
end
```

# Interprétation

Le test d'arrêt $k > m+1$ compare la taille $k$ de l'itemset source et la taille $m$ du conséquent. Il faut $m+1 < k$ pour que le conséquent puisse grandir d'un item en laissant l'antécédent non vide : lorsque $m+1 = k$, le conséquent couvrirait tout $f_k$ et il ne resterait plus rien à mettre à gauche de la flèche. La récursion s'arrête donc d'elle-même à la dernière taille utile, sans instruction de retour explicite.

La génération des conséquents ne s'invente pas de novo : elle réutilise la procédure qui engendre les candidats de l'[[Algorithme Apriori|algorithme Apriori]], appliquée ici à l'ensemble $H_m$ des conséquents de taille $m$. Les conséquents de taille $m+1$ en sortent munis de la même garantie, à savoir que tous leurs $m$-sous-ensembles appartiennent à $H_m$ et ont donc déjà passé le test de confiance.

Chaque conséquent candidat $h_{m+1}$ définit une règle dont l'antécédent est l'itemset source privé de $h_{m+1}$. Sa confiance vaut

$$c\big(f_k - h_{m+1} \to h_{m+1}\big) = \frac{\mathrm{support}(f_k)}{\mathrm{support}(f_k - h_{m+1})}$$

Le numérateur est le [[Support d'un itemset|support]] de $f_k$, identique pour toutes les règles tirées de cet itemset et déjà connu puisque $f_k$ est fréquent. Seul le dénominateur varie avec le conséquent choisi, et un conséquent plus gros laisse un antécédent plus petit, donc un support d'antécédent plus grand, donc une confiance plus faible.

Le conséquent qui n'atteint pas $minconf$ est supprimé de $H_{m+1}$ à l'instant même où sa règle est rejetée. Comme $H_{m+1}$ sert d'entrée à l'appel récursif, la suppression coupe la branche entière : aucun sur-ensemble de ce conséquent ne sera examiné au tour suivant, alors qu'il aurait fallu tester chacune des règles correspondantes. C'est le seul élagage de la procédure.

# Remarque

L'élagage est fondé sur l'[[Anti-monotonie de la confiance selon la taille du conséquent|anti-monotonie de la confiance selon la taille du conséquent]] : à itemset source fixé, la confiance décroît quand le conséquent grandit. Un conséquent $h$ écarté pour insuffisance de confiance a pour tout sur-ensemble $h' \supset h$ un antécédent plus petit, donc un support d'antécédent plus grand et une confiance plus faible encore :

$$h' \supset h \implies c\big(f_k - h' \to h'\big) \le c\big(f_k - h \to h\big) < minconf$$

Aucune règle bâtie sur $h'$ ne peut donc atteindre le seuil, ce qui justifie de supprimer $h$ une fois pour toutes au lieu de le conserver pour les tours suivants.

Cette propriété ne doit rien au [[Propriété d'anti-monotonie du support|support]], dont l'anti-monotonie porte sur l'inclusion des itemsets et non sur la confiance : la [[Monotonie de la confiance|confiance n'est ni monotone ni anti-monotone]] en général, et l'ordre ne subsiste qu'à itemset source fixé, quand la taille du conséquent varie. C'est pourquoi `ap-genrules` traite les itemsets fréquents un par un, sans jamais comparer les règles issues d'itemsets différents.

La procédure constitue la seconde étape du [[Calcul des règles d'association en deux étapes|calcul des règles d'association en deux étapes]] : la [[Génération des règles d'association|génération des règles d'association]] énumère les $(k-1)$-sous-ensembles de chaque $f_k$, forme $H_1$ avec ceux qui passent le seuil, puis délègue à `ap-genrules` l'extension de ces conséquents. Le point de départ est donc $H_1$, et le premier appel ne génère que des conséquents de taille 2.
