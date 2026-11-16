#dmv-subgroup_discovery

# Définition

Un **motif de sous-groupe** est une règle de la forme :

$$s_1 \wedge s_2 \wedge \cdots \wedge s_k \Rightarrow \text{propriété sur le concept cible}$$

où chaque $s_i$ est un [[Sélecteur d'un motif de sous-groupe|sélecteur]], condition élémentaire portant sur un attribut.

# Modèle

Un motif se lit en deux parties.

La **description** est la conjonction de sélecteurs : elle désigne le sous-groupe, c'est-à-dire les individus qui satisfont tous ses sélecteurs.

La **propriété visée** porte sur le [[Attributs de description et attributs cibles|concept cible]] : elle n'énonce pas une valeur pour un individu, mais un comportement global du sous-groupe, comparé à celui de la population totale.

Le motif est donc une description évaluée, pas une règle de prédiction : c'est la [[Tâche de découverte de sous-groupes|tâche de découverte de sous-groupes]] qui le retient lorsqu'il s'écarte suffisamment du reste de la population, et c'est une [[Fonction de qualité d'un sous-groupe|fonction de qualité]] qui mesure cet écart.

# Interprétation

Le conséquent se lit toujours de façon comparative : le sous-groupe décrit a, pour l'attribut cible, une valeur ou une répartition plus marquée que la population entière, en proportion plus forte, en moyenne plus élevée, ou tout autre sens que fixe la fonction de qualité.

La conjonction, elle, joue le rôle d'un filtre : chaque sélecteur supplémentaire restreint le sous-groupe, donc son effectif, tandis que la propriété visée reste la même.

# Exemple

- **$Study = \text{‘Computer Science’}$** : la proportion de ‘Male’ y est plus élevée que dans la population étudiante.
- **$Sex = \text{‘Female’}$ avec $Age \in [40,60]$** : le nombre d'activités y est plus élevé que dans la population totale.

Le premier motif ne pose qu'un sélecteur, le second en conjoint deux et décrit donc un sous-groupe plus étroit : le sexe et une tranche d'âge sont fixés simultanément.

# Remarque

Un motif de sous-groupe est une forme voisine d'une [[Règle d'association et confiance|règle d'association]] : dans les deux cas l'antécédent est une conjonction de conditions sur les attributs.

La différence est dans le conséquent et dans la mesure associée :

- le conséquent d'une règle d'association est un itemset, c'est-à-dire une présence, et la confiance compare la fréquence de l'union à celle de l'antécédent ;
- le conséquent d'un motif de sous-groupe est une propriété sur un attribut cible, et la qualité compare la distribution de cet attribut dans le sous-groupe à celle de la population totale.

Le sous-groupe n'est jamais prédit individu par individu : un motif reste vrai de l'ensemble qu'il décrit, et ce sont les individus couverts par la description qui sont comptés, non ceux qui vérifieraient la propriété visée.
