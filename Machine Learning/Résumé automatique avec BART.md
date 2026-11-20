#ml-3

# Modèle

**BART** est un modèle encodeur-décodeur de 2020 employé pour le résumé automatique : il reçoit un texte et produit un texte plus court qui en conserve l'essentiel.

Il appartient à la famille des [[Variantes du Transformer|Transformers encodeur-décodeur]] : l'encodeur lit le texte source et le décodeur engendre le résumé, selon le schéma général de [[Encodeur-décodeur pour les séquences|génération d'une séquence par encodeur-décodeur]]. [[T5 et l'apprentissage multi-tâche|T5]] est l'autre modèle encodeur-décodeur usuel, mais il ramène toutes ses tâches à une conversion texte vers texte.

# Exemple

## Texte à résumer

> The tower is 324 metres (1,063 ft) tall, about the same height as an 80-storey building, and the tallest structure in Paris. Its base is square, measuring 125 metres (410 ft) on each side. During its construction, the Eiffel Tower surpassed the Washington Monument to become the tallest man-made structure in the world, a title it held for 41 years until the Chrysler Building in New York City was finished in 1930. It was the first structure to reach a height of 300 metres. Due to the addition of a broadcasting aerial at the top of the tower in 1957, it is now taller than the Chrysler Building by 5.2 metres (17 ft). Excluding transmitters, the Eiffel Tower is the second tallest free-standing structure in France after the Millau Viaduct.

## Résumé produit

> The tower is 324 metres (1,063 ft) tall, about the same height as an 80-storey building. Its base is square, measuring 125 metres (410 ft) on each side. Excluding transmitters, the Eiffel Tower is the second tallest free-standing structure in France.

Six phrases deviennent trois, et le résumé conserve la hauteur, la forme de la base et le rang de la tour parmi les structures françaises.

# Remarque

Le résumé reste essentiellement **extractif** : ses trois phrases sont reprises presque mot pour mot de l'entrée, avec seulement quelques troncations, sans reformulation. Il n'illustre donc pas un résumé abstractif, qui réécrirait le contenu avec ses propres mots.

## Pertes d'information

La compression écarte plusieurs informations du texte d'entrée :

- le titre de plus haute structure de Paris, retiré de la première phrase
- le record de la tour, qui dépasse le Washington Monument puis conserve le titre pendant 41 ans, jusqu'à l'achèvement du Chrysler Building en 1930
- le seuil des 300 mètres, que la tour est la première à franchir
- l'antenne de radiodiffusion ajoutée en 1957, qui la place 5,2 mètres au-dessus du Chrysler Building
- le viaduc de Millau, référence de la deuxième structure autoportante de France

Aucune de ces informations n'est remplacée par une formulation plus générale : elles disparaissent simplement du résumé.
