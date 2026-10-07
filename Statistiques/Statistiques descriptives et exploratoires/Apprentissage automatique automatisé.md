# Définition

L'**apprentissage automatique automatisé** (Auto-ML) a pour objectif la **sélection automatique des modèles et de leurs paramètres**.

# Modèle

Le cadre standard est la **vision bayésienne** du problème, qui fait intervenir trois probabilités :

- $\mathbb{P}(\text{model})$ : probabilité d'un modèle ;
- $\mathbb{P}(\theta \mid \text{model})$ : probabilité des paramètres $\theta$ sachant le modèle ;
- $\mathbb{P}(z \mid \theta, \text{model})$ : probabilité de $z$ sachant les paramètres et le modèle.

# Remarque

La sélection automatique des modèles et de leurs paramètres s'inscrit dans la problématique de la [[Sélection de modèle et estimation de la performance|sélection de modèle]] et de l'estimation de la performance. Le cadre bayésien décrit ci-dessus est celui de l'[[Estimation bayésienne]].
