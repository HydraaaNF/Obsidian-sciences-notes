#dmv-pattern_mining_vs_deep_learning

Le temps de calcul de quatre approches de recherche d'un [[Ensemble de motifs|ensemble de motifs]], BiNAPs, Asso, DEsc et SLIM, se mesure sur des données synthétiques en fonction du nombre de variables. C'est le même protocole expérimental qui fournit la [[Qualité des motifs selon le nombre de variables|qualité des motifs trouvés]] : les deux mesures se lisent ensemble, l'une disant ce que coûte une exécution, l'autre ce qu'elle rapporte.

L'axe horizontal porte le nombre de variables sur une échelle logarithmique, de $2\times10^1$ à $2\times10^4$, et l'axe vertical le temps de calcul en secondes, lui aussi logarithmique, de $10^0$ à $10^6$ s. La hauteur d'un point vaut donc

$$y = \log_{10} t$$

où $t$ est le temps de calcul en secondes : une unité de l'axe vertical représente un facteur dix sur le temps, deux unités un facteur cent. Une courbe basse désigne une approche rapide, et la pente d'une courbe se lit comme un exposant de croissance.

# Interprétation

Les quatre courbes croissent avec le nombre de variables, mais à des rythmes très différents, et deux régimes se dégagent.

**BiNAPs paie un coût d'entrée élevé et croît lentement, par paliers.** Sa courbe part à environ $20$ s vers $35$ variables et reste plate, entre $20$ et $25$ s, jusqu'à $340$ variables : sur cette plage, le temps de calcul ne dépend pratiquement pas du nombre de variables. Un seuil est ensuite franchi : environ $80$ s vers $365$ variables, puis environ $130$ s vers $1\,200$ variables. Au-delà, elle croît lentement et régulièrement, jusqu'à environ $1{,}2\times10^4$ s vers $1{,}9\times10^4$ variables. C'est la seule courbe qui couvre toute la plage de mesure.

**Les trois autres approches partent plus bas et décrochent plus tôt.** Asso part à environ $3$ s vers $35$ variables, SLIM et DEsc à environ $1$ s. Asso croît le plus tôt : elle franchit $10^3$ s vers $350$ variables et atteint environ $1{,}7\times10^5$ s vers $1{,}2\times10^3$ variables, où son tracé s'arrête. DEsc et SLIM suivent des trajectoires voisines, d'abord modérées puis fortement croissantes : SLIM atteint environ $2{,}3\times10^5$ s vers $1{,}9\times10^3$ variables, DEsc environ $2{,}5\times10^5$ s vers $3{,}4\times10^3$ variables. Toutes trois quittent la plage haute de l'axe bien avant $10^4$ variables.

**Le classement s'inverse avec la taille.** Aux faibles nombres de variables, BiNAPs est de sept à vingt fois plus lent que ses concurrentes ($21$ s contre $1$ à $3$ s). Aux grands nombres, l'ordre s'inverse : vers $1{,}9\times10^4$ variables, BiNAPs reste autour de $1{,}2\times10^4$ s, alors que les trois autres courbes se sont arrêtées après avoir dépassé $10^5$ s. Le croisement traduit deux façons opposées de payer le coût : un surcoût fixe d'un côté, une croissance forte avec la dimension de l'autre.

Sur un tracé bilogarithmique, une portion rectiligne correspond à une loi de puissance : le temps varie alors comme $t \propto n^{\alpha}$, où $n$ est le nombre de variables et $\alpha$ la pente du segment. La quasi-horizontalité de BiNAPs jusqu'à $340$ variables signifie un exposant proche de zéro, donc un coût indépendant de la dimension ; les segments redressés des trois autres approches signifient au contraire un exposant élevé.

Ce comportement est ce qui rend le passage à l'échelle possible : rester dans l'ordre de $10^4$ s à $2\times10^4$ variables ouvre l'analyse de jeux de motifs réalistes, dont les [[Données de polymorphismes nucléotidiques simples|données de polymorphismes nucléotidiques simples]], qui comptent de $10^5$ à $10^6$ items. Le détail de cet argument est développé dans [[Passage à l'échelle de l'apprentissage de motifs]].

# Exemple

**(b) Temps de calcul en secondes selon le nombre de variables**

```chart
type: line
labels: ["35", "125", "200", "285", "340", "365", "1 200", "1 900", "2 700", "3 400", "3 900", "11 000", "19 000"]
series:
  - title: BiNAPs
    data: [1.3, 1.4, 1.4, 1.4, 1.4, 1.9, 2.1, 2.3, 2.5, 2.6, 2.7, 3.6, 4.1]
  - title: Asso
    data: [0.5, 1.8, 2.3, 2.7, 2.8, 3.9, 5.2, null, null, null, null, null, null]
  - title: DEsc
    data: [0.0, 0.3, 0.6, 0.9, 1.1, 1.8, 3.5, 4.3, 4.9, 5.4, null, null, null]
  - title: SLIM
    data: [0.0, 0.0, 0.5, 1.1, 1.4, 2.5, 4.6, 5.4, null, null, null, null, null]
```

Chaque abscisse est un point de mesure relevé sur le tracé, arrondi ; le bloc les espace régulièrement et ne reproduit donc pas l'échelle logarithmique de la figure, seules les valeurs comptent. Une valeur absente signale soit un point que la courbe ne porte pas, soit un tracé arrêté avant cette abscisse ; elle ne vaut jamais zéro seconde.

Valeurs relevées sur la figure, approximatives, portées en $\log_{10} t$ : lire $3$ sur l'axe vertical revient à lire $10^3$ s.

- **BiNAPs** (bleu) : $\approx 1{,}3$ vers $35$ variables (soit $\approx 20$ s), plateau à $\approx 1{,}4$ jusqu'à $340$, saut à $\approx 1{,}9$ vers $365$, puis $\approx 2{,}1$ vers $1{,}2\times10^3$, $\approx 2{,}5$ vers $2{,}7\times10^3$ et $\approx 4{,}1$ à sa dernière abscisse, vers $1{,}9\times10^4$
- **Asso** (orange) : $\approx 0{,}5$ vers $35$ variables (soit $\approx 3$ s), $\approx 1{,}8$ vers $125$, $\approx 2{,}8$ vers $340$, saut à $\approx 3{,}9$ vers $365$, puis $\approx 5{,}2$ à sa dernière abscisse, vers $1{,}2\times10^3$, où sa courbe s'arrête
- **DEsc** (vert) : $\approx 0$ vers $35$ variables (soit $\approx 1$ s), $\approx 0{,}3$ vers $125$, $\approx 1{,}1$ vers $340$, saut à $\approx 1{,}8$ vers $365$, puis $\approx 4{,}3$ vers $1{,}9\times10^3$ et $\approx 5{,}4$ à sa dernière abscisse, vers $3{,}4\times10^3$
- **SLIM** (jaune) : $\approx 0$ vers $35$ et $125$ variables (soit $\approx 1$ s), $\approx 1{,}1$ vers $340$, saut à $\approx 2{,}5$ vers $365$, puis $\approx 4{,}6$ vers $1{,}2\times10^3$ et $\approx 5{,}4$ à sa dernière abscisse, vers $1{,}9\times10^3$

Au premier point du tracé, vers $35$ variables, BiNAPs tourne en une vingtaine de secondes, Asso en trois secondes, SLIM et DEsc en une seconde. Vers $365$ variables, le seuil est franchi : BiNAPs passe à environ $80$ s, Asso est déjà à près de $8\times10^3$ s, DEsc à environ $60$ s. À $1\,200$ variables, l'écart atteint trois ordres de grandeur : BiNAPs reste vers $1{,}3\times10^2$ s, alors qu'Asso a dépassé $10^5$ s. À $1{,}9\times10^4$ variables, seule la courbe de BiNAPs subsiste, autour de $1{,}2\times10^4$ s.

# Remarque

Le titre de sous-figure « (b) Temps de calcul en secondes selon le nombre de variables » distingue ce tracé de celui de la qualité qui le précède : les deux ne mesurent pas la même grandeur et ne partagent pas la même échelle verticale, et sans ce titre le tracé se confond avec le précédent.

Les étiquettes d'axes sont « nombre de variables » et « temps de calcul en secondes ». La notation de décompte « # » de « # features » n'est pas reprise devant la première, où elle ferait un titre ; elle ne concerne de toute façon que cet axe.

Le franchissement de $10^3$ s par Asso se lit à $n\approx344$ variables, d'où la formulation « vers $350$ variables ». Un repérage plus grossier, calé sur les seules graduations majeures, place volontiers ce franchissement vers $500$ variables : entre $340$ et $365$ variables, Asso passe de $6\times10^2$ s à près de $8\times10^3$ s, si bien que la pente très forte rend l'écart entre les deux lectures inévitable sans changer le propos. La valeur retenue est celle du croisement mesuré sur le tracé.
