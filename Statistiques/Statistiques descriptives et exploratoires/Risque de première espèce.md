# Définition

Dans un test d'hypothèses opposant une [[Hypothèse nulle et hypothèse alternative|hypothèse nulle]] $H_0$ à une hypothèse alternative $H_1$, la décision repose sur l'observation de la [[Moyenne empirique|moyenne empirique]] $\overline{X}$ : on conserve $H_0$ si cette observation appartient à un intervalle $\mathcal{D}$, et on rejette $H_0$ sinon. La probabilité de rejeter $H_0$ à tort est notée

$$\alpha = \mathbb{P}_{H_0} [\overline{X} \notin \mathcal{D}]$$

et appelée **risque de première espèce** ; l'ensemble complémentaire $\mathcal{D}^c$ de $\mathcal{D}$ est appelé **[[Zone critique et seuil d'un test|région critique]]** du test.

# Interprétation

L'erreur de décision correspondant au risque de première espèce est commise lorsque des mesures exceptionnelles conduisent à rejeter $H_0$ alors qu'elle est vraie : sous $H_0$, la probabilité que $\overline{X}$ ne soit pas dans $\mathcal{D}$ est seulement de $\alpha$, si bien que rejeter $H_0$ et accepter $H_1$ s'accompagne d'une probabilité $\alpha$ de se tromper en faisant ce choix.

# Remarque

Le risque de première espèce est l'un des deux risques d'erreur d'un test : il s'oppose au [[Risque de seconde espèce]], encouru lorsque l'on conserve $H_0$ à tort, et intervient dans la [[Puissance d'un test|puissance du test]].
