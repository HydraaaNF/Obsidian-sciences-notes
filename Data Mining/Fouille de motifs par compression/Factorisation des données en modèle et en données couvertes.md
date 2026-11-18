#dmv-pattern_mining_with_information_theory

# Modèle

La base est décomposée en deux facteurs, un modèle et les données conditionnées à ce modèle :

$$D \longmapsto (M,\; D \mid M)$$

- $D$ : les données observées, un jeu de données binaire jouet ;
- $M$ : la partie modèle, la structure latente, représentée par une pile de bandes colorées ;
- $D \mid M$ : la partie résiduelle conditionnelle, la même matrice où les rectangles du motif se superposent.

| Composante | Représentation | Rôle |
|---|---|---|
| $D$ | croix noire sur fond blanc | données observées |
| $M$ | pile de bandes colorées | structure latente |
| $D \mid M$ | carré et rectangles colorés superposés | données conditionnées au modèle |

# Interprétation

Au lieu de traiter $D$ comme un tout opaque, la factorisation isole ce que le modèle explique de ce qui reste à décrire : $M$ porte la structure, et $D \mid M$ capture ce que le motif ne recouvre pas. Elle repose sur la lecture locale du motif, qui recouvre un sous-ensemble de lignes et de colonnes de la matrice (voir [[Motif comme propriété locale des données]]).

# Remarque

La question pratique devient : comment trouver un sous-ensemble de motifs qui décrive les données de façon concise ? Le modèle obtenu est un [[Ensemble de motifs]] et non une énumération de motifs isolés ; sa forme opérationnelle est une [[Table de codes]], et le choix entre plusieurs factorisations possibles est tranché par le [[Principe de la longueur minimale de description]].
