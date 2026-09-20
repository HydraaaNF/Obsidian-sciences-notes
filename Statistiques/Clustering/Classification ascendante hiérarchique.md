# Définition
Méthode de [[Philosophies du clustering|clustering hiérarchique]] qui génère progressivement des clusters imbriqués en fusionnant ou en divisant les données. Peut être visualisée sous forme de **dendrogramme**.

# Algorithme ascendant (agglomératif)
```
initialiser N clusters singletons
nclusters ← N
tant que nclusters > 0 :
    fusionner les deux clusters les plus proches
    nclusters ← nclusters − 1
```

La distance entre deux clusters est donnée par un [[Critères de liaison (linkage)|critère de liaison]].

# Remarque : approche descendante
Il existe aussi une construction **descendante** (*divisive*) du dendrogramme, partant d'un unique cluster et le divisant récursivement — algorithme **DIANA** (*Divisive ANAlysis*).

# Avantages / Inconvénients
**Avantages** : plus performant que le [[k-means]] avec des distances non métriques, peut combiner métriques et critères d'équilibrage, permet de choisir *a posteriori* le nombre de clusters (bien que ce ne soit pas toujours simple en pratique)

**Inconvénients** : lent et coûteux ($O(N^3)$ ou $O(N^2 \log N)$), les optima locaux successifs ne garantissent pas un optimum global (impossible de revenir sur une fusion déjà faite, nécessite des méthodes de relocalisation), et couper le dendrogramme au bon endroit n'est pas aussi simple qu'il y paraît

# Application : segmentation temporelle
La classification ascendante hiérarchique s'applique aussi à la détection de segments temporels similaires, en s'appuyant sur une représentation des clusters par modèle (densités et mélanges gaussiens), la divergence de Kullback-Leibler ou le rapport de vraisemblance généralisé, et des approches de sélection de modèle (critère d'information bayésien) pour déterminer où couper le dendrogramme.
