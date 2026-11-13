#dmv-sequence_mining

# Définition

L'écart temporel (gap) d'un [[Motif séquentiel]] est le nombre d'unités de temps séparant deux itemsets successifs de ce motif.

Une contrainte d'écart temporel impose que cet écart reste dans un intervalle fixé :

$$gap_{\min} \le gap \le gap_{\max}$$

Un écart nul, $gap = 0$, correspond à des itemsets qui se succèdent immédiatement.

Un écart infini ne restreint plus rien : seule la séquentialité, au sens de l'[[Inclusion de sous-séquence]], est exigée.

# Interprétation

La contrainte répond à la question : jusqu'à quel écart considère-t-on encore qu'il y a séquentialité ?

Intuitivement, elle revient à supprimer les événements trop éloignés les uns des autres : deux itemsets séparés par un trop grand nombre d'unités de temps ne forment plus une suite d'événements liés.

# Exemple

Le choix des bornes distingue trois régimes.

- $gap = 0$ : la contrainte impose la contiguïté, les transactions se succèdent immédiatement, comme des ventes de A, B puis C en trois semaines successives (unité de temps : la semaine). Voir [[Sous-séquence contiguë]].
- $gap_{\min} \le gap \le gap_{\max}$ : les transactions ne peuvent être ni trop proches ni trop éloignées. Si quelqu'un loue *Matrix Reloaded*, il louera probablement aussi *Matrix Revolutions* dans les quinze jours (unité de temps : le jour), d'où une borne haute à quinze jours.
- Écart infini : aucune borne, seule la séquentialité compte, et l'on retrouve la fouille sans contrainte temporelle.

# Algorithme

Deux stratégies prennent en compte les contraintes d'écart.

- Fouiller les motifs séquentiels sans contrainte d'écart, puis post-traiter les motifs découverts pour ne garder que ceux qui la respectent.
- Modifier l'[[Algorithme GSP]] pour élaguer directement les candidats qui violent les contraintes d'écart.

# Remarque

La seconde stratégie suppose que l'élagage reste fondé, ce qui pose la question du maintien du principe d'Apriori, c'est-à-dire de l'[[Anti-monotonie du support des motifs séquentiels|anti-monotonie du support]], sous contrainte d'écart : un contre-exemple montre qu'elle tombe sous contrainte d'écart maximal, voir [[Contre-exemple à l'anti-monotonie sous contrainte d'écart maximal]].

Un algorithme dédié à cette famille de contraintes est présenté dans [[Algorithme Gap-BIDE]].

La contrainte fait partie des [[Contraintes temporelles en fouille de motifs séquentiels]], aux côtés de la [[Durée des séquences]] et de la [[Fenêtre de repliement des événements]].
