#ml-2

# Définition

Une **décomposition autorégressive** exprime la densité jointe d'un vecteur $\mathbf{x} = (x_1, \dots, x_T)$ comme le produit des densités conditionnelles de chaque composante sachant toutes les précédentes, dans un ordre fixé à l'avance :

$$
p(\mathbf{x}) = p(x_1)\, p(x_2 \mid x_1)\, p(x_3 \mid x_1, x_2) \cdots p(x_T \mid x_1, \dots, x_{T-1})
$$

soit, sous forme condensée,

$$
p(\mathbf{x}) = \prod_{t=1}^{T} p(x_t \mid x_1, \dots, x_{t-1}).
$$

L'ordre des variables est celui de la séquence : la composante $x_t$ n'est conditionnée que par le passé $x_1, \dots, x_{t-1}$, jamais par le futur. Le produit définit un [[Modèle génératif]] dont chaque facteur est une distribution portant sur la seule variable courante.

# Propriétés

Chaque facteur $p(x_t \mid x_1, \dots, x_{t-1})$ est une densité conditionnelle de la variable $x_t$, et le produit de ces facteurs forme une densité jointe sur $\mathbf{x}$.

Modéliser la densité jointe revient ainsi à modéliser $T$ distributions à une variable, chacune conditionnée par un contexte de longueur croissante.

Lorsque le champ réceptif est borné à $R$, la sortie en $t$ ne dépend que des $R$ échantillons précédents :

$$
p(x_t \mid x_1, \dots, x_{t-1}) = p(x_t \mid x_{t-R}, \dots, x_{t-1}).
$$

# Interprétation

La factorisation ramène la modélisation d'une densité en grande dimension à une suite de prédictions unidimensionnelles conditionnées par le passé. C'est la forme que prend un modèle autorégressif de génération de séquences, comme [[Architecture WaveNet]].

Elle rend l'échantillonnage possible de proche en proche : on tire $x_1$ selon $p(x_1)$, puis $x_2$ selon $p(x_2 \mid x_1)$, et ainsi de suite jusqu'à $x_T$. Chaque échantillon tiré est ajouté à l'entrée, puis l'opération recommence : c'est la [[Génération d'une séquence]] mise en œuvre par l'[[Inférence autorégressive]].

Le prix de cette simplicité est le caractère séquentiel de la génération : un pas de calcul par échantillon, soit 16 000 pas pour une seconde d'audio.

# Algorithme

Échantillonnage autorégressif d'une séquence de longueur $T$ :

1. Tirer $x_1$ selon $p(x_1)$.
2. Tirer $x_t$ selon $p(x_t \mid x_1, \dots, x_{t-1})$ pour $t = 2, \dots, T$.
3. Concaténer chaque nouvel échantillon au contexte, puis répéter.

À l'entraînement, chaque position $t$ fournit une paire formée du contexte et de la cible $x_t$, et la perte est calculée sur cette cible unique : c'est le *teacher forcing*, une seule passe avant suffit pour toutes les positions.

# Exemple

Sur une séquence audio de longueur $n = 12$ et de champ réceptif $R = 4$, la distribution de l'échantillon $x_9$ se réduit au conditionnement par les quatre échantillons précédents $x_5, x_6, x_7, x_8$.

# Remarque

La factorisation est exacte : elle ne suppose aucune indépendance entre les variables, mais seulement un ordre de conditionnement.

Le conditionnement par le seul passé impose une contrainte de causalité aux architectures qui l'implémentent, d'où le recours aux [[Convolution causale|convolutions causales]].
