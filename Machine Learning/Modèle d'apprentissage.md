#ml-1

# Modèle

Un **modèle** est une famille de fonctions $\mathcal{F}$ accompagnée d'une valeur donnée à ses paramètres. La famille décrit la forme des fonctions considérées, et les valeurs des paramètres désignent une fonction précise à l'intérieur de cette famille.

La famille peut être décrite par sa version paramétrique, par exemple $a \times x + b$, ou par un graphe d'opérations. Le choix des valeurs, par exemple $a = -1$ ou $a = 4$, fixe alors une fonction particulière : la famille de fonctions et les valeurs des paramètres, réunies, forment le modèle.

Apprendre consiste à chercher, dans l'[[Espace d'hypothèses|espace d'hypothèses]] $\mathcal{F}$, la fonction qui ajuste au mieux les corrélations observées. Un algorithme recherche pour cela les meilleures valeurs de paramètres ; la qualité d'une fonction se mesure par une [[Fonction de perte]], sur laquelle se construit le [[Risque et risque empirique|risque]].

# Exemple

On cherche une fonction $f$ telle que $f(\text{Size}) = \text{Grey scale}$, sur l'exemple de la classification d'oiseaux selon leur taille.

Deux familles possibles :

- fonction linéaire : $\text{Grey scale} = a \times \text{Size} + b$, de paramètres $(a, b)$ ;
- fonction quadratique : $\text{Grey scale} = a \times \text{Size}^2 + b \times \text{Size} + c$, de paramètres $(a, b, c)$.

Choisir les valeurs de $(a, b)$ ou de $(a, b, c)$ donne un modèle concret dans la famille correspondante. L'apprentissage se fait en trouvant le meilleur couple $(a, b)$ ou le meilleur triplet $(a, b, c)$.

# Remarque

- Une formulation abrégée désigne comme modèle la seule fonction sélectionnée dans la famille. Elle reste compatible avec la définition complète dès lors que l'on garde en tête que cette sélection passe par le choix des valeurs de paramètres : deux fonctions d'une même famille ne diffèrent que par ces valeurs.
- Le type de tâche visé, [[Régression, classification et clustering|régression ou classification]], oriente la forme de la famille et la nature de la sortie de la fonction.
- La famille retenue borne l'ensemble des fonctions accessibles ; l'écart qui en résulte se lit dans l'[[Erreur d'approximation et erreur d'estimation|erreur d'approximation et erreur d'estimation]].
