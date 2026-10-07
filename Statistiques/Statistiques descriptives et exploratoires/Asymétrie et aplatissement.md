# Définition

La [[Moyenne, médiane et mode|moyenne]] ne suffit pas à décrire une variable : il faut aussi en résumer la dispersion et la forme. La forme d'ensemble est décrite par deux moments centrés normalisés :

- la **skewness** (coefficient d'asymétrie) : $\gamma_1 = \mu_3/\sigma^3$ ;
- le **kurtosis** (coefficient d'aplatissement) : $\gamma_2 = \mu_4/\sigma^4$,

où $\mu_3 = \mathbb{E}\left[(X - \mathbb{E}[X])^3\right]$ et $\mu_4 = \mathbb{E}\left[(X - \mathbb{E}[X])^4\right]$ sont les moments centrés d'ordre 3 et 4 (voir [[Moment d'ordre k]]) et $\sigma$ est l'écart-type (voir [[Variance et écart-type]]).

# Interprétation

La skewness renseigne sur l'asymétrie de la distribution :

- distribution symétrique : $\gamma_1 = 0$ ;
- queue plus lourde à gauche : $\gamma_1 < 0$ ;
- queue plus lourde à droite : $\gamma_1 > 0$.

Le kurtosis mesure si la distribution est plutôt « haute et fine » ou « basse et étalée », c'est-à-dire l'importance des queues de distribution ; pour une [[Loi gaussienne|loi normale]], $\gamma_2 = 3$.

# Remarque

L'asymétrie et l'aplatissement font partie des [[Résumés numériques d'une distribution|résumés numériques d'une distribution]], aux côtés des caractéristiques de centre et de dispersion.
