#ml-2

# Algorithme

L'entraînement d'un [[Réseau antagoniste génératif|réseau antagoniste génératif]] alterne deux optimisations : une mise à jour du discriminateur $D$, puis une mise à jour du générateur $G$. Chaque réseau possède son propre [[Optimiseurs|optimiseur]], qui ne modifie que ses paramètres.

La perte utilisée est l'[[Entropie croisée binaire]], notée $\mathrm{BCE}$, appliquée à la sortie de $D$ : le discriminateur se termine par une sigmoïde, sa sortie est donc une probabilité.

- Pour le discriminateur, les données réelles portent l'étiquette 1 et les données générées l'étiquette 0 :

$$\mathcal{L}_D = \mathrm{BCE}\big(D(x), 1\big) + \mathrm{BCE}\big(D(G(z)), 0\big)$$

- Pour le générateur, les données générées portent l'étiquette 1 : il cherche à faire passer ses échantillons pour réels.

$$\mathcal{L}_G = \mathrm{BCE}\big(D(G(z)), 1\big)$$

La boucle, sur chaque lot de données réelles :

```python
bce = nn.BCELoss()   # D se termine par une sigmoïde
for x_real in loader:
    n = len(x_real)
    ones, zeros = torch.ones(n, 1), torch.zeros(n, 1)
    x_fake = G(torch.randn(n, dim_z))

    # 1) discriminateur : réel -> 1, généré -> 0
    loss_D = bce(D(x_real), ones) + bce(D(x_fake.detach()), zeros)
    opt_D.zero_grad()
    loss_D.backward()
    opt_D.step()

    # 2) générateur : tromper le discriminateur (généré -> 1)
    loss_G = bce(D(x_fake), ones)
    opt_G.zero_grad()
    loss_G.backward()
    opt_G.step()
```

Chaque étape suit la [[Boucle d'entraînement et validation|boucle d'entraînement]] habituelle : remise à zéro des gradients, rétropropagation du [[Graphe de calcul|graphe de calcul]], puis pas d'optimisation.

- À chaque lot, le générateur fabrique $x_{fake}$ à partir d'un bruit aléatoire $z$.
- `x_fake.detach()` détache l'échantillon généré du graphe de calcul : la rétropropagation de $\mathcal{L}_D$ ne met pas à jour $G$.
- Les deux optimiseurs sont séparés : `opt_D` ne met à jour que $D$, `opt_G` ne met à jour que $G$.
- Le générateur ne voit jamais les données réelles : il n'apprend qu'à travers le discriminateur.
- Le même lot d'échantillons générés sert aux deux étapes, mais seul le second calcul laisse le gradient remonter jusqu'à $G$.

# Remarque

L'équilibre entre les deux joueurs est délicat.

- Si $D$ est trop fort, $D(G(z)) \approx 0$ et le générateur ne reçoit presque aucun gradient.
- Si $D$ est trop faible, il n'apporte au générateur aucune information utile.

L'effondrement des modes (*mode collapse*) est un autre échec : $G$ trouve quelques échantillons qui trompent $D$ et ne produit plus que ceux-là, par exemple toujours le même visage.

L'entraînement est instable : les deux pertes oscillent et n'indiquent pas quand arrêter.

Enfin, le modèle ne fournit aucune vraisemblance $p(x)$, ce qui interdit l'évaluation par la vraisemblance des données ; on recourt à d'autres métriques, comme la FID (Fréchet Inception Distance), et à l'inspection des échantillons produits.
