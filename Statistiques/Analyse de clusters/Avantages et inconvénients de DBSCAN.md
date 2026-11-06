# Propriétés

Le [[DBSCAN]] présente les avantages et inconvénients suivants.

**Avantages**

- pas d'hypothèse de convexité : DBSCAN est capable de découvrir des clusters de formes et de tailles variées ;
- gestion du bruit : il identifie les points aberrants comme des [[Points core, border et noise|points de bruit]], ce qui le rend robuste au bruit dans les données ;
- aucun besoin de spécifier le [[Choix du nombre de clusters|nombre de clusters]] : DBSCAN le détermine automatiquement à partir des données.

**Inconvénients**

- sensibilité au choix des paramètres : les performances de DBSCAN dépendent de paramètres comme $\varepsilon$ et le nombre minimum de points ;
  - le choix de paramètres appropriés devient délicat lorsque les clusters ont des densités significativement différentes ;
- nécessité d'une [[Mesures de similarité et de distance|fonction de distance]] pertinente.

# Remarque

Voir aussi les avantages et inconvénients du [[Avantages et inconvénients du k-means|k-means]] et ceux du [[Avantages et inconvénients du clustering spectral|clustering spectral]].
