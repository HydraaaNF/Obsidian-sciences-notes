#ml-1

# Définition

Trois régimes de [[Descente de gradient|descente de gradient]] se distinguent par la quantité de données qui sert à chaque mise à jour :

- **lot complet** (batch) : la perte est calculée sur la totalité du jeu d'entraînement, puis les paramètres sont mis à jour une seule fois ; une mise à jour par passe sur les données ;
- **stochastique** : un échantillon par mise à jour, donc $N$ mises à jour par époque ; le gradient est très bruité ;
- **mini-lot** : $B$ échantillons par mise à jour, donc $N/B$ mises à jour par époque ; le gradient est estimé.

Une **époque** est une passe complète sur le jeu d'entraînement ; une **itération** est une mise à jour des paramètres.

# Interprétation

Sur un grand jeu de données, le lot complet coûte une passe entière par mise à jour et peut ne pas tenir en mémoire : plutôt que de calculer un gradient exact, on l'estime sur une partie des données.

Le mini-lot est le choix courant, avec $B$ de quelques dizaines à quelques centaines. Un mini-lot est une matrice : un seul produit matriciel calcule les sorties des $B$ échantillons à la fois, ce qui est rapide sur un GPU.

Le bruit du gradient estimé aide même l'optimisation : il fait sortir les paramètres des zones plates et des mauvais minima.

# Algorithme

En pratique, un `Dataset` décrit la façon d'obtenir **un** échantillon, à partir des tenseurs `x` et `y` construits à la main ; `random_split` découpe ensuite en entraînement, validation et test, selon le protocole des [[Jeux d'entraînement, de développement et de test|jeux d'entraînement, de développement et de test]] ; `DataLoader` fournit des mini-lots mélangés.

```python
from torch.utils.data import Dataset, DataLoader
from torch.utils.data import random_split

class PopulationDataset(Dataset):
    def __init__(self, x, y):      # tensors, as in TP2
        self.x, self.y = x, y
    def __len__(self):
        return len(self.x)
    def __getitem__(self, i):
        return self.x[i], self.y[i]

ds = PopulationDataset(x, y)
train, valid, test = random_split(ds, [0.7, 0.1, 0.2])
loader = DataLoader(train, batch_size=32, shuffle=True)
for x_batch, y_batch in loader:
    ...                            # the four lines
```

Chaque tour de boucle reçoit un lot `x_batch`, `y_batch`, sur lequel s'appliquent les quatre lignes de la [[Boucle d'entraînement et validation|boucle d'entraînement]].

# Remarque

La taille de lot $B$, comme le nombre d'époques, est un [[Hyper-paramètres|hyper-paramètre]] : ces valeurs se comparent sur le jeu de validation.

Un lot réunit les échantillons sur un axe supplémentaire de taille $B$ : les opérations s'appliquent alors au lot entier par [[Diffusion entre tenseurs|diffusion]].

Des mini-lots de séquences de longueurs différentes ne peuvent pas être empilés tels quels : voir [[Longueur variable des séquences]].
