# Définition
*Density-Based Spatial Clustering of Applications with Noise*. Méthode de [[Typologie des clusters|clustering basé sur la densité]] : repère les points densément connectés (analyse de voisinage), permet des clusters de forme arbitraire, robuste au bruit, un seul passage sur les données.

# Algorithme
1. **Étiqueter les points** :
   - **points cœurs** : suffisamment de points dans leur voisinage
   - **points de bordure** : pas assez de points autour, mais proches d'un point cœur
   - **points de bruit** : ni l'un ni l'autre
2. Éliminer les points de bruit
3. Créer les clusters à partir des points cœurs (recherche des composantes connexes du graphe de voisinage, par DFS ou BFS)
4. Assigner les points de bordure aux clusters cœurs correspondants

# Avantages / Inconvénients
**Avantages** : aucune hypothèse de convexité des clusters (formes et tailles arbitraires), gère le bruit (détecté comme points isolés), ne nécessite pas de fixer le nombre de clusters à l'avance

**Inconvénients** : sensible au choix des paramètres ($\varepsilon$ et nombre minimal de points), difficile à paramétrer quand les clusters ont des densités très différentes, nécessite une fonction de distance pertinente

# Remarque
DBSCAN est l'algorithme le plus connu de sa famille, mais d'autres méthodes par densité existent, notamment **OPTICS** (variante gérant mieux des densités variables) et **DENCLUE** (approche fondée sur l'estimation de densité par noyau — voir [[Estimation de densité par noyau]]).
