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
- Prendre sur le jeu de développement toutes les décisions : moment d'arrêt, choix du modèle, valeurs des hyper-paramètres.
- Sélectionner les hyper-paramètres donnant le meilleur risque empirique sur le jeu de développement, puis, facultativement, réestimer les paramètres du modèle sur l'ensemble complet des données pour ces hyper-paramètres optimaux.
- Ne toucher le jeu de test qu'une fois, à la fin, pour rapporter la performance.
- Comparer le résultat à une référence (*baseline*), toujours.

# Remarque

- L'erreur d'entraînement décroît toujours : elle ne dit rien de la qualité du modèle.
- Une erreur de développement qui remonte signale le [[Surapprentissage et sous-apprentissage|surapprentissage]] : c'est le détecteur de ce mode de défaillance.
- Régler sur le jeu de test revient à rapporter un score qu'on ne mérite plus.
- Le risque mesuré sur l'ensemble de validation est un très mauvais estimateur du risque : cet ensemble sert à sélectionner, pas à estimer la performance.
- Le découpage en ensembles séparés est le principe de la [[Méthode de validation]] et de l'[[Estimation non biaisée du risque]] ; la [[Validation croisée|validation croisée]] généralise ce découpage.

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

`Dataset` indique comment obtenir un échantillon, `random_split` découpe entraînement, validation et test, `DataLoader` fournit des mini-lots mélangés.

```python
from torch.utils.data import Dataset, DataLoader
from torch.utils.data import random_split

class PopulationDataset(Dataset):
    def __init__(self, x, y):      # tenseurs
        self.x, self.y = x, y
    def __len__(self):
        return len(self.x)
    def __getitem__(self, i):
        return self.x[i], self.y[i]

ds = PopulationDataset(x, y)
train, valid, test = random_split(ds, [0.7, 0.1, 0.2])
loader = DataLoader(train, batch_size=32, shuffle=True)
for x_batch, y_batch in loader:
    ...
```
