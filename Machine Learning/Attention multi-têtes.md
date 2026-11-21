#ml-3

# Définition

L'**attention multi-têtes** est une couche d'attention qui découpe les features de ses entrées en $n_h$ blocs, calcule une [[Attention à produit scalaire normalisé|attention à produit scalaire normalisé]] indépendante sur chacun de ces blocs, puis concatène les sorties des têtes et les projette une dernière fois.

C'est le bloc qui apprend l'attention, cœur de l'[[Architecture du Transformer|architecture du Transformer]].

Chaque tête dispose de ses propres projections linéaires des valeurs $V$, des clés $K$ et des requêtes $Q$. Les $h$ têtes travaillent en parallèle sur les mêmes entrées, chacune produisant une sortie de même forme que sa tranche d'entrée.

# Modèle

La couche s'écrit, pour $n$ têtes :

$$\operatorname{MultiHead}(Q,K,V)=\operatorname{Concat}(\operatorname{head}_1,\dots,\operatorname{head}_n)\,W^O$$

où chaque tête est une attention appliquée à des projections propres :

$$\operatorname{head}_i=\operatorname{Attention}(QW_i^Q,\ KW_i^K,\ VW_i^V)$$

Les matrices $W_i^Q$, $W_i^K$ et $W_i^V$ sont apprises, une par tête et par rôle, et $W^O$ est la projection de sortie appliquée après la concaténation.

## Des tokens aux requêtes, clés et valeurs

La couche part d'une matrice d'entrée $T$ de forme $[4,1024]$ : quatre tokens, chacun sur une ligne. Cette matrice est la somme des plongements et de l'[[Encodage positionnel|encodages positionnels]], une ligne par token.

Trois couches Linear apprises, de taille $1024\times1024$ chacune, projettent $T$ vers les requêtes, les clés et les valeurs : $Q=TW_Q$, $K=TW_K$ et $V=TW_V$. Les trois résultats ont la même forme $[4,1024]$ que $T$.

Comme $Q$, $K$ et $V$ proviennent tous de la même matrice $T$, la couche est une [[Self-attention|self-attention]] : chaque token s'interroge sur la séquence dont il fait partie.

## Découpage en têtes

Avec $d=1024$ features et $n_h=8$ têtes, chaque tête reçoit $d_k=\frac{1024}{8}=128$ features. Les colonnes de $Q$ sont découpées en huit blocs contigus :

| Tête | Colonnes | Forme |
|---|---|---|
| 1 | 0:128 | $[4,128]$ |
| 2 | 128:256 | $[4,128]$ |
| 3 | 256:384 | $[4,128]$ |
| 4 | 384:512 | $[4,128]$ |
| 5 | 512:640 | $[4,128]$ |
| 6 | 640:768 | $[4,128]$ |
| 7 | 768:896 | $[4,128]$ |
| 8 | 896:1024 | $[4,128]$ |

Le même découpage s'applique à $K$ et à $V$. On peut voir $Q$ comme un tenseur $[4,8,128]$, dont la tête $n$ reçoit le triplet $(Q_n,K_n,V_n)$.

Chaque tête calcule alors sa propre attention et produit $V'_1,\dots,V'_8$, chacune de forme $[4,128]$. Les huit sorties sont concaténées en une matrice $[4,1024]$, puis la couche Linear $W^O$ mélange l'information des différentes têtes.

# Propriétés

Le découpage ne change ni le nombre de tokens ni la dimension totale : l'entrée $[4,1024]$ ressort en $[4,1024]$, chaque tête travaillant sur une sous-partie des features.

Les têtes sont indépendantes et calculées en parallèle : chacune possède ses projections $W_i^Q$, $W_i^K$, $W_i^V$ et son propre jeu de poids d'attention.

La couche se résume donc à la chaîne Linear, Scaled Dot-Product Attention répétée $h$ fois, Concat, puis Linear de sortie.

# Exemple

La visualisation d'une couche d'attention sur la phrase « The animal didn't cross the street because it was too tired » sépare nettement les deux régimes.

Avec une seule tête, une unique carte d'attention est affichée, et la pondération de la sortie `it_` se concentre sur `animal_` : un seul motif dominant est représenté.

Avec plusieurs têtes, les représentations d'entrée sont découpées en bandes de couleurs distinctes, une par tête, et chaque tête possède sa propre carte d'attention. La sortie `it_` agrège alors plusieurs relations simultanées, vers `animal_`, vers `street_`, vers `tired_`.

| Élément | Tête unique | Multi-têtes |
|---|---|---|
| Cartes d'attention | une seule | une par tête |
| Entrée visualisée | une bande de couleur par token | plusieurs bandes empilées par token |
| Relations capturées | un seul motif dominant | plusieurs motifs en parallèle |
| Sortie `it_` | lien marqué vers `animal_` | liens vers plusieurs tokens |

# Remarque

Les visualisations d'attention montrent bien des motifs distincts par tête, mais elles ne suffisent pas à rendre le modèle réellement interprétable : la lecture des cartes est plus fragile qu'elle n'en a l'air, comme le détaille [[Interprétabilité de l'attention|l'interprétabilité de l'attention]].
