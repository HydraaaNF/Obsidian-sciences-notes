# Modèle

La régression logistique multinomiale étend la [[Régression logistique binaire]] au cas où la variable de classe prend plus de deux valeurs.

- Variables observées : $X = \{X_1, \dots, X_n\}$.
- Variable de classe : $Y \in \{1, \dots, K\}$, de loi multinomiale.
- Un jeu de coefficients de régression par classe : $\lambda_0^{(k)}, \lambda_1^{(k)}, \dots, \lambda_n^{(k)}$ pour $k = 1, \dots, K$.

La probabilité a posteriori de la classe $k$ est donnée par

$$\mathbb{P}[Y = k \mid X = \mathbf{x}] = \frac{\exp\left(\lambda_0^{(k)} + \lambda_1^{(k)} x_1 + \dots + \lambda_n^{(k)} x_n\right)}{\sum_{c=1}^{K} \exp\left(\lambda_0^{(c)} + \lambda_1^{(c)} x_1 + \dots + \lambda_n^{(c)} x_n\right)}$$

En notant $\boldsymbol{\lambda}^{(k)} = (\lambda_1^{(k)}, \dots, \lambda_n^{(k)})^\top$ le vecteur des coefficients de la classe $k$ et $\mathbf{x} = (x_1, \dots, x_n)^\top$ le vecteur des observations, la même formule s'écrit

$$\mathbb{P}[Y = k \mid X = \mathbf{x}] = \frac{1}{Z(\mathbf{x})} \exp\left(\lambda_0^{(k)} + \boldsymbol{\lambda}^{(k)\top} \mathbf{x}\right)$$

avec le facteur de normalisation

$$Z(\mathbf{x}) = \sum_{c=1}^{K} \exp\left(\lambda_0^{(c)} + \boldsymbol{\lambda}^{(c)\top} \mathbf{x}\right)$$

# Interprétation

Chaque classe dispose de son propre score linéaire en les observations, $\lambda_0^{(k)} + \boldsymbol{\lambda}^{(k)\top} \mathbf{x}$, et la probabilité a posteriori est ce score transformé puis normalisé sur l'ensemble des classes.

Cette quantité joue le rôle du score du [[Modèle log-linéaire conditionnel]] : les observations $x_i$ y tiennent lieu de fonctions de traits et le coefficient qui les pondère dépend de la classe visée. Le facteur de normalisation $Z(\mathbf{x})$ est commun à toutes les classes et prend la même forme que dans ce modèle.

Comme $Z(\mathbf{x})$ ne dépend pas de $k$, la classe la plus probable est celle dont le score est maximal : comparer les probabilités a posteriori revient à comparer les scores.

# Propriétés

Le logarithme du rapport des probabilités a posteriori de deux classes est une combinaison linéaire des observations :

$$\ln \frac{\mathbb{P}[Y = k \mid X = \mathbf{x}]}{\mathbb{P}[Y = c \mid X = \mathbf{x}]} = \left(\lambda_0^{(k)} - \lambda_0^{(c)}\right) + \sum_{i=1}^{n} \left(\lambda_i^{(k)} - \lambda_i^{(c)}\right) x_i$$

C'est le prolongement du log-rapport linéaire qui définit la [[Régression logistique binaire]].

Pour $K = 2$, en posant $Y \in \{0, 1\}$, la formule se réduit à la sigmoïde de la régression logistique binaire, avec pour coefficients les différences $\lambda_i^{(1)} - \lambda_i^{(0)}$ entre les deux classes.

# Remarque

- L'exposant $k$ désigne la classe du score et l'indice $i$ la covariable $x_i$. La somme du dénominateur porte sur les classes et est indicée $c$ dans cette note, pour ne pas la confondre avec l'indice $i$ des covariables.
- Le même modèle s'écrit aussi sous forme vectorielle avec un biais $b^{(k)}$ et un vecteur de poids $\mathbf{w}^{(k)}$ à la place de $\lambda_0^{(k)}$ et $\boldsymbol{\lambda}^{(k)}$. Cette note retient la notation en $\lambda$, alignée sur la [[Régression logistique binaire]] et sur le [[Modèle log-linéaire conditionnel]].
- Le principe d'un jeu de coefficients par étiquette, normalisé sur l'ensemble des étiquettes, s'étend des classes aux séquences : voir les [[Fonctions de traits pour les séquences]].
