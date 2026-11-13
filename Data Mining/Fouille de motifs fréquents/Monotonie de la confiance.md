#dmv-frequent_itemsets_mining

# Propriétés

La [[Règle d'association et confiance|confiance]] d'une règle d'association n'est **ni monotone ni anti-monotone** : comparer les confiances de deux règles quelconques ne donne aucun ordre, même lorsque leurs itemsets se ressemblent. Une règle portant plus d'items n'a donc pas systématiquement une confiance plus forte ni plus faible.

# Exemple

Base de neuf transactions :

| Transaction | Items achetés |
| :---: | :--- |
| 1 | bread, butter, chocolate, vine, pencil |
| 2 | bread, butter, chocolate, pencil |
| 3 | chocolate |
| 4 | butter, chocolate |
| 5 | bread, butter, chocolate, vine |
| 6 | bread, butter, chocolate |
| 7 | butter |
| 8 | butter |
| 9 | butter |

Les supports utiles se lisent directement dans la table : $\mathrm{support}(\{chocolate\}) = 6$, $\mathrm{support}(\{butter\}) = 8$, $\mathrm{support}(\{butter, chocolate\}) = 5$ et $\mathrm{support}(\{bread, butter, chocolate\}) = 4$.

- $c(\{chocolate\} \to \{bread, butter\}) = 4/6 = 66\,\%$
- $c(\{chocolate\} \to \{butter\}) = 5/6 = 83\,\%$
- $c(\{butter\} \to \{chocolate\}) = 5/8 = 62\,\%$

La deuxième règle, dont le conséquent ne contient qu'un item, a la confiance la plus forte, et la troisième, bâtie sur les mêmes deux itemsets que la deuxième mais dans le sens inverse, la plus faible. Aucune loi d'ordre ne relie ces trois valeurs : la confiance ne peut donc servir à comparer deux règles que par un calcul explicite.

# Interprétation

La confiance combine deux quantités qui varient indépendamment : le support de l'antécédent, au dénominateur, et le support de l'union des deux itemsets, au numérateur. Passer de $\{chocolate\} \to \{butter\}$ à $\{butter\} \to \{chocolate\}$ ne change pas le numérateur, mais fait passer le dénominateur de $6$ à $8$, d'où la chute de $83\,\%$ à $62\,\%$. Un conséquent plus riche fait baisser le numérateur sans toucher au dénominateur, tandis qu'un antécédent plus riche fait baisser les deux : les deux effets ne vont pas dans le même sens, ce qui exclut toute monotonie globale.

# Remarque

Le [[Support d'un itemset|support]], lui, est [[Propriété d'anti-monotonie du support|anti-monotone]] : aucun sur-ensemble d'un itemset infréquent n'est fréquent. La confiance n'offre pas d'équivalent, et aucun élagage général ne s'appuie sur la comparaison de deux règles quelconques.

À antécédent fixé, en revanche, une propriété d'ordre subsiste : la confiance décroît quand le conséquent grandit. C'est cette [[Anti-monotonie de la confiance selon la taille du conséquent|anti-monotonie selon la taille du conséquent]] qui rend possible l'élagage de la [[Génération des règles d'association]], donc la seconde étape du [[Calcul des règles d'association en deux étapes|calcul en deux étapes]].

Une confiance élevée ne traduit qu'une cooccurrence dans la base observée : elle ne suppose aucune relation de cause à effet entre l'antécédent et le conséquent.
