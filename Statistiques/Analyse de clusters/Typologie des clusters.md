# Définition
Au-delà du critère général de similarité intra/inter-classe, plusieurs définitions plus précises d'un cluster coexistent :

- **cluster bien séparé** : chaque point du cluster est plus proche de tout point du cluster que de tout point extérieur
- **cluster centré** : chaque point du cluster est plus proche du centre de son cluster que du centre de tout autre cluster
- **cluster contigu** : chaque point du cluster est plus proche d'au moins un point du cluster que de tout point d'un autre cluster
- **cluster basé sur la densité** : région dense de points, séparée des autres clusters par des régions de faible densité

# Interprétation
Ces définitions ne coïncident pas nécessairement : un même jeu de données peut admettre des clusterings très différents selon la définition retenue. Voir [[DBSCAN]] pour une méthode fondée explicitement sur la densité.
