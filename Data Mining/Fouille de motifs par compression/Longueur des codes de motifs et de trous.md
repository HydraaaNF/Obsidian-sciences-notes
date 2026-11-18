#dmv-pattern_mining_with_information_theory
# Définition

Une [[Table de codes pour séquences d'événements|table de codes de séquences]] associe à chaque motif $X$ un code de motif $code_p(X)$, un code de trou $code_g(X)$ et un code de non-trou $code_n(X)$. La longueur de chacun de ces codes suit la [[Probabilité et longueur optimale d'un code|longueur optimale]] pour la probabilité d'emploi correspondante.

La longueur du code de motif de $X$ dans la table $CT$ est

$$L(code_p(X) \mid CT) = -\log\left( \frac{usage(X)}{\sum_{Y \in CT} usage(Y)} \right)$$

où $usage(X)$ compte le nombre d'emplois du motif $X$ pour couvrir la base.

Pour les positions internes à un motif, on note

- $gaps(X)$ le nombre de trous dans l'usage du motif $X$ ;
- $fills(X)$ le nombre de non-trous dans l'usage du motif $X$, avec

$$fills(X) = usage(X)(|X| - 1) - gaps(X)$$

Chaque emploi du motif $X$ porte $|X| - 1$ liens internes : l'ensemble des liens à coder compte donc

$$gaps(X) + fills(X) = usage(X)(|X| - 1)$$

Les longueurs des deux codes correspondants sont

$$L(code_g(X) \mid CT) = -\log\left( \frac{gaps(X)}{gaps(X) + fills(X)} \right)$$

et

$$L(code_n(X) \mid CT) = -\log\left( \frac{fills(X)}{gaps(X) + fills(X)} \right)$$

# Interprétation

Le code de motif obéit à la même règle que les entrées d'une [[Table de codes|table de codes]] d'itemsets : la probabilité d'un motif est son usage rapporté à la somme des usages de la table, si bien qu'un motif souvent employé reçoit un code court.

Les deux autres codes ne portent pas sur le motif entier mais sur les liens entre ses événements consécutifs. Un motif de taille $|X|$ employé $usage(X)$ fois présente $usage(X)(|X| - 1)$ tels liens, chacun étant soit un trou, soit un non-trou : c'est exactement la quantité $gaps(X) + fills(X)$, et les deux probabilités se partagent ces positions et somment à un.

Un motif réduit à un seul événement n'a aucun lien interne : $gaps(X) = fills(X) = 0$, et son emploi ne consomme ni code de trou ni code de non-trou.

# Remarque

Les $|X| - 1$ liens internes d'un emploi se répartissent entre trous et non-trous, d'où $fills(X) = usage(X)(|X| - 1) - gaps(X)$. Écrire $fills(X) = usage(X)(|X| - 1)$ est une erreur fréquente : cette quantité compte tous les liens internes, trous compris, si bien qu'un motif dont l'usage comporte au moins un trou se verrait attribuer plus de non-trous qu'il n'en a. Le dénominateur commun $gaps(X) + fills(X)$ dépasserait alors le nombre réel de liens internes, chaque trou y étant compté deux fois : les effectifs, ce dénominateur et les deux probabilités qui en dérivent seraient faux, même si ces probabilités somment encore à un.

Ces longueurs élémentaires sont les briques des deux flux encodés : la longueur du flux de motifs $L(C_p \mid CT)$ et celle du flux de trous $L(C_g \mid CT)$ s'en déduisent par sommation, et forment la [[Longueur de description d'une base de séquences]].

Contrairement à un itemset, un motif de séquence peut enjamber des positions de la séquence : les événements qu'il couvre ne sont pas nécessairement contigus, et c'est précisément ce que le code de trou signale pour chaque lien.
