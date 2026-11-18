#dmv-xai

# Définition

Les modèles d'apprentissage automatique servent à prendre des décisions critiques. Il faut donc pouvoir connaître la raison qui soutient une réponse du modèle, c'est-à-dire le *rationale* de cette réponse.

Deux familles de raisons motivent cette exigence :

- le **débogage** : régler le modèle, repérer les biais présents dans les données ;
- les **raisons légales et éthiques**.

Les raisons légales et éthiques se déclinent en quatre motifs :

- le règlement général sur la protection des données, dont le considérant 71 fonde un droit à l'explication des décisions automatisées ;
- le règlement européen sur les services numériques (*Digital Services Act*), qui impose aux plateformes en ligne des obligations de transparence ;
- la compréhension de la source du biais de décision du classifieur ;
- la génération de la confiance, portée par les lignes directrices pour une intelligence artificielle digne de confiance.

Le règlement européen sur l'intelligence artificielle (*AI Act*) distingue de son côté les usages interdits et les usages à haut risque.

# Propriétés

Pour un système d'intelligence artificielle à haut risque, la supervision humaine (article 14) doit mettre la personne chargée de la surveillance en mesure de :

- **(a)** comprendre les capacités et les limites pertinentes du système et surveiller dûment son fonctionnement, notamment pour détecter et traiter les anomalies, les dysfonctionnements et les performances inattendues ;
- **(b)** rester consciente de la tendance possible à s'appuyer automatiquement, ou de façon excessive, sur la sortie produite par un système à haut risque (biais d'automatisation), en particulier lorsque ce système sert à fournir des informations ou des recommandations pour des décisions prises par des personnes physiques ;
- **(c)** interpréter correctement la sortie du système à haut risque, en tenant compte par exemple des outils et des méthodes d'interprétation disponibles ;
- **(d)** décider, dans toute situation particulière, de ne pas utiliser le système à haut risque ou, autrement, de ne pas tenir compte de sa sortie, de passer outre cette sortie ou de l'inverser.

Ces quatre facultés forment un même dispositif : comprendre le système, rester vigilant devant sa sortie, l'interpréter, puis décider de la suite à donner.

# Interprétation

Le cadre légal et éthique ne demande pas seulement qu'une explication existe : il répartit des responsabilités. Le **droit à l'explication** attache la justification à la personne concernée par la décision, tandis que la supervision humaine attache la maîtrise à la personne qui conduit le système.

Deux enjeux éthiques se lisent dans ces obligations. L'**équité** d'abord : repérer la source du biais de décision suppose de remonter du résultat du classifieur aux données qui l'ont produit, ce que le débogage permet déjà et ce que le motif légal donne pour raison d'exiger. La **responsabilité** ensuite : la faculté de ne pas suivre la sortie du système maintient la décision finale du côté humain, y compris lorsque le système fournit une recommandation ou une information déjà formée.

Le biais d'automatisation est le point où les deux enjeux se rejoignent : une explication comprise mais suivie sans recul ne protège personne, et c'est pourquoi la supervision est une obligation de moyen portant sur la vigilance, et non la seule production d'une explication. La confiance recherchée par les lignes directrices pour une intelligence artificielle digne de confiance se construit ainsi sur une défiance organisée, où l'humain peut toujours contredire la machine.

# Remarque

Le règlement européen sur l'intelligence artificielle range d'un côté les usages **interdits**, de l'autre les usages *à haut risque*.

Les usages interdits énumérés sont la notation sociale, l'inférence des émotions au travail ou à l'école, les techniques subliminales visant à altérer la prise de décision, la liste restant ouverte.

Aux systèmes à haut risque s'ajoutent la gouvernance des données, la documentation et la tenue de registres, ainsi que la supervision humaine déjà détaillée.

Le droit à l'explication du considérant 71 se lit avec le droit de ne pas faire l'objet d'une décision fondée exclusivement sur un traitement automatisé.

Le règlement européen sur les services numériques ne vise pas les modèles eux-mêmes mais les plateformes qui les déploient : la transparence exigée porte sur les systèmes de recommandation et sur la publicité, non sur la structure interne du modèle.

La génération de la confiance n'est pas un motif indépendant des autres : elle résulte de la compréhension du biais, de l'explication fournie et de la possibilité de contredire le système.

Les obligations décrites ici se rattachent aux motivations générales de l'[[Explicabilité]] : la confiance et la détection des biais, exposées dans [[Motivations de l'explicabilité]], y prennent la forme d'obligations et non de préférences de conception.

# Exemple

L'affaire du scandale néerlandais des allocations illustre les risques de l'usage d'algorithmes par les administrations : l'administration fiscale a ruiné des milliers de vies en employant un algorithme de détection de fraude aux prestations ; le cas est détaillé dans [[Affaires révélant les risques des modèles opaques]].
