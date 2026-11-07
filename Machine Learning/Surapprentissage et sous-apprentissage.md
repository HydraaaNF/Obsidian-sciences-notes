#ml-1

# Définition

Le **surapprentissage** (*overfitting*) est le défaut d'un modèle trop complexe, qui apprend trop près des données d'entraînement.

Le **sous-apprentissage** (*underfitting*) est le défaut d'un modèle trop simple, ou qui dispose de trop peu de données d'entraînement.

# Exemple

Sur l'exemple des oiseaux, dont la taille sert à prédire le niveau de gris, trois ajustements se comparent sur un même nuage de points :

- une droite : modèle de régression linéaire, trop simple, en sous-apprentissage ;
- une courbe régulière en tirets : ajustement équilibré ;
- une courbe fortement oscillante en trait mixte : modèle très complexe, qui passe au plus près de chaque point d'entraînement, en surapprentissage.

Les points noirs sont les données d'entraînement, les croix vertes les données de test ou de validation. Sous surapprentissage, la courbe colle aux points noirs mais les croix vertes s'en écartent largement : l'ajustement décrit le bruit des données d'entraînement plutôt que la tendance.

# Remarque

- Le surapprentissage se détecte en suivant l'erreur de validation : l'erreur d'entraînement diminue toujours et ne dit rien, tandis qu'une erreur de validation qui remonte signale le surapprentissage. Voir la partition des données en [[Jeux d'entraînement, de développement et de test|jeux d'entraînement, de développement et de test]].
- Un modèle trop complexe appartient à une famille riche en paramètres, dont le coût se lit dans l'[[Erreur d'approximation et erreur d'estimation|erreur d'estimation]] ; un modèle trop simple pèche au contraire par l'erreur d'approximation.
- Le modèle équilibré évite les deux excès à la fois : assez riche pour suivre la tendance réelle, assez contraint pour ne pas suivre le bruit. Ce compromis relève du principe de parcimonie du [[Rasoir d'Occam]].
