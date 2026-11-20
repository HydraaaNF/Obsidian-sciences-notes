#ml-3

# Interprétation

La [[Self-attention|self-attention]] donne l'intuition que ces modèles deviennent interprétables : chaque token produisant une distribution de poids sur les autres tokens, il suffirait de lire ces poids pour lire le raisonnement du modèle.

En réalité, ce n'est pas vraiment le cas. Les cartes d'attention ne rendent pas le modèle réellement interprétable, et les visualisations qui accompagnent chaque tête de l'[[Attention multi-têtes|attention multi-têtes]] doivent être lues avec prudence.

## Ce que montre une carte d'attention

Une visualisation d'attention affiche, pour une couche et une tête données, les poids qui relient chaque token de la phrase aux autres tokens de la même phrase. Sur la phrase « The animal didn't cross the street because it was too tired », découpée en tokens `The_`, `animal_`, `didn_`, `'_`, `t_`, `cross_`, `the_`, `street_`, `because_`, `it_`, `was_`, `too_`, `tire`, `d_`, la ligne du token `it_` relie ce token à toutes les positions de la phrase, y compris celles qui le suivent (`was_`, `too_`, `tire`, `d_`), et non à un token privilégié unique.

Les traits n'ont pas tous la même épaisseur, et les plus épais ne partent pas des tokens les plus proches de `it_` : ils viennent de `The_`, `animal_`, `didn_`, `'_` et `t_`, c'est-à-dire du début de la phrase. À l'inverse, `because_`, `street_`, `the_` et `cross_`, qui précèdent `it_` de peu, comptent parmi les traits les plus fins, `because_` étant le seul token immédiatement antérieur.

| Observation sur la ligne `it_` | Lecture |
|---|---|
| liens vers toutes les positions de la phrase, ponctuation comprise | le token agrège l'ensemble du contexte, pas un antécédent unique |
| traits les plus épais depuis `The_`, `animal_`, `didn_`, `'_`, `t_` | les poids forts se portent sur le début de la phrase, à distance |
| traits fins depuis `because_`, `street_`, `the_`, `cross_` | les tokens proches de `it_`, prédécesseur immédiat compris, ne sont pas privilégiés |

Le motif observé ne se réduit donc pas à une mise en correspondance nette entre le token courant et un token précis, et il n'est pas non plus local : les poids forts se portent sur des tokens éloignés, sans décroissance nette avec la distance. C'est ce décalage entre l'intuition et le comportement observé qui rend la lecture des poids d'attention trompeuse.

# Remarque

Deux erreurs de lecture fréquentes portent sur la ligne d'un token dans une carte d'attention.

La première restreint cette ligne aux tokens qui précèdent le token courant : une carte montre les liens vers toutes les positions de la phrase, celles qui suivent comprises, et non le seul contexte antérieur.

La seconde suppose que l'épaisseur des traits décroît avec la distance, l'attention la plus marquée allant aux tokens immédiatement antérieurs. Sur la ligne `it_`, les traits les plus fins viennent au contraire de `because_`, `street_`, `the_` et `cross_`, c'est-à-dire du voisinage proche, tandis que les plus épais viennent du début de la phrase.
