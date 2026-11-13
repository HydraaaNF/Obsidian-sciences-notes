#dmv-sequence_mining

# Définition

La **pseudo-projection** est la représentation compacte d'une [[Base projetée|base projetée]] : au lieu de copier la [[Base de séquences|base de séquences]] à chaque étape de la fouille, on conserve pour chaque projection un pointeur vers la séquence d'origine et un offset qui repère le début du suffixe restant.

Une projection se résume donc à un couple pointeur-offset, et le suffixe se lit directement dans la séquence pointée.

# Exemple

Pour la séquence $s$ d'une base :

$$s = \langle a(abc)(ac)d(cf)\rangle$$

La projection sur le préfixe $\langle a\rangle$ garde un pointeur vers $s$ et l'offset $2$ ; le premier emplacement du couple, celui du pointeur, reste vide :

$$s|_{\langle a\rangle} : (\ , 2)$$

Le suffixe se lit alors à partir de là, sans copie :

$$\langle(abc)(ac)d(cf)\rangle$$

La projection sur le préfixe $\langle ab\rangle$ garde le même pointeur et avance l'offset à $4$ :

$$s|_{\langle ab\rangle} : (\ , 4)$$

Le suffixe correspondant est :

$$\langle(\_c)(ac)d(cf)\rangle$$

L'offset avance dans la séquence à mesure que le préfixe s'allonge. Lorsqu'il s'arrête à l'intérieur d'un itemset, celui-ci n'est pas recopié : la partie déjà consommée par le préfixe y est remplacée par $\_$, seul l'item restant $c$ demeurant.

# Remarque

La pseudo-projection est la forme sous laquelle l'[[Algorithme PrefixSpan]] matérialise la base projetée : à chaque étape de cette construction, un pointeur vers la séquence et un offset tiennent lieu de la copie de la séquence, ce qui supprime le coût de recopie. Cette amélioration allège l'étape la plus coûteuse de la fouille, la construction de la base projetée.

Le suffixe lu de cette façon n'est pas un [[Suffixe d'une séquence|suffixe]] au sens de la définition usuelle : dans un suffixe, l'itemset coupé ne garde que les items qui restent, alors que la projection y conserve la trace des items déjà consommés sous la marque $\_$, comme le montre $\langle(\_c)(ac)d(cf)\rangle$.

Comme le suffixe n'existe que par référence à la séquence d'origine, la lecture n'est valable que tant que cette séquence reste disponible et inchangée dans la base de séquences.
