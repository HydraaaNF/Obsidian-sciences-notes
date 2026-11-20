#ml-3

# Définition

La **self-attention**, ou *intra-attention*, est le cas du [[Mécanisme d'attention]] où les requêtes $Q$, les clés $K$ et les valeurs $V$ proviennent tous de la **même** séquence.

L'entrée $T$ est la séquence de plongements, éventuellement additionnée de l'encodage positionnel, avec une ligne par token. Chacun des trois tenseurs est obtenu à partir de ce même $T$ par une couche linéaire qui lui est propre :

$$Q = T W_Q$$

$$K = T W_K$$

$$V = T W_V$$

Les projections sont apprises et conservent la forme de $T$. Pour $T$ de forme $[4, 1024]$, chacune des matrices $W_Q$, $W_K$ et $W_V$ est de forme $1024 \times 1024$, et $Q$, $K$ et $V$ restent de forme $[4, 1024]$.

Le rôle des trois tenseurs se lit ainsi :

- $Q$ : ce que chaque élément cherche, la question ;
- $K$ : ce que chaque élément offre, l'index comparé aux requêtes ;
- $V$ : ce qu'il rend une fois sélectionné, le contenu.

Le calcul enchaîne la [[Attention à produit scalaire normalisé]] sur $Q$, $K$ et $V$, puis la concaténation des têtes et une couche linéaire, au sein de l'[[Attention multi-têtes]]. Dans un décodeur, le [[Masque causal]] restreint en outre les positions visibles.

# Interprétation

La self-attention se lit comme un moteur de recherche en miniature : une requête interroge un index de clés, et la meilleure correspondance renvoie la valeur associée.

- La requête $q_i$ est ce que l'élément $i$ cherche ;
- les clés $k_j$ sont ce que chaque élément offre, l'index ;
- les valeurs $v_j$ sont ce que chaque élément contient, le contenu.

| clé | valeur |
| --- | --- |
| $k_1$ | $v_1$ |
| $k_2$ | $v_2$ |
| $k_3$ | $v_3$ |
| $k_4$ | $v_4$ |

La requête $q_i$ est comparée à chaque clé $k_j$ par le score $q_i \cdot k_j / \sqrt{d_k}$. Ce produit scalaire est une véritable similarité : il est grand lorsque $q_i$ et $k_j$ sont alignés. Un softmax sur les scores donne les poids $a_{ij}$, et le résultat est la moyenne pondérée des valeurs :

$$v'_i = \sum_j a_{ij} v_j$$

Le parcours complet s'écrit donc : $q_i$ interroge les couples $(k_1, v_1), \dots, (k_4, v_4)$, les scores $a_{ij}$ pondèrent les valeurs, et la somme fournit $v'_i$.

# Remarque

Dans l'[[Réseau récurrent]], la clé et la valeur ne font qu'un : $k_j = v_j = h_j$, et le décodeur fournit les requêtes $Q = d_i$ tandis que l'encodeur fournit $K = V = h_i$. En self-attention, la clé comparée et la valeur récupérée peuvent différer, car ce sont deux projections $W_K$ et $W_V$ du même token, et $q$, $k$, $v$ sont issus de la même séquence.
