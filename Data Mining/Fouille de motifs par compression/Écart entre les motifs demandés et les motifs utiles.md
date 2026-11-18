#dmv-pattern_mining_with_information_theory

# Interprétation

Le besoin exprimé par la question « comment trouver des motifs utiles ? » ne se confond pas avec la demande habituelle de la fouille de motifs :

- ce qui est demandé : tous les motifs qui satisfont un ensemble de contraintes (voir [[Énoncé standard de la fouille de motifs]]) ;
- ce qui est voulu : un petit ensemble de motifs qui montre la structure des données.

La demande produit un résultat bien plus volumineux que le besoin : l'abaissement des seuils multiplie le nombre de motifs sans gagner en information, et beaucoup d'entre eux sont redondants (voir [[Explosion du nombre de motifs]]).

# Modèle

Le besoin se reformule ainsi : demander un ensemble de motifs $P \subseteq L$ tel que

- chaque membre de l'ensemble satisfasse les contraintes ;
- l'ensemble soit optimal au regard d'un critère.

L'objet demandé n'est plus le motif isolé mais une collection dont la qualité se juge globalement : c'est la notion d'[[Ensemble de motifs]].

# Remarque

Le déplacement du problème est net : la difficulté quitte le comptage exhaustif des motifs pour se loger dans le critère qui décide de l'optimalité. Trouver un petit ensemble qui montre la structure des données revient à [[Factorisation des données en modèle et en données couvertes|factoriser les données]] en un modèle et en ce que le modèle ne capte pas ; le [[Principe de la longueur minimale de description]] fournit le critère correspondant.
