#dmv-pattern_mining_with_information_theory
# Définition

Une base de séquences $D$ encodée avec une [[Table de codes pour séquences d'événements|table de codes de séquences]] $CT$ se lit en deux flux : le flux de motifs $C_p$ et le flux de trous $C_g$. Sa longueur de description au regard de la table est la somme de ces deux flux, augmentée de la description de la segmentation.

Longueur du flux de motifs :

$$L(C_p \mid CT) = \sum_{X \in CT} usage(X) L(code_p(X))$$

Longueur du flux de trous, restreinte aux motifs de taille supérieure à un :

$$L(C_g \mid CT) = \sum_{\substack{X \in CT \\ |X| > 1}} \left( gaps(X) L(code_g(X)) + fills(X) L(code_n(X)) \right)$$

Longueur totale de la base :

$$L(D \mid CT) = L_N(|D|) + \sum_{S \in D} L_N(|S|) + L(C_p \mid CT) + L(C_g \mid CT)$$

# Interprétation

Les deux premiers termes décrivent la structure de la base avant tout contenu : le nombre de séquences de $D$ et la longueur de chaque séquence $S$ de $D$. Sans eux, le décodeur ne saurait pas où commence et où s'arrête chaque séquence du texte reconstruit.

Les deux termes suivants viennent des [[Longueur des codes de motifs et de trous|longueurs des codes de motifs, de trous et de non-trous]], chacune pondérée par le nombre d'emplois du code :

- $L(C_p \mid CT)$ somme les longueurs des codes de motif, une fois par emploi ;
- $L(C_g \mid CT)$ somme les longueurs des codes de trou et de non-trou, une fois par lien interne à un emploi.

La restriction $|X| > 1$ du flux de trous est cohérente avec la forme des liens : un motif d'un seul événement n'a aucune position interne, donc rien à coder dans $C_g$.

Comme la [[Longueur de description d'une base encodée]] pour les itemsets, $L(D \mid CT)$ est le terme de données de l'objectif MDL. Son terme de modèle est la [[Longueur de description d'une table de codes de séquences]], et la somme des deux est la [[Taille totale d'un modèle et des données encodées]] que la recherche du meilleur modèle minimise.

# Remarque

$L_N$ désigne la longueur du code d'un entier sous un code des entiers naturels ; c'est lui qui chiffre le nombre de séquences de la base et la longueur de chaque séquence.

Décoder la base suppose donc de disposer des deux flux et de la segmentation : l'alignement du flux de motifs sur la séquence d'événements, trou par trou, reconstruit la base, mais les frontières entre séquences ne se lisent que dans les deux premiers termes.
