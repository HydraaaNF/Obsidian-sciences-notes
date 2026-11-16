#dmv-subgroup_discovery

# Définition

Une fonction de qualité est une application qui associe à chaque motif de sous-groupe une valeur réelle :

$$q: \text{espace des motifs} \rightarrow \mathbb{R}$$

La valeur $q(P)$ chiffre l'intérêt du sous-groupe décrit par le motif $P$ : c'est la mesure d'intérêt au moyen de laquelle la [[Tâche de découverte de sous-groupes|tâche de découverte de sous-groupes]] compare et ordonne les [[Motif de sous-groupe|motifs]] candidats.

Pour une cible binaire, la plupart des fonctions de qualité reposent sur la [[Matrice de confusion d'un sous-groupe|matrice de confusion]] du sous-groupe, qui croise l'appartenance au sous-groupe et la vérité de la cible.

# Remarque

De nombreuses mesures sont possibles, et c'est la fonction de qualité retenue qui départage les sous-groupes : deux mesures différentes ne conduisent pas aux mêmes sous-groupes les plus intéressants.

Une fonction de qualité construite sur la matrice de confusion se particularise en [[Exactitude relative pondérée]] pour la cible binaire ; pour une cible numérique, les pourcentages de présence cèdent la place à la moyenne de la cible et la même forme de fonction se retrouve dans la [[Fonction de qualité pour cible numérique]].
