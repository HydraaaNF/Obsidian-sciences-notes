#ml-3

# Définition

Le **masque causal** est une matrice $M$, de même forme que les scores d'attention, ajoutée à ces scores avant le softmax. Ses coefficients valent $0$ aux positions autorisées et $-\infty$ aux positions interdites :

$$M_{ij} = \begin{cases} 0 & \text{si } j \le i \\ -\infty & \text{si } j > i \end{cases}$$

Le token $i$ ne peut donc prêter attention qu'aux tokens $1, \dots, i$ : il ne lit jamais les tokens futurs $j > i$. Dans un décodeur, $Q$, $K$ et $V$ sont les projections d'une même séquence, c'est la [[Self-attention]], et le masque la rend causale.

# Modèle

L'[[Attention à produit scalaire normalisé]] reçoit ici un terme correctif ajouté aux scores, avant la normalisation. L'attention masquée s'écrit :

$$\operatorname{softmax}\left(\frac{QK^\top}{\sqrt{d_k}} + M\right)V$$

Le calcul enchaîne les opérations suivantes.

- `MatMul` entre $Q$ et $K^\top$ ;
- `Scale`, division par $\sqrt{d_k}$ ;
- `Mask`, ajout de $M$ ;
- `SoftMax` sur chaque ligne ;
- `MatMul` avec $V$.

Pour une séquence de quatre tokens de dimension $128$, $Q$ est de forme $[4, 128]$, $K^\top$ de forme $[128, 4]$ et $M$ de forme $[4, 4]$. Le masque complet s'écrit :

$$M = \begin{pmatrix} 0 & -\infty & -\infty & -\infty \\ 0 & 0 & -\infty & -\infty \\ 0 & 0 & 0 & -\infty \\ 0 & 0 & 0 & 0 \end{pmatrix}$$

Les scores masqués ont alors la forme triangulaire suivante :

$$\frac{QK^\top}{\sqrt{d_k}} + M = \begin{pmatrix} q_1 \cdot k_1 & -\infty & -\infty & -\infty \\ q_2 \cdot k_1 & q_2 \cdot k_2 & -\infty & -\infty \\ q_3 \cdot k_1 & q_3 \cdot k_2 & q_3 \cdot k_3 & -\infty \\ q_4 \cdot k_1 & q_4 \cdot k_2 & q_4 \cdot k_3 & q_4 \cdot k_4 \end{pmatrix}$$

Le softmax s'applique ligne par ligne. Comme $e^{-\infty} = 0$, les positions futures reçoivent un poids nul et chaque ligne somme encore à $1$ :

$$A = \operatorname{softmax}\left(\frac{QK^\top}{\sqrt{d_k}} + M\right)$$

$$A = \begin{pmatrix} 1 & 0 & 0 & 0 \\ 0{,}4 & 0{,}6 & 0 & 0 \\ 0{,}1 & 0{,}3 & 0{,}6 & 0 \\ 0{,}2 & 0{,}1 & 0{,}3 & 0{,}4 \end{pmatrix}$$

# Exemple

La traduction de « Le petit chat » vers « The little cat » montre le rôle du masque. Le décodeur a déjà produit le préfixe « The little » et doit maintenant produire « cat ». Trois panneaux se lisent ainsi.

| Panneau | Rôle | Contenu |
| --- | --- | --- |
| vert | entrée source, lue par l'encodeur | Le · petit · chat |
| orange | préfixe déjà généré par le décodeur | The · little |
| bleu | cible complète attendue | The · little · cat |

Pour prédire « cat », le décodeur ne doit voir que les positions déjà produites, « The » et « little » ; la position de « cat » dans la cible reste masquée. Cinq flèches partent des cinq jetons du bas, l'entrée source et le préfixe, et convergent vers « cat », le seul jeton de la cible encore à produire. Le décodeur combine ainsi l'information de la source et celle du préfixe pour produire le token suivant.

# Interprétation

Le masque traduit l'ordre temporel de la génération : au moment de produire le token $i+1$, le modèle ne dispose que des tokens $1, \dots, i$. Sans masque, le produit $q_1 \cdot k_2$ donnerait au token $1$ directement la réponse qu'il doit produire, et l'entraînement n'apprendrait rien.

À l'entraînement, la séquence entière est traitée en une seule passe. Le masque rend cette passe parallèle sans casser la causalité : chaque position ne voit que son passé.

# Propriétés

Après le softmax masqué, $A$ est triangulaire inférieure, avec des zéros au-dessus de la diagonale, et chaque ligne somme à $1$ :

- la première ligne vaut $1, 0, 0, 0$ ;
- la deuxième vaut $0{,}4, 0{,}6, 0, 0$ ;
- la troisième vaut $0{,}1, 0{,}3, 0{,}6, 0$ ;
- la quatrième vaut $0{,}2, 0{,}1, 0{,}3, 0{,}4$.

Le résultat $V' = AV$ ne mélange donc, pour chaque token, que les valeurs de son passé :

$$V' = AV$$

$$v'_i = \sum_{j \le i} a_{ij} v_j$$

La ligne $i$ sert à prédire le token $i+1$, et les quatre prédictions sont calculées en une seule passe, chacune causale.

| Vecteur | Prédiction |
| --- | --- |
| $v'_1$ | token 2 |
| $v'_2$ | token 3 |
| $v'_3$ | token 4 |
| $v'_4$ | token 5 |

# Remarque

- L'ordre des étapes est parfois donné comme `MatMul` → `SoftMax` → `Mask` → `Scale` → `MatMul` ; la version retenue ici est `MatMul` → `Scale` → `Mask` → `SoftMax` → `MatMul`, cohérente avec un masque additif posé sur les scores avant normalisation.
- Sur la matrice illustrée, seules les $-\infty$ de la première ligne étaient représentées, les lignes suivantes montrant des produits calculés pour des jetons futurs ; le masque est ici complété sur toutes les lignes, et toutes les positions $j > i$ y valent $-\infty$.
- Les flèches de l'exemple partent aussi des jetons de la source : elles illustrent une [[Architecture du Transformer|attention croisée]], c'est-à-dire l'apport de l'entrée, et non le seul masque causal qui régit la self-attention du décodeur.
