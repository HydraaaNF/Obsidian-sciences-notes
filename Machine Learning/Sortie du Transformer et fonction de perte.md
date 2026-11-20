#ml-3

# Modèle

Trois questions fixent la sortie du Transformer et l'objectif de son entraînement.

- Que renvoie le modèle ? La probabilité de chaque jeton suivant possible du vocabulaire.
- Quelle tâche résout-il ? Une tâche de classification.
- Quelle perte en découle ? L'entropie croisée.

La couche `Linear` produit un score par jeton du vocabulaire, puis le [[Fonction softmax|softmax]] normalise ces scores en probabilités, affichées en `Output Probabilities` à la sortie du décodeur. Chaque jeton du vocabulaire tient ainsi le rôle d'une classe, ce qui fait de la prédiction du jeton suivant une classification et fixe la perte à l'[[Entropie croisée multi-classe|entropie croisée]]. La place de cette tête de sortie dans le réseau est décrite dans [[Architecture du Transformer]].

# Exemple

La traduction de « Le petit chat » en « The little cat » se lit sur les jetons, voir [[Tokenisation]].

| Rôle | Jetons |
| :--- | :--- |
| Entrée | `Le` · `petit` · `chat` · début de séquence · `The` · `little` |
| Sortie attendue | `The` · `little` · `cat` |

La source ouvre l'entrée, puis vient le début de la traduction décalé d'un pas vers la droite : la cible complète est fournie moins son dernier jeton, et le modèle doit produire cette cible. Chaque probabilité de sortie porte donc sur un jeton du vocabulaire, et le jeton attendu à une position y est la classe correcte.
