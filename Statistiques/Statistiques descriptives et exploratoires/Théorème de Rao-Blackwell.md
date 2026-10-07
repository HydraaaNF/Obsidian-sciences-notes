# Théorème 1

**Théorème de Rao-Blackwell.** Si $T$ est un [[Estimateur|estimateur]] [[Biais d'un estimateur|sans biais]] de $\theta$ et $U$ une [[Statistique suffisante|statistique suffisante]] pour $\theta$, alors $T^* = \mathbb{E}[T \mid U]$ est un estimateur sans biais de $\theta$, au moins aussi bon que $T$.

# Théorème 2

S'il existe une statistique suffisante $U$ pour $\theta$, alors l'unique [[Estimateur sans biais de variance minimale|estimateur sans biais de variance minimale]] $T$ de $\theta$ ne dépend que de $U$.

# Interprétation

L'estimateur $T^* = \mathbb{E}[T \mid U]$ est l'espérance conditionnelle de $T$ sachant $U$ : il ne dépend que de la statistique suffisante $U$. Le théorème de Rao-Blackwell énonce que ce conditionnement ne dégrade jamais l'estimation : le caractère sans biais est conservé et le [[Risque généralisé|risque]] n'augmente pas. « Au moins aussi bon » s'entend au sens de la [[Comparaison d'estimateurs|comparaison des estimateurs]] sur la base de leur risque :

$$R(T^*, \theta) \le R(T, \theta) \quad \text{pour tout } \theta.$$

Puisque $T^*$ et $T$ sont tous deux sans biais, cette comparaison revient à comparer leurs variances : $\mathbb{V}[T^*] \le \mathbb{V}[T]$.

Le second théorème en tire la conséquence pratique : dès qu'une statistique suffisante $U$ existe, la recherche d'un estimateur sans biais de variance minimale peut être restreinte aux estimateurs qui ne dépendent que de $U$.

# Remarque

- Partant d'un estimateur sans biais $T$ quelconque, le conditionnement par une statistique suffisante fournit donc un estimateur sans biais dont le risque ne dépasse pas celui de $T$ : c'est une méthode générale d'amélioration d'un estimateur.
- Le [[Théorème de Lehmann-Scheffé]] complète ces résultats : il précise quand $T^* = \mathbb{E}[T \mid U]$ est l'unique estimateur sans biais de variance minimale.
