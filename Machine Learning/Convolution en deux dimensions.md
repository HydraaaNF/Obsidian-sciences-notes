#ml-2

# Définition

Une convolution en deux dimensions prend une entrée décrite par deux axes spatiaux et des canaux, et lui applique un noyau rectangulaire qui la traverse sur toute son épaisseur :

- $H \times W$ : hauteur et largeur de l'entrée ;
- $C$ : nombre de canaux de l'entrée ;
- $\mathbf{k} = (k_1, k_2)$ : taille du noyau, par exemple $\mathbf{k} = (3,3)$ ;
- $\mathbf{w} = (w_{c,u,v})$ : poids du noyau, pour $1 \le c \le C$, $1 \le u \le k_1$ et $1 \le v \le k_2$ ;
- $b$ : biais ;
- $\mathbf{w}$ et $b$ sont des paramètres apprenables ;
- $y_{i,j}$ : élément de la carte d'activation produite.

$$y_{i,j} = \sum_{c=1}^{C} \sum_{u=1}^{k_1} \sum_{v=1}^{k_2} w_{c,u,v}\, x_{c,\, i+u-1,\, j+v-1} + b,
\qquad i = 1, \dots, H - k_1 + 1,\quad j = 1, \dots, W - k_2 + 1$$

Une entrée peut compter plusieurs canaux. Le noyau possède alors la même profondeur que l'entrée, la traverse sur toute son épaisseur (la somme porte sur les $C$ canaux) et produit une carte d'activation, c'est-à-dire un unique canal de sortie. Un noyau distinct est employé par canal de sortie.

# Interprétation

Le noyau est une fenêtre rectangulaire qui glisse simultanément selon les deux axes de l'entrée, toujours avec les **mêmes** poids : les paramètres sont partagés entre toutes les positions. Chaque élément $y_{i,j}$ agrège ainsi une région locale $k_1 \times k_2$ de l'entrée.

La convolution en deux dimensions est la généralisation de la [[Convolution en une dimension]] : le noyau y couvre une surface au lieu d'un segment, donc la sortie diminue en hauteur **et** en largeur. Sur l'entrée $3 \times 24$ et le noyau $3 \times 3$, il ne reste qu'une position verticale ($3 - 3 + 1 = 1$) et $22$ positions horizontales ($24 - 3 + 1 = 22$). Le calcul de ces dimensions est détaillé dans [[Taille de sortie d'une convolution]].

Les noyaux sont les paramètres appris par une [[Couche de convolution]] ; le padding, le stride et la dilation modifient la taille de la sortie (voir [[Padding, stride et dilation]]).

# Exemple

### Entrée $3 \times 24$ et noyau $3 \times 3$

| Élément | Dimension |
| --- | --- |
| Entrée | $3 \times 24$ |
| Noyau (1 kernel) | $3 \times 3$ |
| Sortie | $1 \times 22$ |

Avec $k_1 = k_2 = 3$, un canal d'entrée (`in_channels`) et un canal de sortie (`out_channels`), la sortie est de forme $1 \times 22$. Comme $C = 1$, la somme sur les canaux se réduit au canal $c = 1$ : chaque élément de sortie est la somme pondérée des $9$ valeurs de la fenêtre $3 \times 3$ correspondante, plus le biais :

$$y_{i,j} = \sum_{u=1}^{3} \sum_{v=1}^{3} w_{1,u,v}\, x_{1,\, i+u-1,\, j+v-1} + b$$

La longueur d'entrée est **différente** de la longueur de sortie : $24$ colonnes en entrée donnent $22$ colonnes par canal, et non $24$.

```mermaid
flowchart LR
    E["Entrée : 3 x 24, 1 canal"] --> K["Noyau : 3 x 3, 1 filtre"]
    K --> S["Sortie : 1 x 22, 1 canal"]
```

### Même convolution avec PyTorch

Un `nn.Conv2d` déclare le nombre de canaux d'entrée, le nombre de canaux de sortie, la taille du noyau et la présence du biais. L'entrée d'un lot se range dans l'ordre `batch`, `channels`, `hauteur`, `largeur` :

```python
c = nn.Conv2d(1, 1, (3, 3), bias=True)  # c_in, c_out, kernel, bias
input = torch.randn(1, 1, 3, 24)        # batch, channels, values, values

print(input.shape)    # -> torch.Size([1, 1, 3, 24])
print(c(input).shape) # -> torch.Size([1, 1, 1, 22])
```

Le lot compte une seule entrée, d'un seul canal, de hauteur $3$ et de largeur $24$ ; la couche renvoie un lot d'une carte d'activation $1 \times 22$. L'usage de cette couche dans un modèle complet est décrit dans [[Réseau convolutif avec PyTorch]].

# Propriétés

Sur chaque axe, sans padding, sans stride et sans dilation, la taille de sortie vaut la taille d'entrée moins la taille du noyau plus un :

$$H_{\text{out}} = H - k_1 + 1, \qquad W_{\text{out}} = W - k_2 + 1$$

Ces deux dimensions se lisent sur la [[Forme d'un tenseur]] de sortie, par exemple $(1, 1, 1, 22)$ pour un lot d'une entrée à un canal.

# Remarque

Le noyau glisse indépendamment selon chaque axe : un noyau $3 \times 3$ sur une entrée de hauteur $3$ ne laisse qu'une seule position verticale, alors que la largeur $24$ laisse $22$ positions horizontales. Une entrée de hauteur inférieure à $k_1$, ou de largeur inférieure à $k_2$, ne fournit aucune position de sortie.

La [[Convolution en une dimension]] est le cas particulier de cette opération sur un signal à un seul axe spatial. Les images sont le domaine usuel de la convolution en deux dimensions, avec un noyau qui traverse les canaux de couleur de l'entrée.
