# Définition
La **logique floue** (*fuzzy logic*), fondée sur la **théorie des ensembles flous**, a été proposée par **Lotfi Zadeh en 1965**.

Idée clé : représenter des **classes d'éléments dont les frontières sont vagues**, ce qui permet de modéliser de nombreux termes du langage naturel (*température élevée*, *prix abordable*, *couleur claire*, …). Sa notion centrale est l'[[Ensemble flou]].

# Exemple
**Le concept « jeune »** (*young*). Deux modèles du même concept :
- **modèle booléen** : $f_{\text{young}}(x) = 1$ si $x < 30$, $0$ sinon ;
- **modèle flou** : $\mu_{\text{young}} : [0, 150] \to [0, 1]$, égale à $1$ jusqu'à $30$ ans, puis décroissant linéairement jusqu'à $0$ à $45$ ans (voir [[Fonction d'appartenance trapézoïdale]]).

```chart
type: line
labels: ["0", "2.5", "5", "7.5", "10", "12.5", "15", "17.5", "20", "22.5", "25", "27.5", "30", "32.5", "35", "37.5", "40", "42.5", "45", "47.5", "50", "52.5", "55", "57.5", "60"]
series:
  - title: Booléen (seuil 30)
    data: [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0]
  - title: Flou (30 à 45)
    data: [1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0.83, 0.67, 0.5, 0.33, 0.17, 0, 0, 0, 0, 0, 0, 0]
beginAtZero: true
```

# Remarque
Domaines d'application :
- traitement d'images ;
- classification, *clustering* ;
- analyse de données ;
- bases de données (voir [[Approche quantitative des préférences]]) ;
- aide à la décision.
