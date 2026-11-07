#ml-1

# Propriétés

Dans un espace de [[Plongement|plongements]], les **différences entre vecteurs** encodent des relations : une même relation correspond à un même déplacement.

$$e_{\text{king}} - e_{\text{man}} + e_{\text{woman}} \approx e_{\text{queen}}$$

Le déplacement qui mène de $e_{\text{man}}$ à $e_{\text{woman}}$, ajouté à $e_{\text{king}}$, donne ainsi $e_{\text{queen}}$.

# Exemple

La régularité se vérifie sur plusieurs familles de relations.

Relation de genre, du masculin vers le féminin :

- king → queen
- man → woman

Temps verbal, de la forme simple vers le passé :

- walking → walked
- swimming → swam

Pays vers capitale :

- Spain → Madrid
- Italy → Rome
- Germany → Berlin
- Turkey → Ankara
- Russia → Moscow
- Canada → Ottawa
- Japan → Tokyo
- Vietnam → Hanoi
- China → Beijing

# Remarque

Ces directions n'ont pas été demandées explicitement : elles émergent de l'objectif d'entraînement, qui consiste à prédire le contexte d'un mot ([[word2vec]]).

Attention : le vecteur le plus proche de $e_{\text{king}} - e_{\text{man}} + e_{\text{woman}}$ est souvent $e_{\text{king}}$ lui-même ; par convention, on exclut de la recherche le mot de départ.
