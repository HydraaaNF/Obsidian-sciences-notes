# Définition

Un [[Clustering|clustering]] peut viser différents objectifs, qui précisent la forme des clusters recherchée.

- **Clusters bien séparés** (well separated) : chaque point d'un cluster est plus proche de tout autre point de son cluster que de n'importe quel point extérieur au cluster.
- **Clusters centrés** (center) : chaque point d'un cluster est plus proche du centre de son cluster que du centre de tout autre cluster.
- **Clusters contigus** (contiguous) : chaque point d'un cluster est plus proche d'au moins un autre point de son cluster que de tout point d'un autre cluster.
- **Clusters fondés sur la densité** (density-based) : une région dense de points constitue un cluster ; cette région est séparée des autres clusters par des régions de faible densité.

# Interprétation

Ces objectifs sont illustrés par des schémas : trois groupes nettement éloignés les uns des autres (clusters bien séparés), des groupes centrés (clusters centrés), des points reliés de proche en proche (clusters contigus) et une région dense se détachant de régions peu denses (clusters fondés sur la densité).

# Remarque

L'objectif fondé sur la densité est celui que réalisent les méthodes du [[Clustering par densité]]. Voir aussi les [[Types de clustering]].
