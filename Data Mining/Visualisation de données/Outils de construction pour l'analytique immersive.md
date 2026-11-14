#dmv-visualization

# Propriétés

Deux voies de prototypage s'opposent pour construire une visualisation immersive :

- le prototypage par interface graphique est facile à apprendre et à utiliser, mais reste plus templaté ;
- le prototypage par grammaire demande d'apprendre la grammaire, mais offre plus de flexibilité.

# Exemple

Une spécification déclarative décrit la scène au lieu de la dessiner : largeur, profondeur et hauteur du volume d'affichage, source des données, marque employée, puis, pour chaque variable, le canal qui la porte, son type et son échelle.

```
{
  "width": 15240, "depth": 14330, "height": 2000,
  "data": { "url": "basketball.csv" },
  "mark": "bar",
  "encoding": {
    "x":     { "field": "X",   "type": "quantitative" },
    "z":     { "field": "Z",   "type": "quantitative" },
    "color": { "field": "FGA", "type": "quantitative",
               "scale": { "type": "sequential",
                          "domain": [0, 50, 100] } },
    "y":     { "field": "FGA", "type": "quantitative",
               "scale": { "domain": [0, 100] } },
    "height": { "field": "FGA", "type": "quantitative" }
  }
}
```

La même variable sert ici de couleur, de position et de hauteur : les canaux se combinent sans que la figure soit redessinée à la main.

# Remarque

L'outillage conditionne ce qui peut être construit, et sa souplesse fait partie des [[Défis de recherche de l'analytique immersive]].
Ces outils servent les applications d'[[Analytique immersive]], par exemple un cube espace-temps comme [[GeoGate, cube espace-temps en réalité augmentée]].
