#ml-1

# Définition

Les modèles d'apprentissage ajustent des fonctions réelles de variables réelles. Une [[Donnée et attributs|donnée]] dont un attribut prend des valeurs symboliques (un cercle, une croix, un carré, un triangle) doit donc être convertie en nombres avant de servir d'entrée : c'est l'encodage des valeurs symboliques.

Un encodage associe à chaque valeur d'un alphabet fini un code numérique, de longueur fixe ou variable selon l'encodage, rangé dans un [[Tenseur|tenseur]]. Plusieurs encodages sont possibles pour un même alphabet ; ils diffèrent par le nombre d'entrées consommées et par la structure qu'ils imposent aux codes.

# Exemple

Alphabet de taille 4 : {cercle, croix, carré, triangle}.

| Encodage | Entrées | Codes |
| --- | --- | --- |
| « 1 parmi K », one-hot | 4 | 1000, 0100, 0010, 0001 |
| Encodage à base fixe | 2 | 11, 01, 00, 10 |
| Codage entropique (codage de source) | 1 à 3 | 000, 01, 1, 001 |
| Expertise ordinale (cold, mild, hot) | 1 | 0, 1, 2 |

- Le one-hot alloue une entrée par valeur de l'alphabet : un seul bit vaut 1, les autres valent 0.
- L'encodage à base fixe écrit le code de chaque valeur dans une base fixée, sur un nombre d'entrées constant.
- Le codage entropique compresse : les symboles fréquents reçoivent les codes courts, les rares les codes longs. Sur cet alphabet, il ne consomme donc qu'entre 1 et 3 entrées.
- L'encodage par expertise attribue directement un entier ordonné à chaque valeur.

En pratique, `pandas` produit le code « 1 parmi K » sans l'écrire à la main : `pd.get_dummies` crée une colonne par valeur.

```python
import pandas as pd

df = pd.DataFrame({"animal": ["cat", "dog", "cat"]})
pd.get_dummies(df[["animal"]], dtype=float)
#   animal_cat  animal_dog
# 0        1.0         0.0
# 1        0.0         1.0
# 2        1.0         0.0
```

- Deux valeurs seulement : une seule colonne suffit.
- Sans `dtype=float`, les versions récentes de `pandas` renvoient des booléens.

# Remarque

Parmi ces encodages, seul l'encodage par expertise injecte un ordre : ses codes numériques classent les valeurs les unes par rapport aux autres. Le one-hot est au contraire le cas sans ordre du codage d'une valeur symbolique : aucune valeur n'y est privilégiée par son code, ce dont tire parti la [[Couche de plongement]].

- L'[[Hypothèse distributionnelle]] motive le passage du one-hot, où toutes les valeurs sont équidistantes, à des vecteurs de mots qui rapprochent les contextes semblables.
