#dmv-pattern_mining_vs_deep_learning

Le [[F-mesure F1|score F1]] mesure la qualité des motifs retrouvés : il résume en une valeur entre $0$ et $1$, plus haute est mieux, la part des motifs présents dans les données que l'extraction retrouve et la part des motifs extraits qui existent réellement. Il vaut $1$ quand les deux coïncident exactement, et décroît dès que l'extraction rate des motifs ou en invente. Le comparer entre méthodes sur des données synthétiques, en fonction du nombre de variables du jeu de données, indique jusqu'où chacune garde des motifs pertinents quand la dimension augmente.

L'abscisse porte le nombre de variables, sur une échelle logarithmique : le cadre s'étend d'environ $2\times10^1$ à $2\times10^4$, et seules les graduations étiquetées ($10^2$, $10^3$, $10^4$) valent chacune un facteur dix, les huit graduations non étiquetées de chaque décade marquant les valeurs de $2$ à $9$. Les écarts de position se lisent donc en ordres de grandeur. L'ordonnée porte le score F1, entre $0$ et $1$. Quatre méthodes de fouille d'[[Ensemble de motifs|ensembles de motifs]] sont comparées : [[Auto-encodeur de motifs|BiNAPs]], Asso, SLIM et DEsc.

# Exemple

```chart
type: line
labels: ["35", "125", "200", "285", "340", "365", "1 200", "1 900", "2 700", "3 400", "3 900", "11 000", "19 000"]
series:
  - title: BiNAPs
    data: [0.66, 0.92, 0.9, 0.95, 0.95, 0.94, 0.95, 0.93, 0.91, 0.9, 0.89, 0.71, 0.57]
  - title: Asso
    data: [0.9, 0.9, 0.94, 0.89, 0.9, 0.89, 0.8, null, null, null, null, null, null]
  - title: SLIM
    data: [0.44, 0.41, 0.4, 0.41, 0.37, 0.13, 0.09, 0.08, null, null, null, null, null]
  - title: DEsc
    data: [0, 0.14, 0.16, 0.14, 0.16, 0.17, 0.13, 0.17, 0.16, 0.18, null, null, null]
```

Chaque abscisse est un point de mesure relevé sur le tracé, arrondi ; le bloc les espace régulièrement et ne reproduit donc pas l'échelle logarithmique de la figure, seules les valeurs comptent. Une valeur absente signale une méthode dont la courbe s'arrête avant cette abscisse, et non une qualité nulle.

Valeurs relevées sur la figure, approximatives :

- **BiNAPs** (bleu) : $\approx 0{,}66$ vers $35$ variables, $\approx 0{,}92$ vers $125$, entre $0{,}89$ et $0{,}95$ de $125$ à $3{,}9\times10^3$, puis $\approx 0{,}71$ vers $1{,}1\times10^4$ et $\approx 0{,}57$ à sa dernière abscisse, vers $1{,}9\times10^4$
- **Asso** (orange) : $\approx 0{,}90$ de $35$ à $125$ variables, maximum $\approx 0{,}94$ vers $200$, puis $\approx 0{,}89$ à $365$ et dernière valeur $\approx 0{,}80$ vers $1{,}2\times10^3$, où sa courbe s'arrête
- **SLIM** (jaune) : $\approx 0{,}44$ vers $35$ variables, $\approx 0{,}40$ vers $200$, $\approx 0{,}37$ vers $340$, chute à $\approx 0{,}13$ vers $365$, puis $\approx 0{,}09$ et $\approx 0{,}08$ jusqu'à sa dernière abscisse, vers $1{,}9\times10^3$
- **DEsc** (vert) : part de $0$ vers $35$ variables, monte à $\approx 0{,}16$ vers $200$, puis oscille entre $0{,}13$ et $0{,}18$ jusqu'à sa dernière abscisse, vers $3{,}4\times10^3$

Association entre couleur et méthode, qui ne se lit pas sur le tracé :

| Couleur | Méthode |
| --- | --- |
| Orange | Asso |
| Bleu | BiNAPs |
| Vert | DEsc |
| Jaune | SLIM |

# Interprétation

Les quatre courbes dessinent trois régimes, mais elles ne couvrent pas la même plage : seule BiNAPs est tracée jusqu'au bord droit du graphique, les trois autres s'arrêtent bien avant.

**BiNAPs gagne sur la plus grande partie de la plage.** Sa qualité monte dès les faibles dimensions, plafonne près de $0{,}95$ de $285$ variables à $1{,}2\times10^3$, puis décline lentement jusqu'à $\approx 0{,}89$ vers $3{,}9\times10^3$, et plus nettement ensuite, jusqu'à $\approx 0{,}57$ vers $1{,}9\times10^4$. Entre $125$ et $3{,}9\times10^3$ variables, soit un facteur trente, elle reste entre $0{,}89$ et $0{,}95$ : sur cet intervalle, l'extraction des motifs résiste à la croissance de la dimension, et ne cède qu'aux très grandes dimensions.

**Asso reste bon mais s'érode, et sa courbe s'arrête tôt.** Sa qualité est la plus élevée aux faibles dimensions, $\approx 0{,}90$ contre $\approx 0{,}66$ pour BiNAPs, avec un maximum $\approx 0{,}94$ vers $200$ variables, puis elle diminue lentement, sans rupture, jusqu'à $\approx 0{,}80$ vers $1{,}2\times10^3$. C'est là que le tracé s'arrête : le graphique ne dit rien de ce que vaudrait Asso aux très grandes dimensions.

**SLIM et DEsc ne tiennent pas.** SLIM se maintient à un niveau médiocre, autour de $0{,}44$, cède un peu jusqu'à $\approx 0{,}37$ vers $340$ variables, puis s'effondre à $\approx 0{,}13$ vers $365$ et reste sous $0{,}1$ jusqu'à sa dernière abscisse : au-delà de quelques centaines de variables, il ne retrouve plus les motifs. DEsc, parti de $0$, ne dépasse pas $\approx 0{,}18$ et oscille entre $0{,}13$ et $0{,}18$ sur toute la plage où sa courbe est tracée, jusqu'à $\approx 3{,}4\times10^3$ variables.

**Les croisements se lisent près de $10^2$ variables.** Asso devance BiNAPs vers $35$ variables ($\approx 0{,}90$ contre $\approx 0{,}66$), BiNAPs passe devant vers $125$ ($\approx 0{,}92$ contre $\approx 0{,}90$), Asso reprend l'avantage vers $200$ ($\approx 0{,}94$ contre $\approx 0{,}90$), puis BiNAPs reste devant à partir de $\approx 250$ variables. Au-delà, la dégradation de BiNAPs est la seule que le graphique documente, puisque sa courbe est la seule à atteindre $1{,}9\times10^4$ variables : sa qualité y tombe à $\approx 0{,}57$. Cette lecture de la qualité se complète par celle du coût, dans [[Temps de calcul selon le nombre de variables]], et fonde l'argument de [[Passage à l'échelle de l'apprentissage de motifs|passage à l'échelle]] de l'apprentissage de motifs, utile pour des données aussi denses que les [[Données de polymorphismes nucléotidiques simples|données de polymorphismes nucléotidiques simples]].

# Remarque

La figure ne comporte pas de légende de courbes : rien dans le tracé n'associe une couleur à une méthode. L'association est rétablie ici par le tableau des couleurs ; sans lui, les quatre courbes resteraient anonymes.

Les étiquettes d'axes de la figure portent un préfixe « # », simple artefact d'étiquetage : les axes se lisent ici « nombre de variables » et « score F1 ».

Les valeurs portées dans le graphique sont relevées à la lecture de la figure, donc approximatives ; comme l'abscisse est logarithmique, un même écart horizontal vaut un rapport constant entre nombres de variables, et une courbe plate traduit une qualité indépendante de la dimension sur cet intervalle. Une courbe qui s'arrête ne vaut pas zéro au-delà de son dernier point : la méthode n'y est simplement plus mesurée, et les courbes ne se comparent qu'aux abscisses où elles existent toutes deux.
