# Modèle

On considère une séquence d'observations $x = (x_1, \dots, x_n)$ et la séquence d'étiquettes $y = (y_1, \dots, y_n)$ qui lui est associée. Les [[Fonctions de traits pour les séquences|fonctions de traits]] d'un modèle séquentiel sont des fonctions $f_i : X \times Y \to \mathbb{R}$, ou à valeurs dans $\{0, 1\}$. On suppose, sans perte de généralité, que chacune d'elles se décompose en une somme de contributions locales, une par position :

$$f_i(x, y) = \sum_{s=1}^{n} f_i(y_{s-1}, y_s, x, s)$$

et ce pour tout $i \in \{1, \dots, m\}$.

Le terme local $f_i(y_{s-1}, y_s, x, s)$ ne voit que trois choses : le couple d'étiquettes consécutives des positions $s-1$ et $s$, dont l'une des deux peut être ignorée, l'observation $x$ dans son ensemble, et l'indice $s$ qui repère la position. La même lettre $f_i$ désigne la fonction globale et son terme local, les arguments départageant les deux écritures.

# Propriétés

Les conséquences de cette écriture se lisent sur les arguments du terme local :

- la dépendance aux étiquettes est locale : un terme local ne fait intervenir **au plus deux étiquettes voisines**, $y_{s-1}$ et $y_s$, et il peut n'en utiliser qu'une seule, par exemple avec le trait $\mathbb{1}[y_s = \text{NOUN}]$ lorsque $x_s$ est un mot capitalisé ; la fonction de traits globale ne dépend donc jamais d'un groupe d'étiquettes éloignées de la position courante ;
- la dépendance à l'observation n'est pas restreinte : $x$ est un argument libre du terme local, qui peut porter aussi bien sur un unique $x_s$ que sur la séquence entière ;
- la position $s$ est un argument à part entière : une même fonction de traits peut donc se comporter différemment au début, au milieu ou à la fin de la séquence.

# Interprétation

Une fonction de traits décomposée s'interprète comme un score accumulé le long de la séquence : chaque position apporte sa contribution locale, et la fonction globale en fait la somme. Lorsque le terme local est une indicatrice, cette somme compte simplement le nombre de positions où le motif est réalisé : un motif repéré à quatre endroits donne $f_i(x, y) = 4$, un motif absent donne $f_i(x, y) = 0$.

Le trait décrit ainsi un motif local, et sa valeur globale mesure à quel point la séquence observée, étiquetée par $y$, réalise ce motif. Deux séquences de longueurs différentes restent décrites par le même motif, seule la valeur totale change.

# Remarque

Ne dépendre que d'au plus deux étiquettes voisines, et non de $y$ globalement, est l'analogue, pour un champ conditionnel, de la [[Propriété de Markov]] dans un [[Modèle de Markov caché]] : dans les deux cas, l'information pertinente pour une position se limite à son voisinage immédiat, ce qui autorise un traitement position par position. La restriction ne porte que sur les étiquettes : l'observation, elle, reste accessible globalement par l'intermédiaire du terme local.

L'indice $s$ partant de $1$, le premier terme local fait intervenir une étiquette $y_0$ : les positions de bord se traitent au moyen d'étiquettes fictives, décrites dans [[Étiquetage morphosyntaxique par fonctions de traits]].

Cette forme est celle que retient le [[Champ aléatoire conditionnel à chaîne linéaire]] pour l'ensemble de ses fonctions de traits, la loi conditionnelle y étant écrite directement avec les $f_i$ décomposées. C'est elle qui donne au décodage sa structure de chaîne, exploitée par le [[Décodage d'un champ aléatoire conditionnel à chaîne linéaire]] et par la [[Programmation dynamique pour un champ aléatoire conditionnel]].
