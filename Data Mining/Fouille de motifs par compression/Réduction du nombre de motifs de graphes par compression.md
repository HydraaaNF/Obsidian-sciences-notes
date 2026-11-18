#dmv-pattern_mining_with_information_theory
# Interprétation

La [[Compression d'un graphe par un ensemble de motifs]] ne conserve qu'une petite partie des motifs candidats qui lui sont soumis. Les candidats sont d'abord extraits par un algorithme de croissance de motifs de graphes, ici [[Panorama des algorithmes de croissance de motifs de graphes|gSpan]], à un seuil de support minimal donné ; la sélection par compression en retient ensuite quelques dizaines à quelques centaines.

Deux régularités se dégagent des mesures :

- la réduction est drastique : des milliers ou des centaines de milliers de candidats se réduisent à un modèle de quelques centaines de motifs au plus ;
- le nombre de motifs retenus reste relativement stable quand le seuil de support minimal baisse, alors même que le nombre de candidats augmente d'un ordre de grandeur ou plus.

Autrement dit, le modèle ne grossit pas au rythme des candidats : l'essentiel de la masse des motifs extraits est écarté comme redondant ou inutile à la description.

# Exemple

Trois jeux de données sont utilisés :

- AIDS-CA et AIDS-CM : des molécules, avec peu d'étiquettes de sommets et de nombreux cycles ;
- UD-PUD-En : des arbres de dépendances de phrases anglaises du projet Universal Dependencies, avec de nombreuses étiquettes et sans cycle.

| Jeu de données | Seuil de support minimal | Motifs candidats | Motifs retenus |
|---|---|---|---|
| AIDS-CA | 20 % | 2194 | 115 |
| AIDS-CA | 15 % | 7867 | 123 |
| AIDS-CA | 10 % | 20596 | 148 |
| AIDS-CM | 20 % | 433 | 111 |
| AIDS-CM | 15 % | 779 | 131 |
| AIDS-CM | 10 % | 2054 | 163 |
| AIDS-CM | 5 % | 9943 | 225 |
| UD-PUD-En | 10 % | 164 | 162 |
| UD-PUD-En | 5 % | 458 | 249 |
| UD-PUD-En | 1 % | 6021 | 523 |
| UD-PUD-En | 0 % | 233434 | 773 |

L'évolution du nombre de motifs retenus, pour ces mêmes réglages de seuil :

```chart
type: bar
labels: ["AIDS-CA 20 %", "AIDS-CA 15 %", "AIDS-CA 10 %", "AIDS-CM 20 %", "AIDS-CM 15 %", "AIDS-CM 10 %", "AIDS-CM 5 %", "UD-PUD-En 10 %", "UD-PUD-En 5 %", "UD-PUD-En 1 %", "UD-PUD-En 0 %"]
series:
  - title: Motifs retenus
    data: [115, 123, 148, 111, 131, 163, 225, 162, 249, 523, 773]
```

Sur AIDS-CA, le nombre de candidats passe de 2194 à 20596 quand le seuil tombe de 20 % à 10 %, tandis que le modèle passe seulement de 115 à 148 motifs. Le même écart se lit sur UD-PUD-En au seuil 0 % : 233434 candidats pour 773 motifs retenus.

# Remarque

La réduction n'est spectaculaire que si les candidats sont nombreux. Sur UD-PUD-En au seuil 10 %, 164 candidats donnent 162 motifs retenus : presque tout est conservé, car peu de motifs sont redondants à ce niveau de support. La compression ne supprime donc pas des motifs par principe, elle ne garde que ce qui paie en longueur de description, au sens de la [[Taille totale d'un modèle et des données encodées]].

Le nombre de motifs retenus croît néanmoins avec le nombre de candidats, mais beaucoup plus lentement : c'est le comportement attendu d'une sélection guidée par le gain de compression, analogue à celui observé sur les itemsets avec les [[Propriétés des tables de codes de KRIMP|tables de codes de KRIMP]], qui restent petites elles aussi.
