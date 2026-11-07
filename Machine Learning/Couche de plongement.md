#ml-1

# Définition

Une couche de plongement associe à chaque symbole d'un vocabulaire de taille $V$ un vecteur de taille $H$, appelé [[Plongement|plongement]] du symbole et appris comme n'importe quel autre poids du réseau. C'est une couche linéaire appliquée à un [[Encodage des valeurs symboliques|encodage one-hot]] : sa matrice de poids est une table de $V$ vecteurs de dimension $H$.

# Propriétés

En notant $x_k$ le vecteur one-hot en ligne du symbole $k$, de taille $V$, et $W$ la matrice de poids de la couche, de taille $V \times H$, le plongement obtenu vaut

$$e_k = x_k W = W_{k,:}$$

où $W_{k,:}$ est la ligne $k$ de $W$. Une couche linéaire appliquée à un vecteur one-hot ne fait donc que **sélectionner une ligne** de sa matrice :

$$
\begin{bmatrix} 0 & \cdots & 0 & 1 & 0 & \cdots & 0 \end{bmatrix}
\begin{bmatrix}
w_{1,1} & \cdots & w_{1,H} \\
\vdots & & \vdots \\
w_{k,1} & \cdots & w_{k,H} \\
\vdots & & \vdots \\
w_{V,1} & \cdots & w_{V,H}
\end{bmatrix}
=
\begin{bmatrix} w_{k,1} & \cdots & w_{k,H} \end{bmatrix}
$$

Le produit est inutile : il suffit de lire directement la ligne $k$. En pratique, l'entrée de la couche est donc l'indice du symbole, de type `long`, et le one-hot n'est pas nécessaire.

La couche ne combine pas les entrées : elle lit une ligne de sa table, et toute l'information vient des valeurs qui y sont apprises.

# Exemple

Avec un vocabulaire de $V$ mots et des plongements de dimension $H$ :

```python
import torch.nn.functional as F

emb = nn.Embedding(V, H)      # V mots, H dimensions
w = torch.tensor([42])        # un indice de mot (long)
emb(w).shape                  # torch.Size([1, H])

one_hot = F.one_hot(w, V).float()
torch.equal(one_hot @ emb.weight, emb(w))  # True
```

`nn.Embedding(V, H)` est cette table de $V$ vecteurs de taille $H$. L'indice `42` renvoie directement la ligne correspondante, de forme `(1, H)` ; le produit du one-hot associé par `emb.weight` donne le même vecteur.

# Interprétation

La même notion apparaît des deux côtés d'un réseau :

- du côté de l'entrée, une couche de plongement fournit un vecteur par mot, lu par son indice ;
- du côté de la sortie, la dernière couche fournit un vecteur par classe, comparé à la représentation courante par un produit scalaire (voir [[Un vecteur par classe]]), ce qui explique pourquoi des entrées similaires finissent proches.

[[word2vec]] apprend les deux : un vecteur d'entrée et un vecteur de sortie pour chaque mot. Les Transformers emploient souvent la **même** matrice des deux côtés.

Un même modèle peut réunir les deux rôles : une couche de plongement pour les lettres en entrée, une classe par lettre en sortie.
