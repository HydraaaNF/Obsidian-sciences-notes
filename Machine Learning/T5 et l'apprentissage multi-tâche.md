#ml-3

# Modèle

**T5** est un modèle encodeur-décodeur **multi-tâche** : un même modèle traite plusieurs tâches simultanément, sans architecture ni tête spécialisée par tâche.

Chaque exemple est formulé comme une conversion texte vers texte : l'entrée est une phrase dont certains fragments sont remplacés par des masques `<M>`, et la sortie attendue est le texte complété, y compris les masques des fragments qui restent à produire.

Cette formulation ramène toutes les tâches à une seule forme, ce qui rattache le modèle à l'[[Apprentissage multi-tâches]] et en fait une instance encodeur-décodeur des [[Variantes du Transformer]], bâtie sur l'[[Architecture du Transformer]].

# Exemple

## Pré-entraînement

Le même modèle traite les trois conversions suivantes en parallèle.

| Entrée | Sortie |
|---|---|
| `President Franklin <M> born <M> January 1882.` | `D. Roosevelt was <M> in` |
| `Lily couldn't <M>. The waitress had brought the largest <M> of chocolate cake <M> seen.` | `believe her eyes <M> piece <M> she had ever` |
| `Our <M> hand-picked and sun-dried <M> orchard in Georgia.` | `peaches are <M> at our` |

Les trois entrées convergent vers le module central T5, qui produit les sorties correspondantes.

La réponse cible complète de la première conversion est `President Franklin D. Roosevelt was born in January 1882.`

## Fine-tuning

Le modèle pré-entraîné est ensuite adapté de façon supervisée à une tâche de question-réponse, formulée elle aussi en texte vers texte :

- entrée : `When was Franklin D. Roosevelt born?`
- modèle : T5
- sortie : `1882`

La frontière en pointillés sépare la phase de pré-entraînement multi-tâches de la phase d'adaptation supervisée.

# Remarque

Le pré-entraînement couvre plusieurs tâches à la fois, alors que l'adaptation supervisée ne porte que sur la tâche cible : les mêmes paramètres sont réutilisés d'une phase à l'autre.

- T5 est une instance encodeur-décodeur qui emploie les trois attentions, dont l'[[Architecture du Transformer|attention croisée]] entre encodeur et décodeur.
