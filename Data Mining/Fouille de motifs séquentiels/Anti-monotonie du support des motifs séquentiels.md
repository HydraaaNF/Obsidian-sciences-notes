#dmv-sequence_mining

# Propriétés

Soit une $k$-séquence $P$ et une $(k+1)$-séquence $P'$ qui contient $P$ au sens de l'[[Inclusion de sous-séquence]].

Propriété d'anti-monotonie du [[Support d'un motif séquentiel|support]] : si une $k$-séquence n'est pas fréquente, alors toutes les $(k+1)$-séquences qui la contiennent ne sont pas fréquentes non plus.

$$sup(P) < minsup \implies sup(P') < minsup$$

Autrement dit, le support ne peut pas augmenter quand la séquence s'allonge :

$$P \subseteq P' \implies sup(P') \le sup(P)$$

Toute séquence qui supporte $P'$ supporte aussi $P$, puisque $P$ est une sous-séquence de $P'$ : l'ensemble des séquences qui supportent $P'$ est contenu dans celui des séquences qui supportent $P$, d'où l'inégalité des supports.

La forme contraposée porte sur les séquences fréquentes : si une $(k+1)$-séquence est fréquente, alors toutes les $k$-séquences qu'elle contient sont fréquentes. La fréquence se conserve donc en descendant vers les sous-séquences.

# Exemple

Si $sup(\langle(A)(B,C)\rangle) < minsup$, alors $sup(\langle(A)(B,C)(D)\rangle) < minsup$.

La séquence $\langle(A)(B,C)(D)\rangle$ contient $\langle(A)(B,C)\rangle$ : elle n'est supportée que par des séquences qui supportent déjà $\langle(A)(B,C)\rangle$, elle ne peut donc pas franchir un seuil que celle-ci ne franchit pas.

# Interprétation

La propriété permet d'adapter l'[[Algorithme Apriori]] aux motifs séquentiels, et par là d'extraire aussi les règles d'association temporelles.

L'élagage des candidats par la propriété d'anti-monotonie est la force principale de l'[[Algorithme GSP]] : un candidat dont un sous-motif immédiat n'est pas fréquent est écarté sans que son support soit compté, ce qui évite de parcourir la [[Base de séquences]] pour lui. Le détail de cette étape de génération et d'élagage est décrit dans la [[Génération et évaluation des candidats de GSP]].

C'est cet élagage qui rend praticable l'exploration de l'[[Espace de recherche des motifs séquentiels]], où le nombre de séquences candidates croît de façon explosive avec la longueur.

# Remarque

Le sens de l'inégalité suit celui de l'inclusion. Écrire $sup(\langle(A)(B,C)(D)\rangle) > minsup$ alors que $sup(\langle(A)(B,C)\rangle) < minsup$ contredit la propriété : le support d'une séquence longue ne peut dépasser celui de la séquence courte qu'elle contient, et c'est bien $sup(P') < minsup$ qui découle de $sup(P) < minsup$.

La propriété ne dit rien des séquences qui ne sont pas comparables par inclusion : deux séquences de même longueur peuvent avoir des supports très différents, l'une être fréquente et l'autre non.

Elle est l'analogue, pour les séquences, de la [[Propriété d'anti-monotonie du support]] des itemsets, qui fonde l'élagage d'Apriori.

Sa validité doit être réexaminée dès qu'une [[Contrainte d'écart temporel|contrainte temporelle]] filtre les occurrences : la propriété n'y est plus garantie, comme le montre le [[Contre-exemple à l'anti-monotonie sous contrainte d'écart maximal]].
