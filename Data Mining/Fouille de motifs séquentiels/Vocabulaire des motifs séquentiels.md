#dmv-sequence_mining

# Définition

- Soit $I=\{i_1, \dots, i_n\}$ l'ensemble de tous les items.
- Un **itemset** est un sous-ensemble de $I$, noté $(i_1 i_2 \dots i_m)$ avec $i_k \in I$.
- Une **séquence** $s$ est une liste ordonnée d'itemsets, notée :
$$\langle s_1 s_2 \dots s_p\rangle$$
- Une **$k$-séquence** est un motif séquentiel de longueur $k$, c'est-à-dire formé de $k$ items.

L'ordre d'une séquence est soit **implicite**, porté par la position des éléments, soit **explicite**, porté par les éléments accompagnés d'un horodatage.

# Exemple

Ordre implicite, une séquence d'ADN :
$$\text{ACCGT} \Leftrightarrow \langle \text{A}, \text{C}, \text{C}, \text{G}, \text{T}\rangle$$

Ordre explicite, un journal d'événements :
$$\langle (1, \text{pushButton}), (2, \text{endOfWorld})\rangle$$

La longueur d'une séquence se compte en items et non en itemsets : la séquence
$$\langle (\text{a}\ \text{b})\ (\text{c})\ (\text{d}\ \text{e})\rangle$$
compte $2+1+2=5$ items et est donc une $5$-séquence.

# Remarque

Ce vocabulaire est celui sur lequel se construit la [[Base de séquences|base de séquences]] : les items et les itemsets sont les objets déjà manipulés par les [[Items, itemsets et base de transactions|bases de transactions]], et la séquence y ajoute l'ordre entre les itemsets.

Toute séquence de longueur $k$ est un [[Motif séquentiel|motif séquentiel]] candidat ; la comparaison d'une séquence à un motif, qui décide de la présence du motif, se fait par [[Inclusion de sous-séquence]] et commande la notion de support.

Le même cadre décrit aussi bien des données séquentielles classiques que des données structurées, comme le montre l'[[Extension de la fouille de motifs aux données structurées|extension aux données structurées]].
