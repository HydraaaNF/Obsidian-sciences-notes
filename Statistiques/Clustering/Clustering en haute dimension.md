# Définition
De nombreuses applications nécessitent des espaces de grande dimension (documents textuels, images, données ADN...), ce qui pose des défis spécifiques :

- des dimensions non pertinentes peuvent masquer les clusters
- les mesures de distance perdent leur sens (**fléau de la dimension**)
- des clusters peuvent n'exister que dans certains sous-espaces

# Interprétation
Trois familles de solutions :
- **transformation de variables** : [[Analyse en composantes principales|ACP]] / SVD si les variables sont corrélées/redondantes
- **sélection de variables** : ne garder que les variables où des clusters apparaissent nettement
- **clustering en sous-espaces** : chercher des clusters dans tous les sous-espaces possibles (algorithmes CLIQUE, Proclus)

# Remarque
Pour de très grands jeux de données, même un coût en $O(n)$ peut dépasser la mémoire disponible ; de nombreux algorithmes de clustering sont en $O(n^2)$ ou $O(n^3)$ (temps et/ou mémoire), ce qui devient vite prohibitif.
