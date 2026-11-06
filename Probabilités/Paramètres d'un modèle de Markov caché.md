# Modèle

Un [[Modèle de Markov caché|modèle de Markov caché]] se note $\lambda_N$, où $N$ est le nombre d'états cachés.

Il porte sur deux séquences de même longueur $T$ :

- la séquence d'états cachés $S = s_1, \ldots, s_T$, où chaque $s_t$ est l'un des $N$ états ;
- la séquence d'observations $O = o_1, \ldots, o_T$.

Ses paramètres se répartissent en trois groupes.

- Les **probabilités initiales** $\pi$ donnent la loi du premier état, notée $\pi_{s_1}$ dans la loi d'une séquence d'états :
$$\pi_i = \mathbb{P}[s_1 = i]$$
- La **matrice de transition** $A = (a_{ij})$ donne les probabilités de passage d'un état à l'état suivant :
$$a_{ij} = \mathbb{P}[s_t = j \mid s_{t-1} = i]$$
- Les **probabilités d'observation** $B = (b_i)$ donnent la loi de l'observation sachant l'état qui l'émet :
$$b_i(o_t) = \mathbb{P}[o_t \mid s_t = i]$$

Le modèle se résume ainsi au triplet $\lambda_N = (\pi, A, B)$.

La forme de $B$ dépend de la nature des observations :

- **modèle de Markov caché discret** : $B$ est une matrice de probabilités conditionnelles, où $b_{ik} = \mathbb{P}[O_t = k \mid S_t = i]$ ;
- **modèle de Markov caché à densités continues** : $B$ est un ensemble de densités paramétriques conditionnelles $b_i()$ ; en pratique, $b_i()$ est souvent un [[Mélange gaussien|mélange gaussien]].

# Propriétés

Les trois groupes sont constitués de probabilités, dont les masses se somment à un.

- Les probabilités initiales :
$$\sum_{i=1}^{N} \pi_i = 1$$
- Chaque ligne de la matrice de transition, qui est une loi sur l'état suivant :
$$\sum_{j=1}^{N} a_{ij} = 1$$
- Chaque loi d'observation $b_i$ est une loi de probabilité sur les observations possibles.

# Remarque

- Les paramètres ne dépendent pas de l'indice de temps : la même matrice $A$ et les mêmes lois d'observation $b_i$ valent à chaque instant $t$ (modèle homogène).
- L'état caché suit une [[Chaîne de Markov à temps discret|chaîne de Markov à temps discret]] de distribution initiale $\pi$ et de matrice de transition $A$ ; les observations s'y greffent par les lois d'émission $b_i$, chacune ne dépendant que de l'état courant. La loi jointe des états et des observations s'exprime à partir de ces paramètres, voir [[Probabilités d'un modèle de Markov caché]], et la [[Génération d'un modèle de Markov caché|génération d'un modèle de Markov caché]] décrit la simulation conjointe des deux séquences.
- Un modèle $\lambda_N$ est la donnée de départ des [[Trois problèmes d'un modèle de Markov caché|trois problèmes d'un modèle de Markov caché]] : décodage de la séquence d'états la plus probable, évaluation de la probabilité d'une séquence d'observations et estimation des paramètres. Les paramètres s'estiment par [[Méthode du maximum de vraisemblance|maximum de vraisemblance]] ; les formules empiriques de l'[[Estimation empirique des paramètres d'un modèle de Markov caché|estimation empirique des paramètres]] supposent connues les séquences d'états cachés.
- Un modèle entièrement chiffré, avec ses matrices $A$, $B$ et $\pi$ et le calcul des quantités qui s'en déduisent, se trouve dans l'[[Algorithme forward]] : l'exemple à trois états y sert de support au calcul des probabilités forward.
- Chacun de ces paramètres est un facteur de la loi jointe : $\pi$ en porte le premier terme, $A$ les transitions et les $b_i$ les émissions, comme le détaille [[Probabilités d'un modèle de Markov caché]].
