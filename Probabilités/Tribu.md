# Définition

Les [[Évènement|évènements]] d'une expérience aléatoire forment un ensemble de parties de $\Omega$ ayant une structure de **tribu** (ou **$\sigma$-algèbre**) : il doit contenir $\Omega$ et $\emptyset$, être stable par passage au complémentaire et stable par union et intersection dénombrables.

Formellement, soit $\Omega$ un ensemble non vide. On dit que $\mathcal{F} \subset \mathcal{P}(\Omega)$ est une **tribu de parties de $\Omega$** si :

- $\Omega \in \mathcal{F}$ ;
- $A \in \mathcal{F} \implies \overline{A} \in \mathcal{F}$ ;
- $((\forall n \in \mathbb{N}) (A_n \in \mathcal{F})) \implies \bigcup_{n \in \mathbb{N}} A_n \in \mathcal{F}$.

# Propriétés

En réalité, il suffit d'exiger qu'une tribu contienne $\Omega$, soit stable par passage au complémentaire et stable par union dénombrable. En effet, elle contient alors automatiquement $\emptyset = \overline{\Omega}$, et elle est également stable par intersection dénombrable en vertu de la formule de De Morgan :

$$\bigcap_{n \in \mathbb{N}} A_n = \overline{\bigcup_{n \in \mathbb{N}} \overline{A_n}}$$

Dans un contexte probabiliste où $\Omega$ ne contient qu'un nombre fini d'éléments, ou lorsque $\Omega$ est *dénombrable*, on prend toujours $\mathcal{F} = \mathcal{P}(\Omega)$ comme ensemble des évènements : toute partie de $\Omega$ est alors un évènement. Un ensemble $\Omega$ est dit dénombrable lorsqu'il existe une bijection $f : \mathbb{N} \to \Omega$, ce qui signifie que l'on peut numéroter ses éléments.

### Démonstration

Dans toute modélisation probabiliste, les ensembles réduits à une éventualité (les singletons $\{\omega\}$ pour $\omega \in \Omega$, appelés évènements élémentaires) sont des évènements. Or, dire que $\Omega$ est fini ou dénombrable signifie qu'il existe un ensemble d'indices $I \subset \mathbb{N}$ tel que $\Omega = \{\omega_n \mid n \in I\}$. Tout $A \subset \Omega$ s'écrit alors comme une union dénombrable d'évènements élémentaires :

$$A = \{\omega_n \mid n \in J\} = \bigcup_{n \in J} \{\omega_n\}$$

où $J \subset I \subset \mathbb{N}$. D'après l'axiome de stabilité par union dénombrable, puisque $\{\omega_n\} \in \mathcal{F}$ pour tout $n \in J$, on a $A \in \mathcal{F}$ : $A$ est bien un évènement. Autrement dit, l'ensemble des évènements est dans ce cas la tribu $\mathcal{P}(\Omega)$ en entier.

Si $\Omega$ contient au moins deux éléments, il existe un sous-ensemble $A$ de $\Omega$ distinct de $\Omega$ et de $\emptyset$, et l'on vérifie immédiatement que $\{\emptyset, A, \overline{A}, \Omega\}$ est une tribu de parties de $\Omega$. C'est la plus petite tribu de parties de $\Omega$ contenant $A$ : on dit que c'est la **tribu engendrée par $A$**. Plus généralement, la plus petite tribu sur $\mathbb{R}^+$ contenant les intervalles inclus dans $\mathbb{R}^+$ est la tribu engendrée par les intervalles de $\mathbb{R}^+$ : c'est la [[Tribu borélienne]] de $\mathbb{R}^+$.

# Exemple

### Plus grande et plus petite tribus

- Toute tribu $\mathcal{F}$ de parties de $\Omega$ vérifie bien sûr $\mathcal{F} \subset \mathcal{P}(\Omega)$ : $\mathcal{P}(\Omega)$ est la plus grosse tribu de parties de $\Omega$.
- La plus petite tribu de parties de $\Omega$ est $\{\emptyset, \Omega\}$. Elle ne présente aucun intérêt pour faire des probabilités puisqu'elle ne contient que l'évènement impossible et l'évènement certain.

### Jeter une pièce

Quelle est la tribu associée à l'expérience aléatoire consistant à jeter une seule pièce ? On a ici tout simplement $\Omega = \{p, f\}$. Comme tribu, on n'a pas le choix si l'on veut n'oublier aucun évènement : on prend

$$\mathcal{F} = \mathcal{P}(\Omega) = \{\emptyset, \{p\}, \{f\}, \{p, f\}\}$$

# Remarque

C'est sur la tribu des évènements que se définit une probabilité : voir [[Espace probabilisé]].
