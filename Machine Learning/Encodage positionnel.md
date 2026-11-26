#ml-3

# Définition

L'**encodage positionnel** est un vecteur ajouté au plongement de chaque token pour y inscrire la position $t$ de ce token dans la séquence. Il fournit l'information d'ordre que la [[Self-attention]] ne voit pas.

L'opération a lieu à la sortie de la [[Couche de plongement]], avant le premier bloc de l'[[Architecture du Transformer]]. Pour un token de plongement $E_t$ à la position $t$, l'entrée du bloc vaut

$$x_t = E_t + p_t$$

la somme se faisant terme à terme, dans un espace de dimension $d$ : l'encodage n'est pas concaténé au plongement, ce qui doublerait la dimension.

Les notations :

- $t \in \{0, 1, \dots, T-1\}$ : la position du token dans la séquence, de longueur $T$ ;
- $d$ : la dimension du plongement des tokens, donc celle de $p_t$, un nombre pair ;
- $k \in \{0, \dots, d/2 - 1\}$ : l'indice de la paire de dimensions $(2k, 2k+1)$ ;
- $w_k$ : la fréquence de cette paire.

L'encodage sinusoïdal de dimension $d$ attribue à la position $t$ un vecteur dont les composantes alternent sinus et cosinus :

$$p_t^{(2k)} = \sin(w_k t)$$

$$p_t^{(2k+1)} = \cos(w_k t)$$

$$w_k = \frac{1}{10000^{\frac{2k}{d}}}$$

Chaque paire de dimensions parcourt donc un cercle à sa propre vitesse : les basses dimensions, où $k$ est petit et $w_k$ proche de $1$, tournent vite, les hautes dimensions très lentement.

# Interprétation

L'attention compare des **contenus** : le score $q_i \cdot k_j$ de deux tokens ne dépend pas de l'endroit où ils se trouvent. Deux phrases faites des mêmes mots dans un ordre différent produisent donc exactement les mêmes scores d'attention.

Sans information de position, le Transformer voit la séquence comme un **sac de tokens**. Un réseau récurrent, lui, lisait la séquence dans l'ordre, ce qui rendait l'ordre implicite.

La solution consiste à ajouter à chaque plongement un vecteur qui encode sa position $t$ : l'encodage se combine à la [[Couche de plongement]], à sa sortie et avant le premier bloc de l'[[Architecture du Transformer]].

# Exemple

Deux phrases opposées par le sens mais identiques en contenu :

| Phrase | Score de *bites* vers *dog* | Sens |
|---|---|---|
| the **dog bites** the man | $s$ | le chien mord |
| the man **bites** the **dog** | le même $s$ | l'homme mord |

Dans la première phrase, le lien d'attention va de *dog* vers *bites* ; dans la seconde, de *bites* vers *dog*. Le score est identique alors que l'interprétation est inverse : seul l'ordre distingue les deux lectures.

# Propriétés

Sur les basses dimensions, l'encodage varie fortement d'une position à l'autre et porte donc l'information de position ; sur les dimensions suivantes, il se stabilise et laisse la place à la sémantique. Le modèle apprend à organiser l'information le long des dimensions selon cette répartition.

La carte de chaleur Position × Depth de l'encodage, lue sur la figure, s'interprète ainsi :

| Région | Depth | Aspect observé | Lecture |
|---|---|---|---|
| basses dimensions | 0 à 40 environ | bandes alternées rouge et bleu, inclinées | les activations oscillent fortement d'une position à l'autre |
| structure diagonale | 10 à 30 environ | rayures obliques | décalage progressif de l'oscillation avec la position |
| transition | 40 à 50 environ | mélange des deux régimes | passage progressif d'un régime à l'autre |
| hautes dimensions | 50 à 120 | bleu foncé uniforme, fines colonnes claires | direction dominante commune à toutes les positions |

La carte porte en ordonnée la position, de 0 à 50, et en abscisse la profondeur, de 0 à 120, sur une échelle de couleur allant de $-1{,}00$ (rouge foncé) à $+1{,}00$ (bleu foncé). Les dimensions basses portent la position, les hautes la sémantique, ce qui confirme la répartition décrite plus haut.

# Liens avec d'autres lois

- Dans l'[[Attention multi-têtes]], l'entrée $T$ est la somme des plongements des tokens et de leurs encodages positionnels.
- L'entrée de [[BERT et le modèle de langage masqué|BERT]] additionne de même le plongement de chaque token et son encodage positionnel.
