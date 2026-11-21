#ml-1

# Définition

Les champs liés à l'apprentissage automatique, ou [[Machine Learning|machine learning]], forment un ensemble de disciplines voisines :

- l'apprentissage automatique
- les statistiques
- le [[Fouille de données et visualisation|data mining]]
- la data science
- le big data

# Interprétation

Les liens entre ces champs se lisent sur le schéma suivant :

- l'apprentissage automatique est relié aux statistiques et au data mining
- les statistiques sont reliées à la data science
- le data mining et la data science sont tous deux reliés au big data

```mermaid
flowchart TD
    ML["Apprentissage automatique"]
    Stat["Statistiques"]
    DM["Data mining"]
    DS["Data science"]
    BD["Big data"]

    ML --- Stat
    ML --- DM
    Stat --- DS
    DM --- BD
    DS --- BD
```

Le big data occupe une position de jonction : il est le seul champ relié à la fois au data mining et à la data science, sans lien direct avec l'apprentissage automatique ni avec les statistiques.

# Remarque

La [[Modélisation statistique et apprentissage automatique|modélisation statistique]] est un sous-ensemble de l'apprentissage automatique, qui l'englobe : le cadre statistique restreint l'exploration à un type particulier de fonctions et se ramène à l'estimation de densité.
