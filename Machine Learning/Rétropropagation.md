#ml-1

# Définition

La rétropropagation calcule les dérivées partielles de la perte par rapport à chaque entrée d'un [[Graphe de calcul]] en remontant le graphe depuis la perte, une boîte à la fois.

Chaque opération embarque sa propre dérivée locale :

- la multiplication connaît $\partial(uv)/\partial u = v$ ;
- l'élévation au carré connaît $\partial(e^2)/\partial e = 2e$.

Le gradient se propage en parcourant le graphe vers l'arrière et en multipliant, à chaque boîte, le gradient reçu par le facteur local.

# Exemple

Passe avant sur un échantillon isolé $(x, y) = (4, 7)$ :

- $z = ax$ ;
- $\hat{y} = z + b$ ;
- $e = \hat{y} - y = -2$ ;
- $\ell = e^2$.

Dérivées locales de ces boîtes :

- $\partial z/\partial a = x = 4$ ;
- $\partial \hat{y}/\partial z = 1$ ;
- $\partial e/\partial \hat{y} = 1$ ;
- $\partial \ell/\partial e = 2e = -4$.

Parcours arrière, en partant de la perte :

- $\partial \ell/\partial \ell = 1$ ;
- $\partial \ell/\partial e = 1 \times 2e = -4$ ;
- $\partial \ell/\partial \hat{y} = -4 \times 1 = -4$ ;
- $\partial \ell/\partial z = -4 \times 1 = -4$ ;
- $\partial \ell/\partial a = -4 \times x = -16$ ;
- $\partial \ell/\partial b = -4 \times 1 = -4$.

# Propriétés

Le parcours démarre à $1$ parce que $\partial \ell/\partial \ell = 1$ : c'est la graine du calcul, pas une convention.

L'addition laisse passer le gradient, la multiplication le multiplie par l'autre entrée.

Aucune boîte du graphe ne connaît $L$ ni le jeu de données, et pourtant $\partial \ell/\partial a$ sort du parcours.

Les paramètres sont partagés par tous les échantillons, donc on lance le parcours arrière une fois par échantillon et les gradients des paramètres s'additionnent. Avec les trois échantillons $x = 1, 2, 4$ et les erreurs $e = 1, -1, -2$ correspondantes :

- $x = 1$, $e = 1$ : $2e = 2$ et $2ex = 2$ ;
- $x = 2$, $e = -1$ : $2e = -2$ et $2ex = -4$ ;
- $x = 4$, $e = -2$ : $2e = -4$ et $2ex = -16$.

En sommant sur les échantillons :

$$\frac{\partial L}{\partial b} = \sum_i 2e_i = -4$$

$$\frac{\partial L}{\partial a} = \sum_i 2e_i x_i = -18$$

Ces deux valeurs coïncident exactement avec le calcul analytique de la dérivée de la perte totale.

Un paramètre peut aussi apparaître sur plusieurs chemins du graphe. En liant $b$ à $a$ avec $f(x) = ax + a$, le paramètre $a$ est utilisé deux fois : il faut additionner la contribution de chaque chemin.

$$\frac{\partial L}{\partial a} = \underbrace{-18}_{\text{via } \times} + \underbrace{-4}_{\text{via } +} = -22$$

### Démonstration

La forme fermée de la perte pour ce modèle est $L = \sum_i \left(a(x_i + 1) - y_i\right)^2$, d'où

$$\frac{\partial L}{\partial a} = \sum_i 2e_i(x_i + 1) = -18 + (-4) = -22$$

ce qui redonne bien la somme des deux contributions.

# Remarque

Un logiciel de [[Différenciation automatique]] comme PyTorch accumule les gradients dans l'attribut `.grad` des tenseurs. C'est exactement pour cette raison que `a.grad` doit être remis à zéro entre deux étapes : deux `backward()` successifs donnent $-36$ au lieu de $-18$.

Le gradient ainsi accumulé est la quantité que consomment les [[Optimiseurs]] pour mettre à jour les paramètres.
