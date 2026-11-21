#dmv-pattern_mining_with_information_theory

# Interprétation

Deux exigences gouvernent la fouille de motifs :
- l'**efficacité** : extraire les motifs avec des algorithmes, des stratégies d'exploration et des structures de données qui passent à l'échelle ;
- l'**utilisabilité** : rendre les motifs extraits exploitables par celui qui les demande.

Les gains d'efficacité se lisent comme une suite de paliers, chacun élargissant la classe des bases traitées :
- extraire des motifs de jeux de données ;
- extraire des millions de motifs de grands jeux de données ;
- extraire des millions de motifs en quelques secondes de grands jeux de données ;
- extraire des millions de motifs en quelques secondes de jeux de données complexes et grands.

Chaque palier est franchi par un progrès portant sur les algorithmes, leurs stratégies et leurs structures de données, non par un changement de la question posée : la fouille reste la recherche de tous les motifs qui satisfont les contraintes, telle que l'[[Énoncé standard de la fouille de motifs|énoncé standard]] la définit.

# Remarque

L'efficacité ne suffit pas. Une extraction terminée en quelques secondes livre encore des motifs trop nombreux, redondants et sans pertinence pour la question posée, et l'utilisateur placé devant cette masse de motifs n'a pas de réponse directe : c'est l'[[Explosion du nombre de motifs|explosion du nombre de motifs]].
