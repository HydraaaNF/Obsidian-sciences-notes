#dmv-subgroup_discovery

# Définition

Un jeu de données se représente comme un tableau dont chaque ligne est une transaction et chaque colonne un [[Attribut et types d'attributs|attribut]].

Les colonnes se partitionnent en deux groupes :

- les **attributs de description**, sur lesquels se formule la condition qui définit le sous-groupe ;
- les **attributs cibles**, qui portent la propriété dont on étudie la valeur.

Le nombre d'attributs cibles n'est pas limité à un : plusieurs attributs cibles peuvent être traités simultanément, la partition séparant alors un bloc de descripteurs et un bloc de cibles.

# Exemple

Le schéma de la partition est celui d'une table coupée verticalement : les transactions restent les lignes communes aux deux blocs, les colonnes de gauche portent les attributs sur lesquels se formule la description du sous-groupe, les colonnes de droite la propriété étudiée.

| partie de la table | contenu |
| --- | --- |
| lignes | une transaction par ligne, communes aux deux blocs de colonnes |
| bloc gauche de colonnes | attributs de description : la condition du sous-groupe s'y formule |
| bloc droit de colonnes | attributs cibles : la propriété étudiée, plusieurs colonnes possibles |

Un sous-groupe est alors un sous-ensemble de lignes, sélectionné par une condition portant sur les seules colonnes de description, dont les valeurs sur les colonnes cibles s'écartent de celles de la population totale.

# Remarque

La partition n'est pas une propriété intrinsèque des données mais un choix de modélisation : le même attribut peut servir de descripteur dans une analyse et de cible dans une autre. Ce choix précède la recherche, car il fixe l'espace dans lequel les descriptions sont construites (voir [[Tâche de découverte de sous-groupes]]).

Quand plusieurs attributs cibles coexistent, la comparaison entre le sous-groupe et les données complètes porte sur un modèle et non sur une valeur isolée, cas traité dans la [[Découverte de modèles exceptionnels]].
