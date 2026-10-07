# Définition

Dans un [[Clustering hiérarchique|clustering hiérarchique]], le **type de liaison** (linkage) définit la façon de mesurer la distance entre deux clusters. C'est cette distance qui décide de la fusion des clusters et qui est reportée dans la [[Matrice de proximité et clustering ascendant|matrice de proximité]].

- **liaison simple** (single linkage) : $D(A, B) = \min(d(x, y) \ \forall(x, y) \in A \times B)$, à réserver aux classes bien séparées ;
- **liaison complète** (complete linkage ou total linkage) : $D(A, B) = \max(d(x, y) \ \forall(x, y) \in A \times B)$, favorise les grands clusters ;
- **liaison moyenne** (average linkage) : $D(A, B) = \frac{1}{|A|\,|B|} \sum_{x \in A} \sum_{y \in B} d(x, y)$, la distance moyenne entre les éléments de $A$ et de $B$, robuste au bruit et aux outliers, mais biaisée vers les clusters globulaires ;
- **liaison de Ward** (Ward's linkage) : l'augmentation de la variance du cluster fusionné ;
- **et beaucoup d'autres** : distance entre moyennes ou médianes, distance entre modèles (statistiques) des données, etc.

# Interprétation

La liaison ne mesure pas une proximité entre points isolés, mais une proximité entre groupes : c'est elle qui fixe quels clusters fusionnent à chaque étape d'un [[Clustering agglomératif et divisif|clustering agglomératif]]. Un même jeu de données regroupé avec des liaisons différentes ne donne donc pas la même hiérarchie.

# Exemple

Sur un même exemple de six points, trois liaisons sont illustrées avec les fusions successives numérotées : liaison simple (MIN), liaison complète (MAX) et moyenne de groupe (Group Average). Les dendrogrammes associés montrent que l'ordre des fusions et la hauteur à laquelle elles se produisent diffèrent d'une liaison à l'autre : la hiérarchie obtenue dépend du type de liaison retenu.
