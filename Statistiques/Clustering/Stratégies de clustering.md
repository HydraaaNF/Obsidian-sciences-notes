# Définition

Les algorithmes de [[Clustering|clustering]] se répartissent en deux grandes familles de méthodes.

**Stratégie hiérarchique**, le [[Clustering hiérarchique|clustering hiérarchique]] regroupe ou divise progressivement les points :

- **Agglomérative** (bottom-up) : chaque point est initialement un cluster ; on combine répétitivement les deux clusters « les plus proches » en un seul.
- **Divisive** (top-down) : on part d'un seul cluster et on le scinde récursivement.

Ces deux variantes constituent le [[Clustering agglomératif et divisif|clustering agglomératif et divisif]].

**Stratégie d'affectation de points**, un ensemble de clusters est maintenu, et chaque point appartient au cluster « le plus proche ». C'est la stratégie mise en œuvre par le [[k-means]].

# Interprétation

L'approche hiérarchique se visualise par un arbre de regroupements : en partant des points individuels, chaque fusion réunit deux clusters en un cluster unique. L'affectation de points se visualise dans le nuage des données : chaque point y est rattaché au cluster le plus proche, ce qui délimite des groupes de points.
