# Définition
Dans l'**approche quantitative** d'une [[Requête à préférences|requête à préférences]], chaque préférence utilisateur est traduite par une **fonction de score monotone**. Un score global est obtenu en **agrégeant** les scores partiels de chaque critère.

# Propriétés
La relation de préférence se déduit du score :

$$
t_1 \succ t_2 \iff \operatorname{score}(t_1) \geq \operatorname{score}(t_2)
$$

où $\succ$ se lit « est préféré à ».

# Interprétation
Le score global fournit directement un **préordre total** sur les réponses : toutes les réponses sont comparables, mais des ex æquo sont possibles.

C'est l'approche retenue dans ce cours, et elle s'appuie sur la [[Logique floue]] : la [[Fonction d'appartenance]] d'un [[Ensemble flou]] joue le rôle de fonction de score. L'agrégation des critères est réalisée par une [[Norme triangulaire]], une [[Conorme triangulaire]] ou un [[Opérateur de compromis]].

# Remarque
À opposer à l'[[Approche qualitative des préférences]].
