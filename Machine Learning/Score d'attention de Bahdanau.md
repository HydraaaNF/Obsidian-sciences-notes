#ml-3

# Modèle

À chaque pas de temps $t$, le décodeur dispose d'un état caché $d_t$. La question à résoudre est la suivante : étant donné $d_t$, quelle attention $a_i \in [0, 1]$ faut-il accorder à chacun des états cachés $h_1, \dots, h_N$ produits par l'encodeur ?

Le vecteur d'attention au pas $t$ rassemble ces poids : $\mathbf{a}_t = [a_1, \dots, a_N]$. Appliqué aux états, il donne le produit terme à terme, ou produit de Hadamard, $\mathbf{a}_t \odot \mathbf{h} = [a_1 h_1, a_2 h_2, \dots, a_N h_N]$.

La solution consiste à poser $\mathbf{a}_t = f(d_t, \mathbf{h})$, où $f$ est une **fonction apprise**. Elle est implémentée par des couches denses, dont la fonction d'activation finale ramène la sortie dans $[0, 1]$ : sigmoïde ou [[Fonction softmax|softmax]].

Le décodeur $D$ prédit alors une nouvelle sortie à partir de la combinaison pondérée :

$$(\hat{y}_{t+1}, d_{t+1}) = D(\hat{y}_t, d_t, \mathbf{a}_t \odot \mathbf{h})$$

Autrement dit, $\mathbf{a}_t \odot \mathbf{h}$ remplace la seule dépendance à l'état caché final de l'encodeur : le décodeur consulte l'ensemble des états, pondérés par leur pertinence pour l'état courant.

# Définition

Le **score de compatibilité** d'un état d'encodeur $h_i$ avec l'état de décodeur $d_t$ est un score additif appris par une petite couche dense :

$$e_i = \mathbf{w} \cdot \tanh(W d_t + U h_i)$$

où $W$ et $U$ sont des matrices de poids et $\mathbf{w}$ un vecteur de poids. Les scores sont ensuite normalisés en une distribution d'attention :

$$\mathbf{a}_t = \operatorname{softmax}(\mathbf{e})$$

Chaque poids vérifie donc $a_i \in [0, 1]$ et, le softmax imposant une somme unitaire, $\sum_i a_i = 1$. Le vecteur de contexte est la moyenne pondérée des états d'encodeur :

$$c_t = \sum_i a_i h_i$$

# Interprétation

L'attention se lit comme un **moteur de recherche jouet** à trois rôles :

- la **requête** (*query*) est $d_t$, ce que le décodeur cherche ;
- les **documents** sont $h_1, \dots, h_N$, les états de l'encodeur ;
- le **score de pertinence** $a_i$ mesure l'adéquation du document $h_i$ à la requête $d_t$, et le softmax garantit $\sum_i a_i = 1$ ;
- le **résultat** $c_t = \sum_i a_i h_i$ est le mélange des documents selon leur score.

Le mécanisme permet ainsi au décodeur de se focaliser sur les parties utiles de la séquence d'entrée au moment où il produit chaque sortie, et non sur un unique vecteur résumé.

# Exemple

Dans l'analogie du moteur de recherche, une requête $d_t$ est comparée à quatre documents $h_1, h_2, h_3, h_4$. La distribution d'attention obtenue n'est pas uniforme : $h_2$ reçoit le score le plus élevé, $h_3$ un score intermédiaire, $h_1$ et $h_4$ des scores faibles. Le vecteur de contexte est alors dominé par $h_2$, tout en conservant une contribution des autres états.

# Remarque

Deux lectures du score coexistent. La première, celle de l'analogie du moteur de recherche, présente $a_i$ comme une **similarité** : « à quel point $h_i$ correspond à $d_t$ ». La seconde, propre à l'attention de Bahdanau, précise que le score est **appris** par une petite couche dense, $e_i = \mathbf{w} \cdot \tanh(W d_t + U h_i)$, puis normalisé par un softmax.

C'est la seconde lecture qui est retenue ici : il s'agit d'une **compatibilité apprise**, et non d'une similarité véritable au sens d'un produit scalaire. Ce score appris s'oppose au score de l'[[Attention à produit scalaire normalisé|attention à produit scalaire normalisé]], $\frac{q_i \cdot k_j}{\sqrt{d_k}}$, qui mesure une véritable similarité entre une requête et une clé.

Le caractère appris de $f$ distingue cette attention du [[Mécanisme d'attention|mécanisme d'attention]] à score fixé : les poids de la couche dense sont entraînés avec le reste du modèle, en même temps que les paramètres de l'encodeur et du décodeur de l'[[Attention dans un encodeur-décodeur|encodeur-décodeur]].

Sur le plan des notations, le symbole $\otimes$ désigne couramment le produit tensoriel ; le produit terme à terme employé ici est un produit de Hadamard, noté $\odot$.
