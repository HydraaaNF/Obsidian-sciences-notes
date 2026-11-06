# Modèle

Un problème de prédiction met en regard des observations $X$ et une sortie $Y$ à prédire. Deux familles de modèles graphiques s'en chargent :

- un **modèle génératif** décrit la loi jointe $\mathbb{P}[X, Y]$ : les observations et la sortie y sont des variables aléatoires, engendrées par le modèle ;
- un **modèle conditionnel** décrit directement la loi conditionnelle $\mathbb{P}[Y \mid X]$ : les observations $X$ y sont toujours données et seule la sortie $Y$ est modélisée.

# Interprétation

Le bestiaire des modèles range les deux familles sur deux lignes, chacune parcourant les mêmes trois degrés de complexité.

| Famille | Modèle simple | Modèle séquentiel | Modèle général |
| --- | --- | --- | --- |
| Génératif | [[Classifieur naïf de Bayes]] | [[Modèle de Markov caché]] | modèles dirigés génératifs |
| Conditionnel | régression logistique | CRF à chaîne linéaire | CRF généraux |

Les CRF sont les champs aléatoires conditionnels.

De gauche à droite, la structure s'enrichit :

- premier degré : une sortie unique reliée à quelques observations, sans dépendance entre celles-ci ;
- deuxième degré : les observations forment une séquence et chaque observation est attachée à un état d'une chaîne (flèche SEQUENCE) ;
- troisième degré : observations et sorties sont reliées par un graphe quelconque (flèche GENERAL GRAPHS).

D'une ligne à l'autre, la structure du graphe se conserve et seule la loi décrite change :

- la ligne générative est faite de graphes dirigés, où les observations sont engendrées par les variables du modèle ; au troisième degré, une observation peut à son tour en engendrer une autre ;
- la ligne conditionnelle est faite de graphes de facteurs, sans direction, où les observations sont toujours présentes ; l'étiquette CONDITIONAL marque que seul le conditionnement sur ces observations est modélisé.

Le bestiaire se lit ainsi en correspondance terme à terme : le classifieur naïf de Bayes a pour homologue conditionnel la régression logistique, le modèle de Markov caché le CRF à chaîne linéaire, et les modèles dirigés génératifs les CRF généraux.

# Remarque

La ligne générative est constituée de [[Réseau bayésien|réseaux bayésiens]] et la ligne conditionnelle de [[Graphe de facteurs|graphes de facteurs]] : la première porte des flèches, la seconde des facteurs.

Le choix entre les deux familles est un compromis :

- le génératif décrit aussi la loi des observations $\mathbb{P}[X]$, ce qui est coûteux lorsque les observations sont de grande dimension, mais permet d'engendrer des données ;
- le conditionnel n'en décrit pas la loi et concentre l'effort sur $\mathbb{P}[Y \mid X]$.

Le [[Champ de Markov caché]] diffère des CRF de la ligne conditionnelle : il modélise la loi jointe d'un champ caché et de ses observations, alors qu'un CRF conditionne sur les observations.
