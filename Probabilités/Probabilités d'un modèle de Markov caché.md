# Loi

Un [[Modèle de Markov caché|modèle de Markov caché]] fait vivre deux séquences sur les mêmes instants $t = 1, \dots, T$ : les états cachés $S = s_1, \dots, s_T$ et les observations $O = o_1, \dots, o_T$. La loi qui régit l'ensemble du modèle est la loi jointe du couple, et elle se factorise en la loi des états et en la loi des observations sachant les états :

$$\mathbb{P}[O = o_1, \dots, o_T, S = s_1, \dots, s_T] = \mathbb{P}[O \mid S] \, \mathbb{P}[S]$$

Le facteur $\mathbb{P}[S]$ est la probabilité de la suite d'états, le facteur $\mathbb{P}[O \mid S]$ la probabilité des observations une fois cette suite connue. Chacun se calcule à partir d'une seule hypothèse du modèle, ce qui rend la loi jointe entièrement calculable.

# Propriétés

La suite des états est une [[Chaîne de Markov à temps discret|chaîne de Markov]] d'ordre 1 : chaque état ne dépend que de l'état précédent, et le premier état est régi par le seul terme $\pi_{s_1}$. La probabilité d'une suite d'états vaut donc

$$\mathbb{P}[S = s_1, \dots, s_T] = \pi_{s_1} \prod_{t=2}^{T} \mathbb{P}[s_t \mid s_{t-1}]$$

Le terme $\pi_{s_1}$ donne la probabilité de commencer en $s_1$, chaque facteur suivant une probabilité de transition de $s_{t-1}$ vers $s_t$.

Les observations sont conditionnellement [[Indépendance de variables aléatoires|indépendantes]] sachant les états : chacune ne dépend que de l'état de sa propre date, si bien que la probabilité conditionnelle de la séquence d'observations est le produit de ces dépendances locales :

$$\mathbb{P}[O = o_1, \dots, o_T \mid S = s_1, \dots, s_T] = \prod_{t=1}^{T} \mathbb{P}[o_t \mid s_t]$$

En reportant ces deux expressions dans la loi jointe, on obtient la probabilité d'une histoire complète, états et observations :

$$\mathbb{P}[O = o_1, \dots, o_T, S = s_1, \dots, s_T] = \pi_{s_1} \prod_{t=2}^{T} \mathbb{P}[s_t \mid s_{t-1}] \prod_{t=1}^{T} \mathbb{P}[o_t \mid s_t]$$

# Interprétation

La factorisation reflète les deux niveaux du modèle. La loi jointe se lit comme un enchaînement génératif : un état initial de probabilité $\pi_{s_1}$, $T - 1$ transitions pour dérouler la suite des états, puis un tirage d'observation par état atteint. Sa valeur est la vraisemblance d'une trajectoire complète, celle d'un couple (états, observations) donné, et non celle des seules observations.

Chacune des deux hypothèses fournit un seul des deux facteurs : la suite des états cachés évolue selon une chaîne de Markov, dont la probabilité est celle de son état initial multipliée par les probabilités de transition successives, tandis que chaque observation $o_t$ ne dépend que de l'état $s_t$ au même instant.

# Remarque

La notation $O = o_1, \dots, o_T$ désigne la séquence entière, la lettre nue $O$ renvoyant à la suite et chaque $o_t$ à la valeur prise à l'instant $t$ ; de même pour $S$ et $s_t$. L'écriture $O = o_1, \dots, T$, où la virgule est suivie directement de $T$, omet l'indice final de $o$ : la séquence s'arrête à $o_T$, d'où la forme $O = o_1, \dots, o_T$ employée dans les formules ci-dessus.

Les deux indices d'une probabilité conditionnelle se lisent à la date qu'ils portent : $\mathbb{P}[o_t \mid s_t]$ compare l'observation et l'état du même instant $t$, tandis que $\mathbb{P}[s_t \mid s_{t-1}]$ relie deux instants consécutifs.

Le produit sur les états part de $t = 2$ parce que le cas $t = 1$ est déjà couvert par $\pi_{s_1}$ ; le produit sur les observations part de $t = 1$ parce que chaque instant émet une observation, y compris le premier.

Aucune constante de normalisation n'apparaît : le produit $\mathbb{P}[O \mid S] \, \mathbb{P}[S]$ est déjà une loi sur le couple des deux séquences.

Les facteurs $\pi_{s_1}$, $\mathbb{P}[s_t \mid s_{t-1}]$ et $\mathbb{P}[o_t \mid s_t]$ sont exactement les [[Paramètres d'un modèle de Markov caché|paramètres du modèle]]. La loi marginale des observations s'obtient en sommant la loi jointe sur toutes les suites d'états possibles, somme qui définit le problème d'évaluation parmi les [[Trois problèmes d'un modèle de Markov caché|trois problèmes d'un modèle de Markov caché]].
