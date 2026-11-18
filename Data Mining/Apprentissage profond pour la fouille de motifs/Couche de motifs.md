#dmv-pattern_mining_vs_deep_learning

# Modèle

La couche de motifs est la couche cachée d'un [[Auto-encodeur de motifs]] : chaque neurone qu'elle contient est destiné à porter un motif, et l'activation de ce neurone signale la présence du motif dans l'entrée.

La passe avant la traverse entre une entrée et une sortie de même largeur, avec une couche de motifs plus étroite : pour une entrée de $m = 5$ neurones, la couche en compte $k = 3$.

| Étage | Rôle |
|---|---|
| Entrée, 5 neurones | une transaction encodée en binaire, issue de [[Items, itemsets et base de transactions]] |
| Poids binaires $W_b^\top$ | connexions de l'entrée vers la couche de motifs |
| Couche de motifs, 3 neurones | un neurone par motif, chacun avec son biais $b$ |
| Miroir $W_b$ | les mêmes poids, relus dans l'autre sens |
| Sortie, 5 neurones | la transaction reconstruite |

L'entrée alimente la matrice de poids binaires $W_b^\top$ : c'est l'[[Encodage d'une transaction en motifs]].
Chaque neurone de la couche de motifs reçoit un biais $b$ et n'est actif que pour un seul motif.
Le miroir $W_b$ reconstruit le motif dans la couche de sortie, ce qui est le [[Décodage d'une couche de motifs]].

# Propriétés

Dans le schéma de la passe avant, l'activation d'un neurone de motif est une fonction échelon de seuil nul, appliquée à la pré-activation $z = c + b$, où $c$ est la somme pondérée reçue et $b$ le biais du neurone :

$$f(z) = \begin{cases} 1 & z \ge 0 \\ 0 & z < 0 \end{cases}$$

Le biais d'un neurone de motif est négatif et vaut moins la taille du motif :

$$b = -|P|$$

où $|P|$ est le nombre d'items du motif $P$ porté par le neurone.
Dans ce schéma, un neurone de motif n'est actif que si tous les items de son motif sont présents dans l'entrée.

# Remarque

Sur une entrée binaire et des poids binaires, la somme pondérée d'un neurone de motif compte les items du motif présents dans la transaction : elle vaut un entier $c$ entre $0$ et $|P|$. Le biais est ajouté à cette somme avant l'échelon, et l'activation vaut $1$ dès que la pré-activation $c + b$ atteint zéro ; avec $b = -|P|$, la condition $c + b \ge 0$ revient à $c \ge |P|$, de sorte que, dans ce schéma, le seuil effectif du neurone, mesuré sur le comptage des items, est la taille du motif. La même fonction s'écrit avec le seuil porté par le biais, $f(x) = 1$ si $x \ge b$ avec $b = -|P|$ ; cette forme ne rend pas ce critère. Appliquée à la pré-activation $x = c + b$, elle donne $c - |P| \ge -|P|$, soit $c \ge 0$, et activerait donc le neurone sur une transaction vide ; appliquée au comptage brut $x = c$, elle serait satisfaite pour tout $c \ge 0$ puisque $b < 0$. Dans ce schéma, le seuil se lit sur la pré-activation, à $0$, ou de façon équivalente sur le comptage, à $|P|$.

La passe avant ne laisse pas l'activation continue : elle la quantifie après un bornage dans l'intervalle unité, avec un biais discrétisé $b_d$ :

$$\lambda_E(z) = \operatorname{round}\left(\operatorname{clamp}\left(z + b_d\right)\right)$$

où $\operatorname{clamp}(x)$ vaut $0$ pour $x < 0$, $x$ pour $0 \le x \le 1$ et $1$ pour $x > 1$. Pour un comptage $c$ entier et un biais $b_d$ entier, la quantité $c + b_d$ est entière : si elle est négative ou nulle, le bornage vaut $0$ et l'arrondi $0$ ; dès qu'elle vaut au moins $1$, le bornage vaut $1$ et l'arrondi $1$. L'activation quantifiée vaut donc $1$ si et seulement si $c \ge 1 - b_d$, et le seuil effectif sur le comptage est $1 - b_d$, non $|b_d|$. Le détecteur exact du motif de taille $|P|$ demande ainsi $b_d = 1 - |P|$ ; transposé tel quel à cette quantification, le biais $b_d = -|P|$ du schéma n'active jamais le neurone, puisque $c \le |P| < |P| + 1$.

La règle « biais négatif égal à moins la taille du motif » est une règle de conception, pas une propriété des biais obtenus après apprentissage et discrétisation.
Sur une couche entraînée de quatre neurones, les biais discrétisés valent $[-1, -2, -1, -2]$, soit des seuils effectifs $[2, 3, 2, 3]$, alors que les motifs retenus sont de tailles 2, 4 et 3, pour lesquelles le détecteur exact demanderait $[-1, -3, -2]$ : les neurones de tailles 2 et 3 coïncident avec cette règle, leurs seuils valant 2 et 3 ; celui de taille 4 s'active dès 3 items présents sur 4 et reconstruit l'item manquant, et son seuil ne suit donc pas la taille du motif ; le troisième neurone, dont la ligne de poids est nulle, n'est rattaché à aucun motif et son seuil de 2 ne peut être atteint.
La règle décrit l'intention du seuil (n'activer que sur le motif complet), les valeurs numériques, elles, sortent de l'optimisation.

Un neurone de motif est un cas particulier de [[Neurone formel]] : entrées et poids binaires, somme pondérée comparée à un seuil, sortie binaire, avec ici une activation en échelon et un biais négatif qui porte le seuil.
