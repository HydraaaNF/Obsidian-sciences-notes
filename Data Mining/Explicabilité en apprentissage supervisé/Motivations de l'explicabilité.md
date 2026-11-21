#dmv-xai

# Interprétation

Les modèles d'apprentissage automatique ne se contentent pas de prédire : ils tranchent. Dans les usages courants, leur réponse est une décision qui engage directement autrui.

| Domaine | Question de l'agent IA | Réponse | Conséquence |
|---|---|---|---|
| Imagerie médicale | Everything ok? | Yes | Le médecin valide l'analyse des scanners |
| Conduite autonome | Need to stop? | No | Le véhicule poursuit sa trajectoire |

Dans les deux cas, l'agent ne fournit pas un avis mais une décision exécutée aussitôt : l'analyse des scanners est validée, le véhicule conserve sa trajectoire. Une réponse fausse n'y est donc pas une erreur de prédiction anodine, elle a une conséquence matérielle sur un patient ou sur un usager de la route.

De là vient l'exigence propre à l'[[Explicabilité]] : il faut connaître le rationale d'une réponse, c'est-à-dire les raisons qui la fondent, et pas seulement son résultat. Un modèle opaque, au sens de l'[[Interprétabilité]], ne livre que la réponse ; l'[[Explication]] est ce qui permet à son destinataire de l'examiner, de l'accepter ou de la corriger.

Les motivations de cette exigence se rangent en deux familles.

- Débogage du système : régler le modèle (*tuning*) et repérer les biais présents dans les données d'entraînement.
- Raisons légales et éthiques, dont le détail est porté par [[Cadre légal et éthique de l'explicabilité]].

Les deux familles ne concernent pas les mêmes destinataires : le débogage sert à corriger le modèle, les raisons légales et éthiques engagent la décision rendue. Le seul destinataire nommé est le médecin, qui valide l'analyse des scanners avant d'agir.

Une même réponse n'appelle donc pas la même explication selon l'usage qu'on en fait : corriger le modèle ou justifier la décision.

# Exemple

Un husky est classé « loup » par un classifieur d'images. La prédiction seule ne dit rien de la raison du verdict ; l'explication, elle, montre sur quoi le modèle s'est appuyé. Les deux vignettes vont par paire : (a) la prédiction, husky classé « loup » ; (b) l'explication, où le fond enneigé est retenu et l'animal masqué.

L'explication révèle un indice trompeur : le classifieur s'appuie sur la neige du décor plutôt que sur l'animal lui-même. C'est exactement le défaut que la motivation de débogage vise à mettre au jour : sans l'explication, le modèle serait tenu pour compétent alors qu'il répond à un élément du décor.

# Remarque

Les lignes directrices pour une IA digne de confiance rattachent l'explication à la production de la confiance.

Les défaillances qui rendent ces motivations concrètes, du classement biaisé à la décision administrative automatisée, sont rassemblées dans [[Affaires révélant les risques des modèles opaques]].
