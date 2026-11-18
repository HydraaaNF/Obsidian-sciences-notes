#dmv-xai

# Définition

Une **explication globale** rend compte de « all possible outcomes of the black box » : elle couvre l'ensemble des sorties possibles de la boîte noire, et non une prédiction isolée. Elle se définit par sa portée, et non par la méthode qui la produit.

# Interprétation

L'explication globale et l'[[Explication locale]] ne portent pas sur le même objet.

- une explication locale justifie une sortie pour une instance donnée
- une explication globale décrit le comportement du modèle sur la population entière, donc pour toutes les instances que la boîte noire peut rencontrer

Le point de départ reste le même dans les deux cas : un jeu de données étiquetées sert à apprendre la boîte noire, dont on ne voit que les entrées et les sorties. Une première voie d'obtention est l'**ingénierie inverse** (*reverse engineering*) : la boîte noire est reprise comme source de données pour un classifieur interprétable, qui est ensuite présenté à l'utilisateur.

```mermaid
flowchart LR
    A["Données étiquetées"] --> B["Phase d'apprentissage"]
    B --> C["Boîte noire"]
    C --> D["Ingénierie inverse"]
    D --> E["Classifieur interprétable"]
    E --> F["Utilisateur"]
```

Suivant cette voie, le substitut interprétable est le modèle effectivement lu par l'utilisateur.

Une autre voie consiste à combiner des explications locales calculées sur de nombreuses instances : l'explication globale est alors agrégée à partir de ces explications locales, sans substitut.

# Remarque

Les familles de méthodes globales se répartissent selon la forme du substitut ou du résumé produit.

- les courbes de dépendance partielle, qui tracent l'effet moyen d'une variable sur la prédiction : [[Graphique de dépendance partielle]]
- l'importance des variables, obtenue en agrégeant des explications locales sur de nombreuses instances : [[Importance des variables par agrégation]]
- les substituts globaux lisibles, arbre de décision ou ensemble de règles appris sur les entrées et sorties de la boîte noire : [[Substituts globaux par arbre et par règles]]
- les contrefactuels globaux, qui décrivent les modifications d'entrée valables pour des groupes d'instances : [[Contrefactuels globaux]]

Une explication globale ne se lit pas comme le commentaire d'une ligne du jeu de données : elle s'apprécie sur la population, et sa lecture reste agrégée même lorsque la méthode sous-jacente part d'explications locales.

La [[Taxonomie des techniques d'explicabilité]] situe ces familles parmi les techniques produites après coup, selon leur portée et leur mode de calcul.
