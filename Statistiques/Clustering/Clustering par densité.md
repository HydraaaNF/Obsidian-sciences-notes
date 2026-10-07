# Définition

Le **clustering par densité** est une approche du [[Clustering|clustering]] qui suit les points connectés par densité (*density-connected points*) : elle procède par analyse de voisinage. Elle réalise les [[Objectifs d'un clustering|objectifs de clusters par densité]].

# Interprétation

Sur un nuage de points en deux dimensions, les clusters apparaissent comme des groupes de points de formes variées (bandes, croissants entrelacés, amas allongés) séparés par des zones où les points sont épars ; les points isolés restent hors des clusters.

# Propriétés

- Les clusters peuvent prendre une **forme arbitraire**.
- L'approche est **robuste au bruit**.
- Elle effectue **un seul passage sur les données**.

# Remarque

Les algorithmes typiques de cette famille sont [[DBSCAN]], OPTICS et DENCLUE ; [[DBSCAN]] s'appuie sur la classification des points en [[Points core, border et noise|points core, border et noise]].
