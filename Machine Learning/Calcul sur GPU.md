#ml-1

# Définition

Le produit matriciel est ce pour quoi un GPU est conçu (voir [[Forme matricielle de la régression]]).

En PyTorch, un [[Tenseurs PyTorch|tenseur]] vit sur un appareil donné, désigné par `"cuda"` pour le GPU et `"cpu"` pour le processeur. Le modèle et les données doivent vivre sur le **même** appareil ; on les y transfère par `.to(device)`.

# Algorithme

Le modèle rejoint l'appareil une seule fois, avant la boucle, puis chaque mini-lot à son tour :

```python
device = "cuda" if torch.cuda.is_available() else "cpu"
model = model.to(device)

for x_batch, y_batch in loader:
    x_batch = x_batch.to(device)
    y_batch = y_batch.to(device)
    ...
    # the four lines, unchanged
```

Le choix de l'appareil se fait à l'exécution : `torch.cuda.is_available()` est vrai quand un GPU est présent, et le code bascule sinon sur le CPU. Les quatre lignes de la boucle d'entraînement ne changent pas (voir [[Boucle d'entraînement et validation]]) : seuls les transferts de tenseurs s'ajoutent, le modèle venant de [[Composer un réseau avec PyTorch]] et les lots de [[Lots, époques et chargement des données]].

# Remarque

La mémoire est une contrainte à part entière : le modèle, un mini-lot et le [[Graphe de calcul|graphe]] de rétropropagation doivent tous tenir en même temps sur l'appareil.

Sur une machine sans GPU, le même code s'exécute sur le CPU : c'est la branche `else` du choix d'appareil qui le permet, sans modification du reste du programme.
