#adm-9

# Définition

Un test d'hypothèse se rattache à l'une des grandes familles suivantes, selon la comparaison qu'il met en œuvre :

- comparaison des données à une distribution théorique, c'est-à-dire un test d'ajustement : [[Test de comparaison d'une moyenne à une valeur donnée|comparaison d'une moyenne à une valeur donnée]], [[Test d'ajustement du chi-deux|test du chi-deux]], etc. ;
- comparaison de deux populations : [[Test du chi-deux d'indépendance|test du chi-deux]], [[Comparaison d'échantillons appariés|test t apparié]], [[Test de Wilcoxon de comparaison de deux échantillons indépendants|tests de rangs]], etc. ;
- [[Test du rapport de vraisemblance|tests du rapport de vraisemblance]].

# Interprétation

Les familles décrivent la forme de la question posée, pas l'outil employé : une même loi de statistique peut servir dans plusieurs d'entre elles. Le test du chi-deux apparaît ainsi à la fois comme test d'ajustement, où une distribution observée est confrontée à une distribution théorique, et comme test de comparaison de deux populations, où deux échantillons sont confrontés l'un à l'autre.

Le test d'ajustement part d'une seule série d'observations et d'une référence théorique, tandis que la comparaison de deux populations met en regard deux séries d'observations.

# Exemple

Comparaison de deux populations : deux classifieurs, C4.5 et C4.5+m, évalués par leur exactitude sur quatorze jeux de données.

| Jeu de données | C4.5 | C4.5+m | Différence | Rang |
| :--- | :---: | :---: | :---: | :---: |
| adult (sample) | $0{,}763$ | $0{,}768$ | $+0{,}005$ | $3{,}5$ |
| breast cancer | $0{,}599$ | $0{,}591$ | $-0{,}008$ | $7$ |
| breast cancer wisconsin | $0{,}954$ | $0{,}971$ | $+0{,}017$ | $9$ |
| cmc | $0{,}628$ | $0{,}661$ | $+0{,}033$ | $12$ |
| ionosphere | $0{,}882$ | $0{,}888$ | $+0{,}006$ | $5$ |
| iris | $0{,}936$ | $0{,}931$ | $-0{,}005$ | $3{,}5$ |
| liver disorders | $0{,}661$ | $0{,}668$ | $+0{,}007$ | $6$ |
| lung cancer | $0{,}583$ | $0{,}583$ | $0{,}000$ | $1{,}5$ |
| lymphography | $0{,}775$ | $0{,}838$ | $+0{,}063$ | $14$ |
| mushroom | $1{,}000$ | $1{,}000$ | $0{,}000$ | $1{,}5$ |
| primary tumor | $0{,}940$ | $0{,}962$ | $+0{,}022$ | $11$ |
| rheum | $0{,}619$ | $0{,}666$ | $+0{,}047$ | $13$ |
| voting | $0{,}972$ | $0{,}981$ | $+0{,}009$ | $8$ |
| wine | $0{,}957$ | $0{,}978$ | $+0{,}021$ | $10$ |

La différence vaut l'exactitude de C4.5+m moins celle de C4.5 : une différence positive signale un avantage du second classifieur, une différence négative un avantage du premier.

# Remarque

Le rang classe les jeux de données par la valeur absolue de la différence, et non par son signe. Les ex æquo partagent le rang moyen : les deux différences nulles reçoivent le rang $1{,}5$, et les deux différences de valeur absolue $0{,}005$, de signes opposés, le rang $3{,}5$.
