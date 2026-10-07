# Définition

**Le problème.** À partir d'un (grand) corpus de séquences $\mathcal{C} = \{S_1, \dots, S_n\}$, estimer l'ensemble des probabilités conditionnelles $\mathbb{P}[w \mid h]$ d'un modèle de Markov, pour tous $h$ et $w$, où $h$ désigne le contexte et $w$ le symbole qui le suit.

# Propriétés

La solution est donnée par l'**[[Méthode du maximum de vraisemblance|estimation par maximum de vraisemblance]]** ; l'[[Estimateur du maximum de vraisemblance|estimateur du maximum de vraisemblance]] s'écrit comme une fréquence relative :

$$\tilde{\mathbb{P}}[w \mid h] = \frac{C(hw)}{C(h)} = \frac{C(hw)}{\sum_{v \in V} C(hv)} = \frac{\text{nombre de fois où l'on voit } hw}{\text{nombre de fois où l'on voit } h}$$

Cette solution provient de la maximisation de la log-[[Fonction de vraisemblance|vraisemblance]] du corpus

$$\ln \mathbb{P}[C] = \sum_{i=1}^n \ln \mathbb{P}[S_i] = \sum_{i=1}^n \left( \ln(\mathbb{P}[s_1^i \mid \epsilon]) + \sum_{k=2}^{n_i} \ln(\mathbb{P}[s_k^i \mid s_{k-1}^i]) \right)$$

sous les contraintes de normalisation $\sum_w \mathbb{P}[w \mid h] = 1 \quad \forall h$.

# Remarque

Une version lissée de l'estimateur est nécessaire en pratique : voir le [[Lissage des probabilités|lissage des probabilités]]. Les probabilités estimées sont les paramètres du [[Modèle de Markov pour les textes]].
