#dmv-sequence_mining

# Définition

WINEPI est l'algorithme de [[Fouille d'épisodes dans une séquence d'événements|fouille d'épisodes]] qui ramène le problème à un comptage sur les [[Fenêtre glissante de WINEPI|fenêtres glissantes]] d'une [[Séquence d'événements]] : il énumère les [[Épisode|épisodes]] niveau par niveau, à la manière de l'[[Algorithme Apriori]], en ne retenant comme candidats d'une taille donnée que les épisodes dont tous les sous-épisodes sont déjà [[Fréquence d'un épisode|fréquents]].

# Algorithme

Entrées :

- un ensemble $R$ de types d'événements ;
- une séquence d'événements $s$ sur $R$ ;
- un ensemble $E$ d'épisodes, parallèles ou série ;
- une largeur de fenêtre $win$ ;
- un seuil de fréquence $min\_fr$.

Sortie : la collection des épisodes fréquents, notée $F(s, win, min\_fr)$.

```text
C_1 ← {α ∈ E | |α| = 1} ;
i ← 1 ;
while C_i ≠ ∅ do
    // Database pass
    F_i(s, win, min_fr) ← {α ∈ C_i | fr(α, s, win) ≥ min_fr} ;   // Test of frequency
    i ← i + 1 ;
    // Candidate generation
    C_i ← {α ∈ E | |α| = i et ∀β ∈ E, β ⊆ α ⇒ β ∈ F_|β|(s, win, min_fr)} ;
for all i do output F_i(s, win, min_fr)
```

# Interprétation

Le niveau 1 est formé de tous les épisodes de $E$ de taille 1 : aucun filtrage préalable n'est possible, et la première passe sur la base mesure directement leur fréquence. Chaque tour de boucle enchaîne ensuite deux traitements.

La passe sur la base ne conserve parmi les candidats du niveau $i$ que ceux dont la fréquence atteint le seuil :

$$F_i(s, win, min\_fr) = \{\alpha \in C_i \mid fr(\alpha, s, win) \ge min\_fr\}$$

La génération des candidats puise dans $E$ les épisodes de taille $i$ dont tous les sous-épisodes sont déjà fréquents, chacun au niveau de sa propre taille :

$$C_i = \{\alpha \in E \mid |\alpha| = i \text{ et } \forall \beta \in E, \beta \subseteq \alpha \Rightarrow \beta \in F_{|\beta|}(s, win, min\_fr)\}$$

La condition de génération est exactement la traduction de l'[[Anti-monotonie des épisodes|anti-monotonie de la fréquence]] : un épisode dont un sous-épisode n'est pas fréquent ne peut pas être fréquent, donc il est inutile de le compter. La boucle s'arrête dès que $C_i$ est vide, c'est-à-dire dès qu'aucun épisode de taille $i$ ne réunit les sous-épisodes fréquents requis. Le résultat est la réunion des niveaux produits, $F_1, F_2, \dots$ : chaque épisode fréquent y figure une fois, au niveau de sa taille.

# Exemple

On cherche tous les épisodes parallèles de fréquence supérieure à 40 %, soit présents dans au moins 5 des onze fenêtres de la séquence $D, C, A, B, D, A, B, C$ découpée par une fenêtre d'une largeur de 40 s.

- Les singletons, épisodes parallèles de taille 1, sont $A$, $B$, $C$ et $D$ ; tous sont fréquents.
- Les candidats de taille 2, construits à partir de ces singletons fréquents, sont $AB$, $AC$, $AD$, $BC$, $BD$ et $CD$ ; tous sont fréquents.
- Les candidats de taille 3, construits de même, sont $ABC$, $ABD$, $ACD$ et $BCD$ ; seul $ABD$ apparaît dans plus de quatre fenêtres.
- Aucun épisode candidat de taille 4 n'est engendré.

Le niveau 3 illustre l'élagage : les six épisodes parallèles de taille 2 étant fréquents, les quatre combinaisons de taille 3 sont testées, mais trois d'entre elles disparaissent à la passe sur la base et ne peuvent plus servir de sous-épisodes fréquents.

# Remarque

L'ensemble $E$ fixe la famille d'épisodes explorée, parallèles ou série : l'algorithme ne considère que les épisodes de $E$, et la génération des candidats ne construit rien en dehors de cet ensemble.

Le tarissement de la boucle s'explique par la condition de génération : après le niveau 3 de l'exemple, seul $ABD$ reste fréquent parmi les épisodes de taille 3, et aucun épisode de taille 4 n'a tous ses sous-épisodes de taille 3 fréquents.

L'approche est celle des méthodes générer et élaguer, avec une passe sur la base par niveau. L'alternative consiste à se passer de fenêtre glissante et à chercher directement les occurrences exactes de chaque épisode : c'est le principe de l'[[Algorithme MINEPI]], fondé sur l'[[Occurrence minimale d'un épisode|occurrence minimale]].
