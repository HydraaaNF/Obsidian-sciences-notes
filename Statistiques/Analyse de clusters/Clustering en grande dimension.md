# Interprétation

De nombreuses applications nécessitent des espaces de grande dimension : documents textuels, images, données d'ADN, etc. La grande dimension soulève de nouvelles difficultés pour le [[Clustering|clustering]] :

- de nombreuses dimensions non pertinentes peuvent masquer les clusters ;
- la [[Mesures de similarité et de distance|mesure de distance]] devient sans signification (malédiction de la dimensionnalité) ;
- un cluster peut n'exister que dans certains sous-espaces.

Plusieurs contournements permettent de traiter ces difficultés :

- **transformation de variables** : [[Analyse en composantes principales|analyse en composantes principales]] (ACP) ou décomposition en valeurs singulières (SVD), lorsque les variables sont corrélées ou redondantes ;
- **sélection de variables** : ne retenir que les variables où de beaux clusters apparaissent ;
- **clustering par sous-espaces** (*subspace clustering*) : chercher des clusters dans tous les sous-espaces possibles (CLIQUE, Proclus).

# Remarque

La dimensionnalité des données est l'un des éléments à examiner pour le [[Choix d'une méthode de clustering|choix d'une méthode de clustering]].
