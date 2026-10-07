# Définition

L'apprentissage consiste à chercher une bonne fonction dans un [[Espace d'hypothèses|espace de fonctions]] $\mathcal{F}$. La perte associée à une fonction $f \in \mathcal{F}$ sur une donnée $z$ est mesurée par une fonction de perte $L : \mathcal{Z} \times \mathcal{F}$, notée $L(z, f)$.

# Exemple

Exemples de fonctions de perte :

- **Régression** :
  $$L(z, f) = L((x, y), f) = (f(x) - y)^2$$
- **Classification** :
  $$L(z, f) = L((x, y), f) = \begin{cases} 0 & \text{if } f(x) = y \\ 1 & \text{otherwise} \end{cases}$$
- **Estimation de densité** :
  $$L(z, f) = -\log p(z)$$

# Remarque

La fonction de perte est utilisée pour définir le [[Risque et risque empirique]] ; le [[Risque généralisé]] étend le risque défini à partir d'une fonction de perte.
