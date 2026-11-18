#dmv-pattern_mining_with_information_theory
# Propriétés

Les tables de codes produites par l'[[Algorithme KRIMP]] présentent trois propriétés, qui vont dans le sens attendu d'un modèle au sens du [[Principe de la longueur minimale de description]] :

- **elles sont caractéristiques** : elles compressent bien les données, ce qui est exactement le critère de sélection de la théorie de l'information ;
- **elles sont petites** : elles se composent de peu de motifs, l'algorithme ayant écarté tout candidat dont l'ajout n'améliorait pas la description ;
- **elles sont spécifiques** : elles contiennent des itemsets relativement longs, et non une collection de petits motifs génériques.

Les deux dernières propriétés se renforcent l'une l'autre. Une table petite et spécifique contient peu d'entrées, mais chacune d'elles décrit une combinaison précise d'items : le modèle est à la fois concis et informatif, au lieu de lister un grand nombre de régularités faibles.

# Remarque

La compression est une garantie de fidélité, pas une garantie d'utilité. Une table de codes peut décrire les données avec une description courte tout en reposant sur des régularités qui n'apprennent rien sur le phénomène étudié, par exemple des combinaisons propres au hasard d'échantillonnage. C'est la question laissée ouverte après ces trois propriétés : ces motifs sont-ils utiles ?

La réponse ne peut venir de la seule longueur de description : elle demande de confronter les tables à des tâches concrètes. C'est l'objet des [[Applications des tables de codes]] et, en particulier, de la [[Classification par compression avec des tables de codes]].

La propriété de spécificité explique aussi pourquoi l'[[Élagage après acceptation d'une table de codes]] est nécessaire : en accumulant des itemsets longs, l'algorithme rend inutiles certaines entrées plus courtes devenues redondantes, qu'un simple parcours par ajouts ne retire pas.
