#ml-1

# Définition

Les données se répartissent en deux catégories selon la structure qu'elles imposent à leurs valeurs :

- les données **structurées** sont gouvernées par une structure de données particulière ;
- les données **non structurées** sont celles dont l'ordre des valeurs n'a guère d'importance.

# Exemple

Données structurées, chacune portée par une structure de données :

- une **liste** pour un texte ;
- un **arbre** pour une expression arithmétique ;
- un **graphe** pour des relations sociales.

Données non structurées, où permuter les valeurs ne change rien :

- le couple (taille, poids) et le couple (poids, taille) ;
- les **ensembles** et les **sacs**.

# Remarque

Dans une donnée structurée, la position d'une valeur dans la structure est porteuse d'information ; dans une donnée non structurée, remettre les valeurs dans un autre ordre ne modifie pas la donnée.

Un **sac** autorise les répétitions, contrairement à un ensemble.

Les valeurs elles-mêmes, leur type et leur domaine se décrivent avec les notions de [[Donnée et attributs]].

Cette structure conditionne la façon de conserver les données, voir [[Stockage des données]].

Les données numériques manipulées par les modèles d'apprentissage sont rangées dans des [[Tenseur|tenseurs]], tableaux à $n$ dimensions.
