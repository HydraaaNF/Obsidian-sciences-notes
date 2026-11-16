#dmv-subgroup_discovery

# Définition

La [[Découverte de modèles exceptionnels|découverte de modèles exceptionnels]] prend pour paramètre important une **classe de modèle** sur les attributs cibles : modèle linéaire, processus gaussien, conjonction de valeurs, entre autres.

Deux modèles de cette classe sont ajustés :

- un modèle est inféré sur l'ensemble des données ;
- un modèle est inféré sur le sous-groupe seul.

Le modèle du sous-groupe est un **modèle exceptionnel** s'il diffère significativement du modèle inféré sur toutes les données.

# Interprétation

L'objet comparé n'est pas une valeur isolée de la cible mais le modèle qui la décrit : le sous-groupe est intéressant lorsque la relation elle-même change d'allure à l'intérieur du sous-groupe, et non seulement lorsque le niveau moyen de la cible s'y déplace.

Une classe de modèle fixe la forme de la relation étudiée sur les attributs cibles, et non ses valeurs : la classe dit quelle famille de relations est testée, puis un modèle de cette classe est ajusté sur les données.

Le modèle inféré sur toutes les données sert de référence : il résume le comportement ordinaire des attributs cibles, et l'écart du modèle de sous-groupe à cette référence est ce qui rend le sous-groupe exceptionnel.

Le choix de la classe de modèle commande donc l'analyse : la même classe appliquée aux mêmes données désigne un type de relation à tester, et un sous-groupe peut être exceptionnel pour une classe et banal pour une autre.

# Exemple

**Conjonction de littéraux sur la présence d'animaux.** La classe de modèle est la conjonction de littéraux et les attributs cibles sont la présence ou l'absence d'animaux.

Le sous-groupe est décrit par la conjonction de trois littéraux sur les températures maximales :

- température maximale en septembre $\le 11{,}1$ °C ;
- température maximale en avril $\le 3{,}47$ °C ;
- température maximale en novembre $\ge -2{,}56$ °C.

Le modèle exceptionnel associé est la conjonction de quatre espèces qui apparaissent relativement souvent sous ce sous-groupe, comparées à l'ensemble de l'Europe :

- Arctic fox ;
- Skunk bear ;
- Norway lemming ;
- Elk.

**Relation linéaire entre deux cibles.** La classe de modèle est la relation linéaire et les attributs cibles sont $y_1$ et $y_2$. Les données se répartissent en trois groupes repérés par un attribut de description $x$, de valeurs $a$, $b$ et $c$.

Le modèle inféré sur toutes les données est croissant, d'équation $y_2 = 0{,}94\,y_1 + 0{,}04$. Les modèles inférés sur les sous-groupes ne suivent pas cette allure :

| données d'ajustement | relation linéaire obtenue |
|---|---|
| toutes les données | croissante, $y_2 = 0{,}94\,y_1 + 0{,}04$ |
| sous-groupe $x(i) = b$ | décroissante |
| sous-groupe $x(i) = c$ | décroissante, avec une ordonnée à l'origine nettement plus élevée |

Les deux modèles de sous-groupes s'écartent donc fortement du modèle global : la relation passe de croissante sur l'ensemble des données à décroissante à l'intérieur de chacun des deux sous-groupes. Les points ne se répartissent pas non plus de la même façon selon le groupe : ceux du groupe $x(i) = b$ se massent dans la zone des faibles valeurs de $y_1$ et de $y_2$, ceux du groupe $x(i) = c$ dans celle des valeurs élevées, tandis que ceux du groupe $x(i) = a$ couvrent tout le plan.

# Remarque

Le modèle est ajusté sur les seuls [[Attributs de description et attributs cibles|attributs cibles]] ; la condition qui définit le sous-groupe porte, elle, uniquement sur les attributs de description, et se lit comme un [[Motif de sous-groupe]].

Une classe de modèle qui relie plusieurs attributs cibles à la fois permet de traiter le cas des cibles multiples : la comparaison porte alors sur tout un modèle au lieu de se faire cible par cible.

La différence entre les deux modèles doit être **significative** : une simple fluctuation d'ajustement ne suffit pas à déclarer le modèle du sous-groupe exceptionnel. Le choix de la classe de modèle commande donc ce qui est comparé, et seul un écart significatif à la référence fait d'un sous-groupe un modèle exceptionnel.
