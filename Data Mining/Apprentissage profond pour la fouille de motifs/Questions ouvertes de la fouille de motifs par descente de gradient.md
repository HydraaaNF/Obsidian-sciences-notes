#dmv-pattern_mining_vs_deep_learning

La recherche d'un [[Ensemble de motifs]] peut être conduite selon deux familles d'optimisation : des heuristiques guidées par la longueur de description minimale, qui parcourent l'espace des motifs candidats, et l'optimisation continue d'un [[Auto-encodeur de motifs]], qui ajuste ses poids par [[Descente de gradient]]. Leur comparaison laisse une question ouverte.

# Remarque

L'optimisation par [[Descente de gradient]] donne de bons résultats, alors que celle des approches fondées sur la longueur de description minimale (MDL) n'en donne pas. Le constat est net, mais aucune explication n'est donnée.

# Interprétation

Trois questions découlent de ce constat, et aucune n'a de réponse établie.

- Pourquoi la descente de gradient fonctionne-t-elle là où l'approche fondée sur la longueur de description échoue ?
- Certaines façons d'optimiser, comme l'aller-retour entre espace binaire et espace continu décrit dans [[Poids binaires et optimisation différentiable]], pourraient-elles être empruntées pour améliorer les heuristiques fondées sur la longueur de description ?
- Plus généralement, se peut-il que l'espace des motifs ait été mal exploré jusqu'ici ?

La dernière question ne porte pas sur un réglage d'algorithme : elle met en cause la manière dont l'espace des motifs est parcouru.
