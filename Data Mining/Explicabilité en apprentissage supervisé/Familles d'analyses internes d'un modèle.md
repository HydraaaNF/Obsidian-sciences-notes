#dmv-xai

# Définition

Certaines approches d'[[Explicabilité]] ne fonctionnent que pour les réseaux de neurones. Les familles attributionnelle, conceptuelle et mécaniste expliquent le modèle en analysant ce qu'il calcule à l'intérieur, poids, activations, neurones et couches ; la famille comportementale, elle, ne considère que la relation entre ses entrées et sa sortie.

Ces analyses internes se rangent en quatre familles : comportementale, attributionnelle, conceptuelle et mécaniste.

# Modèle

| Famille | Ce qui est lu |
|---|---|
| Comportementale | relations entrées-sorties $f(\bullet) = \bigstar$ et $f(\blacktriangle, \bullet) = \bigstar$ |
| Attributionnelle | gradients de la sortie par rapport aux entrées, $\frac{\partial \bigstar}{\partial \blacktriangle} = 1$ et $\frac{\partial \bigstar}{\partial \bullet} = 2$ |
| Conceptuelle | sondes (probes) |
| Mécaniste | mécanisme $\bigstar + \blacktriangle = \triangle$ et $\triangle + \bullet = \bigstar$ |

Les symboles désignent deux entrées, $\blacktriangle$ et $\bullet$, et la sortie $\bigstar$.

# Propriétés

- Une analyse interne est soit observationnelle, soit interventionnelle.
- Seules les interventions permettent d'établir une causalité.

Techniques observationnelles :

- Structured Probes
- Logit Lens
- Sparse Autoencoder

Techniques interventionnelles :

- Activation Patching
- Attribution Patching
- Causal Scrubbing

# Interprétation

L'analyse mécaniste vise l'interprétabilité mécaniste : appliquer des techniques de rétro-ingénierie aux réseaux de neurones pour en extraire des actifs interprétables par l'humain.

Ce que l'analyse permet de lire dépend de la profondeur : les couches proches des données portent des motifs de bas niveau, et les actifs extraits deviennent des concepts de plus en plus abstraits à mesure que l'on avance vers la sortie.

# Exemple

Lecture couche par couche d'un réseau de reconnaissance d'image, de l'image d'entrée jusqu'à la prédiction « chat ».

| Étage | Actif interprétable |
|---|---|
| Couche 1 | contours, orientations |
| Couche 2 | coins, textures |
| Couche 3 | parties : oreilles, yeux, moustaches |
| Couche 4 | concept d'objet : tête de chat, corps de chat |
| Sortie | prédiction : chat, chat ou pas chat |

Le parcours va du bas niveau, proche des données, au haut niveau, plus abstrait.

# Remarque

La [[Taxonomie des techniques d'explicabilité]] range l'examen direct des réponses du modèle parmi les techniques d'inspection ; les familles décrites ici précisent ce que cet examen lit.

La famille attributionnelle rejoint les [[Méthodes d'attribution par gradients]], et la famille conceptuelle les [[Explications par concepts et prototypes]]. La famille mécaniste suppose connue l'[[Architectures et représentations des réseaux|architecture en couches]] du réseau analysé.

Une analyse seulement observationnelle ne suffit pas à conclure à une causalité : cette conclusion demande une intervention.
