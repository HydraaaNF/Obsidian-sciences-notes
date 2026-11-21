#ml-1

# Modèle

La [[Régression linéaire]] suppose une entrée et une sortie scalaires. Le cadre se généralise en gardant les mêmes objets, avec des dimensions plus grandes : l'entrée $x$ est de dimension $n$ et la sortie $f(x)$ de dimension $m$.

Les paramètres deviennent alors :

- la matrice $A$ de taille $m \times n$, dont chaque ligne porte les poids d'une composante de la sortie ;
- le vecteur $b$ de $m$ valeurs, une par composante.

$$h = f(xA^\top + b)$$

où $x$ est vu comme une ligne de $n$ valeurs, si bien que $xA^\top$ est de taille $m$. Pour $m = 1$, on retrouve $f(x) = ax + b$ avec $a$ de dimension $n$ : la règle de calcul ne change pas, seules les tailles des objets changent.

L'écriture matricielle remplace la boucle sur les échantillons par un seul produit matriciel. Le graphe de calcul et les règles de dérivation locales restent identiques, ce sont les tenseurs qui grandissent. Un mini-lot ajoute simplement une dimension supplémentaire, celle des échantillons.

C'est ce produit qui concentre tout le calcul arithmétique, et c'est exactement ce pour quoi un GPU est conçu : le même programme appliqué à un grand nombre de valeurs en parallèle. C'est à cela que sert l'attribut `device` d'un tenseur.

Rien n'oblige la famille de fonctions à être affine : toute famille différentiable convient. C'est la porte d'entrée du [[Perceptron multicouche]].

# Propriétés

Pour un lot de $B$ échantillons, les formes s'enchaînent ainsi :

- `x @ A`, ou `torch.matmul(x, A)` : $(B, n)$ multiplié par $(n, m)$ donne $(B, m)$ ;
- les tailles intérieures doivent coïncider, les tailles extérieures donnent la forme du résultat ;
- ajouter $b$, de forme $(m,)$, le [[Diffusion entre tenseurs|diffuse]] sur chaque ligne du lot ;
- avec un vecteur $a$ de forme $(n,)$, `x @ a` a pour forme $(B,)$ et non $(B, 1)$.

```
x = torch.rand(16, 2)      # 16 échantillons, 2 attributs
A = torch.rand(2, 1)       # une sortie
b = torch.rand(1)
(x @ A + b).shape          # torch.Size([16, 1])

a = torch.rand(2)          # un vecteur
(x @ a).shape              # torch.Size([16]) : pas d'axe 1
```
