# Définition

Les quantiles sont les bornes des intervalles qui divisent les données en parts égales. Selon le nombre de parts, ils portent des noms particuliers :

- la médiane, qui divise les données en 2 parts égales ;
- les quartiles $Q_1$, $Q_2$ et $Q_3$, qui divisent les données en 4 parts égales ;
- les déciles, qui divisent les données en 10 parts égales ;
- les percentiles, qui divisent les données en 100 parts égales.

Pour une série de 40 valeurs triées $x_1 \leq x_2 \leq \dots \leq x_{40}$, les quartiles occupent les positions suivantes :

$$x_1 \leq \dots \leq \underbrace{x_{10}}_{Q_1} \leq x_{11} \leq \dots \leq \underbrace{x_{20}}_{Q_2} \leq x_{21} \leq \dots \leq \underbrace{x_{30}}_{Q_3} \leq x_{31} \leq \dots \leq x_{40}$$

Le deuxième quartile $Q_2$ correspond à la médiane (voir [[Moyenne, médiane et mode]]).

L'écart interquartile, noté IQR, est la différence entre le troisième et le premier quartile :

$$IQR = Q_3 - Q_1$$

# Interprétation

L'écart interquartile mesure la dispersion de la moitié centrale des données : $Q_1$ et $Q_3$ encadrent les 50 % centraux de la série. Il complète d'autres indicateurs de dispersion, comme l'[[Étendue]]. Les quartiles $Q_1$ et $Q_3$, ainsi que l'écart interquartile, servent également de base à la [[Boîte à moustaches]].
