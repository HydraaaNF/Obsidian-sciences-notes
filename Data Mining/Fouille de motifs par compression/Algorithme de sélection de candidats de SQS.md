#dmv-pattern_mining_with_information_theory
# Algorithme

SQS-CANDIDATES sélectionne, parmi un ensemble de motifs candidats $\mathcal{F}$ fourni par un autre algorithme de fouille, un sous-ensemble $\mathcal{P}$ de motifs non singletons qui compresse une base de séquences $D$. Le principe est celui de [[Algorithme KRIMP|KRIMP]] : les candidats sont examinés un par un, et un candidat n'entre dans la table que si la compression progresse.

```text
SQS-CANDIDATES(F, D)
input  : motifs candidats F
output : ensemble P de motifs non singletons minimisant heuristiquement
         le problème de la table de codes minimale

1. ordonner les motifs X de F selon L(D, {X}) ;
2. P ← ∅ ;
3. pour chaque X de F dans cet ordre faire
4.     si L(D, P ∪ X) < L(D, P) alors          // gain apporté par le motif ?
5.         P ← PRUNE(P ∪ X, D, faux) ;         // étape d'élagage
6. P ← PRUNE(P, D, vrai) ;
7. ordonner les motifs X de G selon L(D, P) - L(D, P privé de X) ;
8. retourner P ;
```

# Interprétation

Le tri initial classe les candidats selon la longueur de description d'une table réduite au seul motif $X$ : la boucle les visite dans cet ordre, ce qui fait entrer d'abord les motifs les plus avantageux pris isolément.

La boucle est gloutonne : chaque candidat est ajouté à la table courante, la base est réencodée, et l'ajout n'est conservé que si la longueur totale diminue. L'élagage de la ligne 5 accompagne chaque acceptation, puisque l'arrivée d'un motif modifie les usages des entrées déjà présentes, donc la longueur de leurs codes.

Le troisième argument de `PRUNE` distingue les deux moments de l'élagage : `faux` après chaque ajout accepté, `vrai` une fois la boucle terminée. L'élagage consiste à retirer les entrées dont le retrait raccourcit encore la description, en propageant les usages libérés, selon le principe de l'[[Élagage après acceptation d'une table de codes]].

La ligne 7 reclasse enfin les motifs retenus selon ce que coûterait leur retrait : l'écart $L(D, \mathcal{P}) - L(D, \mathcal{P} \setminus X)$ mesure la perte subie si $X$ disparaissait de la table.

# Remarque

La ligne 7 trie les motifs d'un ensemble $G$ que l'algorithme n'introduit nulle part : ses seules variables sont $\mathcal{F}$ et $\mathcal{P}$. Cet ensemble doit se lire comme l'ensemble des motifs retenus dans $\mathcal{P}$, et le tri comme un classement des motifs sélectionnés par importance ; il ne modifie pas l'ensemble $\mathcal{P}$ retourné à la ligne 8.

Le résultat dépend entièrement de la qualité de $\mathcal{F}$ : l'algorithme ne construit aucun motif, il choisit seulement dans un vivier fourni de l'extérieur. C'est la différence de principe avec l'[[Algorithme de recherche progressive de SQS]], qui génère ses propres candidats au fil des itérations, peut s'interrompre à tout moment et rend le meilleur modèle courant.
