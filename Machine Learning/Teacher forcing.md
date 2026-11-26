#ml-1

# Définition

Le **teacher forcing** est la méthode d'entraînement d'un décodeur de séquence : le vrai élément précédent $y_{t-1}$ est fourni en entrée à chaque pas, à la place de la prédiction $\hat{y}_{t-1}$ produite par le modèle.

L'entrée est donc la séquence cible **décalée d'un pas vers la droite**.

# Exemple

Pour la séquence cible « the little cat » :

- entrée : $\langle s \rangle$, « the », « little », « cat »
- cible : « the », « little », « cat », $\langle /s \rangle$

Le symbole de début $\langle s \rangle$ occupe la première entrée, et le symbole de fin $\langle /s \rangle$ la dernière cible.

# Propriétés

- Chaque pas reçoit sa perte dans la même passe, comme dans le cas many-to-many.
- Une erreur commise tôt ne s'amplifie pas au fil des pas : les entrées suivantes restent les vrais éléments de la séquence.

# Remarque

À l'inférence, le vrai $y$ n'existe plus : le modèle lit ses propres prédictions, comme dans la [[Génération d'une séquence]]. Il n'a jamais vu ses propres erreurs pendant l'entraînement, si bien que celles-ci s'accumulent : c'est le **biais d'exposition**. Sur une projection à 36 mois, la prévision dérive progressivement loin des données.

Les Transformers s'entraînent de la même façon, avec des sorties décalées vers la droite, mais sans récurrence : tous les pas sont calculés en parallèle, et non l'un après l'autre.

- La [[Décomposition autorégressive d'une densité]] justifie l'entraînement position par position : chaque facteur conditionnel apporte sa perte dans la même passe.
- L'[[Inférence autorégressive]] contraste avec cet entraînement parallèle : la génération y est séquentielle, un échantillon à la fois.
- Le [[Pipeline Hugging Face]] applique ce décalage d'un token en passant `labels = input_ids`, le modèle réalisant le décalage en interne.
