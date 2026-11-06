# Algorithme

Un test d'hypothèse se conduit en sept étapes :

1. définir l'[[Hypothèse nulle et hypothèse alternative|hypothèse nulle]] $H_0$ et l'hypothèse alternative $H_1$ ;
2. déterminer les variables sur lesquelles porte la décision ;
3. déterminer la forme de la région critique d'après $H_1$ ;
4. calculer la région critique pour un seuil $\alpha$ donné ;
5. calculer éventuellement la puissance du test ;
6. calculer la valeur expérimentale de la variable de décision ;
7. accepter ou rejeter $H_0$.

# Interprétation

Les deux premières étapes fixent la question et l'instrument de mesure : $H_0$ est l'hypothèse que l'on cherche à trancher, $H_1$ en est la contradiction, et la variable de décision est la [[Statistique de test|statistique de test]], dont la loi sous $H_0$ doit être connue pour que la décision soit calculable.

Les étapes 3 et 4 construisent la [[Zone critique et seuil d'un test|zone critique]]. L'étape 3 en donne la forme, unilatérale ou bilatérale, qui se déduit de l'orientation de $H_1$ ; l'étape 4 en fixe la frontière numérique à partir du seuil $\alpha$, c'est-à-dire du [[Risque de première espèce|risque de première espèce]] accepté.

L'étape 5 est facultative : elle évalue la [[Puissance d'un test|puissance]] du test, c'est-à-dire sa capacité à rejeter $H_0$ lorsque $H_1$ est vraie. Les étapes 6 et 7 confrontent enfin la valeur observée de la statistique à la région critique : on rejette $H_0$ lorsque cette valeur appartient à la région critique, on la conserve sinon.

# Remarque

L'ordre des étapes n'est pas indifférent. Les étapes 1 à 5 se règlent avant de calculer la valeur expérimentale de l'étape 6 : choisir la forme de la région critique ou le seuil $\alpha$ après avoir vu les données retire toute garantie sur le risque de première espèce réellement encouru.

La forme de la région critique (étape 3) se déduit uniquement de $H_1$ ; le seuil $\alpha$ (étape 4) ne fait que translater la frontière de cette région. Une région critique de forme correcte mais de seuil mal choisi reste donc une région critique de la bonne forme, avec un autre niveau.
