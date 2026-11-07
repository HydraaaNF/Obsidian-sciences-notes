#adm-9

# Définition

Le **p-hacking** consiste à collecter les données d'abord, puis à chercher le test qui dit ce qu'on veut : la procédure de test est choisie après avoir vu les données, en fonction du résultat qu'elle produit, au lieu d'être fixée avant.

# Exemple

On compare un algorithme `Our` à l'état de l'art `SOTA` sur cinq réglages, en mesurant les temps de calcul en secondes :

| Réglage | S1 | S2 | S3 | S4 | S5 |
| :--- | :---: | :---: | :---: | :---: | :---: |
| `Our` | 123 | 104 | 145 | 196 | 142 |
| `SOTA` | 152 | 120 | 164 | 195 | 134 |

La question posée est « `Our` est-il plus rapide que `SOTA` ? », au seuil $\alpha = 5\,\%$.

Les six premiers tests portent sur les mêmes données ; seul le test change, dans l'ordre où il vient à l'esprit. Les tests parcourus vont des [[Test de Wilcoxon de comparaison de deux échantillons indépendants|tests de rang pour échantillons indépendants]] aux [[Comparaison d'échantillons appariés|tests pour données appariées]].

| Test essayé | p-value | Verdict |
| :--- | :---: | :---: |
| Test des signes | 0,50 | non significatif |
| Test $U$ de Mann-Whitney | 0,35 | non significatif |
| Test $t$ de Welch (non apparié) | 0,30 | non significatif |
| Test de Wilcoxon des rangs signés | 0,16 | non significatif |
| Test $t$ apparié | 0,09 | non significatif |
| Test $t$ apparié sur $\log(\text{temps})$ | 0,085 | non significatif |
| Test $t$ apparié, réglages S4 et S5 retirés (points dits aberrants) | 0,016 | publier |
| Test « rejeter toujours $H_0$ » | aucune | publier |

# Remarque

Tant que les tests portent sur les cinq réglages, aucun n'est significatif au seuil de $5\,\%$ : les p-values décroissent de $0{,}50$ à $0{,}085$ sans jamais franchir $0{,}05$. Le tableau illustre donc, dans cette partie, la démarche inverse du p-hacking : aucun des six tests usuels, sur données intactes, n'a produit de rejet. Les deux seuls « succès » affichés ne relèvent pas du même procédé. Retirer les réglages S4 et S5 en les déclarant aberrants ne change pas le test appliqué : c'est la donnée qui est retaillée, et c'est là que la faute se commet. Le test « rejeter toujours $H_0$ » est bien un test, mais un test dégénéré de niveau $1$ : il rejette $H_0$ sans même consulter les données, si bien que son verdict ne prouve rien.

La règle est donc de choisir le test (et les données) **avant** de regarder les données, comme le fait la [[Méthodologie d'un test d'hypothèse|démarche correcte d'un test d'hypothèse]] : un test fixé à l'avance a un niveau connu, tandis qu'une batterie de tests essayés jusqu'au rejet n'a plus de niveau contrôlé. C'est précisément l'objet du [[Méta-test]] : le risque de rejeter $H_0$ à tort croît avec le nombre d'essais, et la [[Correction de Bonferroni]] en est le remède classique.
