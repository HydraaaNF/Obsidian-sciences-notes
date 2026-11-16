#dmv-subgroup_discovery

# Remarque

Un [[Élagage top-k|classement top-k]] retient les $k$ [[Motif de sous-groupe|motifs]] de plus grande [[Fonction de qualité d'un sous-groupe|qualité]]. Ce critère souffre de deux sources de redondance distinctes.

1. Des langages de motifs expressifs mais redondants : beaucoup de descriptions différentes couvrent le même ensemble d'objets, ce qui produit des top-k uniformes, où les $k$ premières places reviennent à des variantes d'un même motif.
2. Des problèmes indépendants de la recherche : une [[Recherche des sous-groupes|recherche exhaustive]] doit énumérer tous les motifs redondants, et une [[Recherche en faisceau diversifiée|recherche en faisceau]] répète la sélection top-k.

Ces deux problèmes ne sont pas propres à la découverte de sous-groupes.

# Exemple

Un classement top-4 renvoie les quatre descriptions suivantes, rangées par qualité décroissante.

| Rang | Description |
| :--- | :--- |
| 1 | `checking_status != <0 && checking_status != 0<=X<200 && other_parties != co_applicant && other_payment_plans != bank` |
| 2 | `checking_status != <0 && checking_status != 0<=X<200 && other_parties != co_applicant && other_payment_plans != bank && purpose != vacation` |
| 3 | `checking_status != <0 && checking_status != 0<=X<200 && other_parties != co_applicant && other_payment_plans != bank && purpose != other` |
| 4 | `checking_status != <0 && checking_status != 0<=X<200 && other_parties != co_applicant && other_payment_plans != bank && personal_status != female_single` |

Les quatre descriptions partagent le même préfixe de quatre [[Sélecteur d'un motif de sous-groupe|sélecteurs]] sur `checking_status`, `other_parties` et `other_payment_plans`. La première s'arrête à ce préfixe commun, sans sélecteur supplémentaire ; les trois autres n'y ajoutent qu'un seul sélecteur : `purpose != vacation`, `purpose != other`, ou `personal_status != female_single`. Le classement occupe donc ses quatre places avec une seule description et trois de ses quasi-variantes.

# Interprétation

Le classement top-k souffre d'une double perte.

- Il ne montre que de nombreuses variantes du même thème : les rangs sont monopolisés par des descriptions qui couvrent presque le même ensemble d'objets.
- D'autres motifs intéressants ne sont pas trouvés : un thème distinct, classé juste après la fenêtre retenue, reste invisible.

En rangeant les motifs par qualité décroissante, les variantes d'un même motif occupent les premiers rangs et la fenêtre des $k$ premiers ne contient qu'elles ; le premier motif d'un thème différent tombe après la coupure.

Cette difficulté est l'analogue, pour les motifs de sous-groupes, de la redondance qui frappe les [[Limites des itemsets fréquents|itemsets fréquents]] : une masse de motifs répète la même information. Les remèdes diffèrent : les itemsets admettent des représentations condensées, dont les [[Itemsets fréquents maximaux]], tandis qu'un classement top-k se remplace par la [[Sélection d'un ensemble de sous-groupes|sélection d'un ensemble de sous-groupes]], qui retient un ensemble diversifié au lieu des $k$ meilleurs pris individuellement.
