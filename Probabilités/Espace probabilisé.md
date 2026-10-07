# Définition

Dans un espace probabilisé, à chaque [[Évènement|événement]] est associé un nombre de $[0,1]$, sa probabilité, qui satisfait les axiomes de Kolmogorov :

- $\mathbb{P}[\Omega] = 1$ ;
- tout ensemble fini d'événements incompatibles $E_i$ vérifie $\mathbb{P}[\bigcup_i E_i] = \sum \mathbb{P}[E_i]$.

# Propriétés

Les conséquences des axiomes sont :

- $\mathbb{P}[\emptyset] = 0$ ;
- $\mathbb{P}[A \cup B] = \mathbb{P}[A] + \mathbb{P}[B] - \mathbb{P}[A \cap B]$ ;
- $\mathbb{P}[\overline{E}] = 1 - \mathbb{P}[E]$ ;
- $\mathbb{P}[\bigcup_i A_i] \leq \sum \mathbb{P}[A_i]$ ;
- $\mathbb{P}[A] \leq \mathbb{P}[B]$ si $A \subset B$ ;
- $\lim_{A_i \to 0} \mathbb{P}[A_i] = 0$.

# Remarque

$\mathbb{P}[A] = 0$ (resp. $\mathbb{P}[A] = 1$) n'implique pas que $A$ ne se produise jamais (resp. qu'il se produise toujours).

# Exemple

Une cellule sans fil dispose de $5$ canaux, chacun dans l'un de deux états : occupé ($0$) ou disponible ($1$). On cherche la probabilité qu'une conférence téléphonique ne soit pas bloquée ($X = 1$), sachant qu'au moins $3$ canaux sont requis.

1. **Espace d'échantillonnage** : les $5$-uplets de $0$ et de $1$.
2. **Probabilités** : on suppose que chaque événement est équiprobable : voir [[Probabilité discrète]].
3. **Événement d'intérêt $E$** : « au moins trois canaux sont disponibles », représenté par l'ensemble des $5$-uplets ayant au moins trois $1$ ($16/32$).
4. **Calcul de la probabilité cherchée** : $E$ est une union d'[[Évènement|événements élémentaires]] mutuellement exclusifs $E_i$ de probabilité $1/32$ chacun, d'où

   $$\mathbb{P}[X = 1] = \sum_i \mathbb{P}[E_i] = \sum_i \frac{1}{32} = \frac{16}{32}.$$
