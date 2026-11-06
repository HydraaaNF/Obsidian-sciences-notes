# Définition
Variantes du [[k-means]] où le centre d'un cluster n'est plus la moyenne de ses membres mais :

- **k-médianes** : la médiane (composante par composante) des points du cluster
- **k-médoïdes** : le point du cluster (un membre réel des données, pas un point fictif) minimisant la somme des distances aux autres points du cluster

# Interprétation
Utile quand la moyenne n'a pas de sens pour la distance ou les données considérées (ex : données catégorielles, ou distance non euclidienne), ou pour limiter l'influence des valeurs aberrantes.
