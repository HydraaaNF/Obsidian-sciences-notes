#ml-1

# Définition

Le **protocole** de découpage répartit les données en trois jeux aux rôles disjoints.

Le **jeu d'entraînement** (*train*) est celui sur lequel le modèle ajuste ses paramètres.

Le **jeu de développement** (*dev*, ou de validation) est celui sur lequel sont prises toutes les décisions qui nous reviennent : moment d'arrêt de l'apprentissage, choix du modèle, valeurs des [[Hyper-paramètres|hyper-paramètres]].

Le **jeu de test** est touché une seule fois, pour rapporter la performance finale.

Si l'objectif est à la fois d'obtenir le meilleur modèle et d'estimer sa performance espérée, trois ensembles de données sont nécessaires.

# Algorithme

- Découper les données en trois jeux.
- Ajuster les paramètres du modèle sur le jeu d'entraînement.
- Sélectionner les hyper-paramètres donnant le meilleur risque empirique sur le jeu de développement, puis, facultativement, réestimer les paramètres du modèle sur l'ensemble complet des données pour ces hyper-paramètres optimaux.
- Ne toucher le jeu de test qu'une fois, à la fin, pour rapporter la performance.
- Comparer le résultat à une référence (*baseline*), toujours.

# Remarque

- L'erreur d'entraînement décroît toujours : elle ne dit rien de la qualité du modèle.
- Une erreur de développement qui remonte signale le [[Surapprentissage et sous-apprentissage|surapprentissage]] : c'est le détecteur de ce mode de défaillance.
- Régler sur le jeu de test revient à rapporter un score qu'on ne mérite plus.
- Le risque mesuré sur l'ensemble de validation est un très mauvais estimateur du risque : cet ensemble sert à sélectionner, pas à estimer la performance.
- Le taux d'apprentissage de la [[Descente de gradient]] se règle sur le jeu de développement, jamais sur le jeu de test.

# Exemple

**Avec scikit-learn**

`train_test_split` mélange les données, puis coupe `x` et `y` de façon cohérente ; les tenseurs entrent, les tenseurs sortent.

- `random_state` fixe le même découpage à chaque exécution, de sorte que les expériences restent comparables ;
- `stratify=y` conserve les mêmes proportions de classes dans les deux ensembles.

```python
from sklearn.model_selection import train_test_split

x_train, x_test, y_train, y_test = train_test_split(
    x, y, test_size=0.2, random_state=0, stratify=y)
```

Le jeu de test est alors mis de côté et n'est plus regardé avant la toute fin.

**Avec PyTorch**

Le chargement PyTorch est décrit dans [[Lots, époques et chargement des données]].
