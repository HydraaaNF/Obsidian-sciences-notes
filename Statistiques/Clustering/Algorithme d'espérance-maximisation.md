# Algorithme

L'**algorithme d'espérance-maximisation** (EM) compense des données manquantes (ou [[Variables cachées d'un modèle de mélange|données latentes]]) en les remplaçant par leurs espérances. Il s'applique en particulier à l'[[Estimation par maximum de vraisemblance d'un modèle de mélange|estimation par maximum de vraisemblance]] des paramètres d'un [[Modèles de mélange|modèle de mélange]].

Le principe est itératif :

1. estimer les variables manquantes étant donné une estimation courante des paramètres ;
2. estimer de nouveaux paramètres étant donné l'estimation courante des variables manquantes ;
3. répéter les étapes 1 et 2 jusqu'à convergence.

Sous forme algorithmique :

```
choisir des paramètres initiaux (bons) θ_0
n ← 0
tant que la convergence n'est pas atteinte faire
  (a) pour i = 1 → N et j = 1 → K faire
    calculer la probabilité a posteriori de composante γ_j^(n)(i)
  fin pour
  (b) pour chaque paramètre α ∈ θ faire
    calculer la nouvelle valeur α_{n+1} à partir des quantités γ_j^(n)(i)
    (en maximisant Q(θ, θ_n))
  fin pour
  (c) n ← n + 1
fin tant que
```

À l'étape (a), l'algorithme calcule la probabilité a posteriori de composante, c'est-à-dire la [[Probabilité d'appartenance à une classe|probabilité d'appartenance]] de l'observation $i$ à la composante $j$ :

$$\gamma_j^{(n)}(i) = \mathbb{P}[Z_i = j \mid x_i ; \theta_n].$$

À l'étape (b), il réestime chaque paramètre $\alpha$ en maximisant la [[Fonction auxiliaire de l'algorithme d'espérance-maximisation|fonction auxiliaire]] $Q(\theta, \theta_n)$.

# Remarque

Le principe s'applique à de nombreux problèmes, pas seulement à l'[[Méthode du maximum de vraisemblance|estimation par maximum de vraisemblance]] des paramètres.

Les propriétés de l'algorithme et sa convergence sont détaillées dans [[Propriétés et convergence de l'algorithme d'espérance-maximisation]] ; son application aux [[Mélange gaussien|mélanges gaussiens]] est traitée dans [[Espérance-maximisation pour un mélange de gaussiennes]].
