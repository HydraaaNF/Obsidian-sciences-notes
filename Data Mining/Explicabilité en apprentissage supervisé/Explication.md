#dmv-xai

# Définition

Une explication est un énoncé qui caractérise les relations entre les entrées et les sorties d'un modèle d'intelligence artificielle : « a statement that characterizes the **(causal?)** relationships between the inputs and outputs of an AI model ».

# Remarque

Le point d'interrogation marque que la causalité n'est qu'une hypothèse : une explication peut se contenter de décrire une relation statistique entre les variables d'entrée et la prédiction, sans établir que la variation de l'entrée est la cause de la sortie. La relation décrite est donc causale lorsqu'elle est établie, seulement corrélationnelle sinon, et une formulation plus neutre se passe de toute mention de causalité pour ne retenir que les relations entre entrées et sorties.

Une explication se produit parce qu'elle est attendue : les [[Motivations de l'explicabilité]] en donnent les raisons, réglementaires, économiques ou de confiance.

# Exemple

Un système d'aide au choix de cours explique la note prédite pour un cours donné. Pour un étudiant du cours BUSINESS MANAGEMENT, l'explication détaille la contribution de chaque variable :

- « taking this course for the first time » a une forte contribution positive sur la note prédite
- « your grade in Communication II » a une faible contribution positive
- la difficulté totale des cours du semestre, mesurée par l'estimateur alpha, a une contribution négative médiane
- « the number of times you took Communication II » a une faible contribution négative

```chart
type: pie
labels: ["Contribution positive 55 %", "Contribution négative 25 %", "Contribution négative 11 %", "Contribution positive 10 %"]
series:
  - title: Contributions
    data: [55, 25, 11, 10]
```

Les contributions positives figurent en vert, les négatives en rouge : l'explication se lit comme une décomposition chiffrée de la prédiction. Les quatre pourcentages affichés totalisent 101 %, leur somme n'étant pas normalisée à 100 %, et les valeurs sont reprises telles quelles.

L'explication ne prend pas toujours la forme d'une décomposition de contributions. Selon la modalité des données, elle se présente aussi comme :

- un texte dont certains mots sont surlignés, par exemple « Salem », « theories » et « science » dans un message
- une réponse à une question sur une image : « What is the man doing? » donne « Surfing », « What is she holding? » donne « Baseball bat »
- un chemin dans un graphe de connaissances : la requête `(Kelly, Nationality, ?)` reçoit la réponse « Scotland », les arêtes étant masquées selon une échelle de 1.00 à 0.00

Ces formes sont détaillées dans [[Formes d'explication selon la modalité des données]] ; chacune relève d'une famille de méthodes, de [[LIME]] aux méthodes d'attribution, que classe la [[Taxonomie des techniques d'explicabilité]].

# Interprétation

Une explication est l'énoncé produit, tandis que l'[[Explicabilité]] est la capacité d'un modèle à être expliqué et que l'[[Interprétabilité]] est la propriété de sa représentation d'être comprise directement. Un modèle interprétable livre ses explications par sa forme même ; un modèle opaque exige une méthode dédiée pour produire l'énoncé qui caractérise ses relations entre entrées et sorties.
