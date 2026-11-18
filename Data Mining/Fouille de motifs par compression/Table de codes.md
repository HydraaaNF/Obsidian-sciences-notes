#dmv-pattern_mining_with_information_theory

# Définition

Une **table de codes** (en anglais *code table*, notée $CT$) est un ensemble d'[[Items, itemsets et base de transactions|itemsets]] muni d'un encodage : chaque itemset effectivement utilisé reçoit un code.

Les itemsets sont construits sur un ensemble d'items $I$.

# Exemple

Pour $I = \{A, B, C, D, E\}$, une table de codes compte huit entrées :

| Itemset | Code |
|---|---|
| $\{A, C\}$ | bleu clair |
| $\{B, D\}$ | bleu foncé |
| $\{C, E\}$ | bleu clair |
| $\{A\}$ | bleu foncé |
| $\{B\}$ | bleu clair |
| $\{C\}$ | aucun code |
| $\{D\}$ | bleu clair |
| $\{E\}$ | bleu foncé |

Les codes sont figurés par deux nuances de bleu, et l'entrée $\{C\}$ ne reçoit aucun code.

# Remarque

Le modèle d'une approche par compression prend cette forme : la table est le modèle $M$, et ses codes servent à encoder les transactions de la base.

Réduite aux seuls itemsets singletons, la table devient la [[Table de codes standard]]. Le parcours d'une transaction pour choisir ses codes est décrit dans [[Couverture d'une transaction par une table de codes]], et la longueur attribuée à chaque code dépend de son usage dans [[Probabilité et longueur optimale d'un code]].

Le choix de la table optimale, lui, n'offre aucune structure exploitable pour une énumération directe : voir [[Recherche de la table de codes optimale]].
