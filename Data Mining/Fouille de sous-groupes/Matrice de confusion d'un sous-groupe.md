#dmv-subgroup_discovery

# Définition

Pour une cible binaire, la **matrice de confusion d'un sous-groupe** croise l'appartenance au sous-groupe (sa description, vraie ou fausse) avec la valeur de la cible (vraie ou fausse) :

| Sous-groupe | Cible vraie | Cible fausse |
| :--- | :--- | :--- |
| Vrai | $a$ | $b$ |
| Faux | $c$ | $d$ |

Les quatre cellules comptent les individus correspondants :

- $a$ : individus couverts par le sous-groupe dont la cible est vraie ;
- $b$ : individus couverts par le sous-groupe dont la cible est fausse ;
- $c$ : individus hors du sous-groupe dont la cible est vraie ;
- $d$ : individus hors du sous-groupe dont la cible est fausse.

L'étendue (*extent*) du sous-groupe et la taille de la population totale se lisent sur ces cellules :

$$n = a + b$$

$$N = a + b + c + d$$

# Interprétation

La matrice rassemble en quatre nombres ce qu'exploitent la plupart des [[Fonction de qualité d'un sous-groupe|fonctions de qualité]] pour cible binaire : la taille du sous-groupe, la proportion de cible vraie qu'il contient et la proportion de cible vraie dans toute la population.

Deux taux s'en déduisent directement et se comparent :

- le taux de présence de la cible dans le sous-groupe, $t_P = \dfrac{a}{n}$ ;
- le taux de présence de la cible dans toute la population, $t_{all} = \dfrac{a + c}{N}$.

Un sous-groupe intéressant est celui dont le premier taux s'écarte du second, c'est-à-dire celui qui capte une population où la cible est surreprésentée. Le facteur de couverture $n/N$ pondère cet écart par la part de la population que le sous-groupe concerne : un écart fort sur un sous-groupe minuscule pèse moins qu'un écart modéré sur un sous-groupe large. C'est exactement le compromis que chiffre l'[[Exactitude relative pondérée]].

# Remarque

Les cellules de la matrice portent le même comptage que celles d'une [[Règle d'association et confiance|règle d'association]] dont l'antécédent décrit le sous-groupe et dont le conséquent est la cible vraie : $a$ est le nombre d'individus couverts par la règle, $n = a + b$ la couverture de l'antécédent et $a/n$ la confiance de la règle. La matrice de confusion ajoute au comptage la distinction entre les individus hors du sous-groupe, qui permet de situer le sous-groupe par rapport à la population entière et non seulement par rapport à lui-même.

La table est celle de la [[Matrice de confusion et exactitude|matrice de confusion d'un classifieur]], mais ses deux axes y opposent l'appartenance au sous-groupe et la valeur de la cible, là où ceux d'un classifieur opposent la classe réelle (en lignes) et la classe prédite (en colonnes). Un sous-groupe ne se règle pas par un seuil : sa description est vraie ou fausse pour chaque individu, si bien que les désaccords avec la cible se lisent en $b$ (cible fausse chez les individus couverts) et en $c$ (cible vraie chez les individus non couverts).
