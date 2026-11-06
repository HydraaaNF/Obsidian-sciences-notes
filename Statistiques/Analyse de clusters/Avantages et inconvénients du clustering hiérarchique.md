# Propriétés

Le [[Clustering hiérarchique|clustering hiérarchique]] présente les avantages et inconvénients suivants.

**Avantages**

- meilleur que le [[k-means]] pour les distances non métriques ;
- peut combiner des métriques et des critères d'équilibrage des clusters ;
- possibilité de définir a posteriori le [[Choix du nombre de clusters|nombre de clusters]] (mais pas si facile en pratique).

**Inconvénients**

- assez lent et coûteux en calcul ($O(N^3)$ ou $O(N^2 \log(N))$) ;
- les optima locaux peuvent ne pas être globalement bons :
  - on ne peut pas défaire ce qui a été fait précédemment ;
  - des méthodes de relocalisation sont nécessaires ;
- la coupe du dendrogramme n'est pas aussi facile qu'il n'y paraît.

# Remarque

Voir aussi les [[Avantages et inconvénients du k-means|avantages et inconvénients du k-means]].
