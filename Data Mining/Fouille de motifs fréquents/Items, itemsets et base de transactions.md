#dmv-frequent_itemsets_mining

# Définition

- Une **base d'items** est un ensemble fini $A = \{a_1, \dots, a_n\}$ ; ses éléments $a_1, \dots, a_n$ sont les **items**.
- Tout sous-ensemble $I \subseteq A$ est un **itemset**, c'est-à-dire un ensemble d'items considéré comme une entité.
- Un **$k$-itemset** est un itemset contenant $k$ items.
- Une **base de transactions** est une suite $T = (t_1, \dots, t_m)$ de transactions, chacune étant un sous-ensemble de la base d'items :
$$\forall i,\ t_i \subseteq A$$
- L'**indice de transaction** de la transaction $t_j$ est son rang dans la base :
$$ tid(t_j) = j. $$

Chaque transaction est donc un itemset particulier parmi les $m$ lignes de la base : une transaction contient tout ou partie des items de $A$, et son indice $tid$ sert à la désigner sans ambiguïté. Dans les données d'un supermarché, cadre de l'[[Analyse du panier de la ménagère]], une transaction est le panier d'un client et les items sont les articles qui y figurent.

# Exemple

Base d'items $A = \{A, B, C, D, E\}$ et base de transactions $T = (t_1, \dots, t_6)$ écrite en lignes :

| Transaction | A | B | C | D | E |
| :-: | :-: | :-: | :-: | :-: | :-: |
| **1** | X | X | X | X | X |
| **2** | X | X | X |   | X |
| **3** |   |   | X |   |   |
| **4** |   | X | X |   |   |
| **5** | X | X | X | X |   |
| **6** | X | X | X |   |   |

Lecture de la base :

- $t_2 = \{A, B, C, E\}$ et $tid(t_2) = 2$ ;
- $t_3 = \{C\}$ est un $1$-itemset ;
- $\{B, C\}$ est un $2$-itemset, contenu dans les transactions $t_1$, $t_2$, $t_4$, $t_5$ et $t_6$ ;
- $A = \{A, B, C, D, E\}$ est lui-même un itemset, égal à la transaction $t_1$.

# Remarque

La base écrite ci-dessus, avec une ligne par transaction et une colonne par item, est dite en **format horizontal** : c'est la forme sous laquelle la base est lue par l'algorithme [[Algorithme Apriori|Apriori]], pour lequel chaque transaction est parcourue afin d'y reconnaître les itemsets candidats. Le [[Format vertical des transactions|format vertical]] réorganise la même information en associant à chaque itemset la liste de ses indices de transaction, ce qui rend l'indice de transaction $tid$ central.

Les itemsets sont les objets de base sur lesquels se définissent le [[Support d'un itemset|support]] et la notion d'[[Itemset fréquent|itemset fréquent]] ; ce sont eux qui servent ensuite de briques aux [[Règle d'association et confiance|règles d'association]], une règle $X \to Y$ portant sur deux itemsets disjoints.

La transaction binaire décrite ici est l'entrée du réseau qui apprend un ensemble de motifs : voir [[Encodage d'une transaction en motifs]].

La base binaire se relit comme une matrice de cases, dont un motif recouvre localement certaines lignes et certaines colonnes : c'est la lecture du [[Motif comme propriété locale des données]].
