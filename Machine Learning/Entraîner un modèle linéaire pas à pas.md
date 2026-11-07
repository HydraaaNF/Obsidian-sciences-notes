#ml-1

# Modèle

Le modèle affine de la [[Régression linéaire]] prédit $f_{a,b}(x) = ax + b$ et s'entraîne en minimisant la perte quadratique totale sur $n$ échantillons, somme des pertes par échantillon :

$$L(a,b) = \sum_i \left(f_{a,b}(x_i) - y_i\right)^2$$

Les dérivées partielles $\frac{\partial L}{\partial a}$ et $\frac{\partial L}{\partial b}$ indiquent le sens et l'amplitude de la correction à appliquer à chaque paramètre. Leur calcul est confié à la [[Différenciation automatique]], et la règle de mise à jour est celle de la [[Descente de gradient]] :

- $a \leftarrow a - \alpha \dfrac{\partial L}{\partial a}$ ;
- $b \leftarrow b - \alpha \dfrac{\partial L}{\partial b}$.

# Exemple

À partir de $(a_0, b_0) = (1, 1)$, où $L = 6$, les deux dérivées sont négatives : la perte diminue quand $a$ et $b$ augmentent.

Une mise à jour avec $\alpha = 0{,}025$ :

- $a_1 = 1 - 0{,}025 \times (-18) = 1{,}45$ ;
- $b_1 = 1 - 0{,}025 \times (-4) = 1{,}10$ ;
- $L$ passe de $6$ à $2{,}41$.

Après 200 pas de ce type : $a = 1{,}93$, $b = -0{,}49$, $L = 0{,}64$ ; c'est la droite qui ajuste déjà les points.

Contrôle sur la courbe à un paramètre. En supprimant $b$, le modèle se simplifie en $f(x) = ax$ et le rétrocalcul à la main donne

$$\frac{\partial L}{\partial a} = \sum_i 2 e_i x_i = 0 - 8 - 24 = -32$$

où $e_i = f(x_i) - y_i$. La courbe de la perte pour ce modèle est $L(a) = 21a^2 - 74a + 66$, donc $L'(a) = 42a - 74$ et $L'(1) = -32$ : les règles locales appliquées sur le graphe redonnent la dérivée globale de la fonction.

# Algorithme

Une étape d'entraînement avec les [[Tenseurs PyTorch]] tient en quatre temps : passe avant, rétropropagation, mise à jour des paramètres, remise à zéro du gradient.

```
a = torch.tensor([1.0], requires_grad=True)

loss = ((a * x - y) ** 2).mean()
loss.backward()                     # remplit a.grad
with torch.no_grad():               # la mise à jour n'est pas enregistrée
    a -= lr * a.grad
a.grad.zero_()                      # avant la rétropropagation suivante

history.append(loss.item())         # un flottant, pour tracer plus tard
plt.plot(x, (a * x).detach())       # hors du graphe d'abord
```

Trois précautions accompagnent ce code :

- la mise à jour doit rester hors du graphe, d'où le bloc `torch.no_grad()` ; écrire `a.data = a.data - lr * a.grad.data` contourne lui aussi l'enregistrement ;
- le gradient s'accumule d'un appel à l'autre : il faut le remettre à zéro avec `a.grad.zero_()` avant chaque nouvelle rétropropagation ;
- pour journaliser ou tracer, `.item()` renvoie un nombre Python et `.detach()` un tenseur sorti du graphe.

# Remarque

- Le graphe ne fait que rejouer des règles de dérivation locales, nœud par nœud, et la dérivée globale en sort exactement : l'automatisation répète ce calcul sans se fatiguer, ce qui rend possible l'enchaînement de milliers d'étapes.
- [[Différenciation automatique]] et [[Descente de gradient]] se complètent : la première fournit les dérivées, la seconde les utilise pour déplacer les paramètres.
- Les [[Optimiseurs]] généralisent cette règle de mise à jour.
- La perte est ici une somme : à $(1, 1)$ elle vaut $6$, tandis que la moyenne des pertes quadratiques sur les trois échantillons vaudrait $2$. Le code de l'étape d'entraînement emploie `.mean()` : la division par $n = 3$ ne change ni le signe des dérivées ni la direction de la mise à jour, seulement leur amplitude.
