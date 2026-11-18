#dmv-pattern_mining_vs_deep_learning

# Remarque

Un [[Auto-encodeur de motifs]] doit satisfaire deux exigences contradictoires :

- pour des résultats interprétables, les poids doivent être binaires ;
- pour une optimisation correcte de la perte, les poids doivent être continus, donc différentiables.

Un poids binaire ne vaut que 0 ou 1 : la [[Couche de motifs]] se lit alors directement comme une collection d'itemsets, chaque neurone de motif sélectionnant les items qu'il contient. Un poids continu ne s'interprète plus comme une appartenance, mais il possède une dérivée, sans laquelle aucune [[Descente de gradient]] ne peut rétropropager l'erreur de reconstruction.

# Propriétés

Les deux espaces ne sont pas deux jeux de paramètres concurrents, mais deux rôles attribués au même réseau selon la passe :

- poids binaires lors de la **passe avant** : la couche de motifs définit les motifs et reconstruit les données à partir d'eux ;
- poids continus lors de la **passe arrière** : la perte est dérivée et les paramètres sont corrigés dans l'espace continu.

À la fin de la [[Rétropropagation]], les paramètres continus sont ramenés sur leurs versions binarisée et discrétisée, réutilisées à la reconstruction de l'itération suivante :

$$W \longrightarrow W_b$$

Le biais est discrétisé avec un maximum de $-1$, ce qui impose des motifs de taille supérieure à 1.

La matrice binaire $W_b$ joue les deux rôles de la couche : elle intervient transposée dans l'[[Encodage d'une transaction en motifs|encodage]] et telle quelle dans le [[Décodage d'une couche de motifs|décodage]].

# Interprétation

L'apprentissage tient dans cet aller-retour entre les deux espaces :

- l'espace binaire définit les motifs et reconstruit les données ;
- l'espace continu optimise la perte de reconstruction.

La [[Boucle d'apprentissage de l'auto-encodeur de motifs]] déroule cette alternance itération par itération. L'interprétabilité n'est donc pas un traitement appliqué après coup : la binarité est réappliquée à chaque itération, si bien que les motifs lus dans les poids sont ceux qui ont servi à reconstruire les données.

Le biais discrétisé ajoute une contrainte sur la taille des motifs : avec un maximum de $-1$, aucun motif d'un seul item n'est retenu, tous les motifs de la couche font au moins deux items.
