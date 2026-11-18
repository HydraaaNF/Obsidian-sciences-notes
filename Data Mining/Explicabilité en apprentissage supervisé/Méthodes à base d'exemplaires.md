#dmv-xai

# Définition

Les méthodes à base d'exemplaires forment une famille de modèles interprétables dont la prédiction se lit sur des exemples : les k plus proches voisins et les prototypes de classe.

Un prototype de classe est un exemple associé à une classe ; la classe rapportée pour une nouvelle observation est celle du prototype le plus proche.

# Modèle

Les k plus proches voisins conservent l'ensemble des exemples étiquetés. Pour classer une nouvelle observation, on considère les $k$ exemples les plus proches d'elle, et la réponse est portée par leur classe.

Les prototypes de classe remplacent cette collection par un jeu réduit d'exemples représentatifs, un ou plusieurs par classe. La règle de prédiction reste la même : elle rapporte la classe du prototype le plus proche.

# Interprétation

La prédiction s'explique par les exemples qui l'ont produite : la réponse est la classe d'exemples que l'on peut montrer, et non le résultat d'un calcul opaque. C'est à ce titre que la famille figure parmi les modèles dont l'[[Interprétabilité]] est directe. Le modèle est lui-même constitué d'exemples : la règle de décision est une représentation directement lisible, faite des exemples retenus, au même titre que le [[Modèle linéaire]] et l'[[Arbre de décision]] le sont par leurs coefficients et par leurs chemins.

# Remarque

La sélection des prototypes est le point délicat de la méthode. Elle se définit comme un compromis entre trois quantités : la couverture, la minimalité et la dissimilarité des prototypes.

- la couverture : les prototypes doivent représenter les exemples de leur classe ;
- la minimalité : ils doivent rester peu nombreux ;
- la dissimilarité : deux prototypes ne doivent pas se ressembler.

Ces trois exigences se contredisent : un jeu réduit couvre mal les classes, tandis qu'un jeu qui les couvre bien demande davantage de prototypes et laisse apparaître des prototypes proches les uns des autres.

Un prototype de classe joue pour sa classe le rôle qu'un centre joue pour un cluster dans le [[k-means]] : c'est un point de référence dont la proximité décide de l'affectation. La même idée d'explication par des exemples représentatifs est exploitée par les [[Explications par concepts et prototypes]].

Le choix du nombre de prototypes et la comparaison de deux jeux de prototypes relèvent d'un protocole commun à toutes les méthodes d'explication, voir le [[Protocole de comparaison d'explications]].

# Exemple

Sur un nuage de points à deux classes, des carrés bleus et des triangles rouges, l'observation à classer est marquée d'un point vert accompagné d'un point d'interrogation. Deux voisinages sont tracés autour d'elle : un cercle plein serré, qui ne contient qu'un carré bleu et deux triangles rouges, et un cercle en pointillés plus large, qui n'ajoute que deux carrés bleus et aucun triangle rouge. Le voisinage serré compte donc un carré bleu contre deux triangles rouges, le voisinage large trois carrés bleus contre deux triangles rouges : la classe majoritaire change avec l'étendue du voisinage retenue.

Sur un mélange de gaussiennes à trois classes, quatre frontières de décision sont comparées : la frontière de Bayes, prise comme référence, puis celles obtenues par sélection de prototypes (PS), par K-medoids et par LVQ. Les prototypes retenus apparaissent comme des points pleins colorés, et la frontière de Bayes est rappelée en gris dans les trois autres panneaux.

| Panneau | Prototypes et frontière |
|---|---|
| Bayes Boundary | frontière de référence, sans prototype |
| PS | peu de prototypes par classe, frontière proche de celle de Bayes |
| K-medoids | davantage de prototypes, frontière découpée en segments dans la zone où les classes se mêlent |
| LVQ | des prototypes répartis dans les zones denses des trois classes |

Aucune des trois frontières ne coïncide exactement avec la frontière de Bayes : le choix de la méthode de sélection des prototypes déplace la frontière.
