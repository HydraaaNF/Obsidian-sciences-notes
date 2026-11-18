#dmv-pattern_mining_with_information_theory
# Interprétation

Une [[Table de codes de motifs de graphes]] décrit un graphe par une liste de motifs et un code par motif. Encoder le graphe revient à le couvrir par des occurrences de ces motifs, puis à émettre le code du motif pour chaque occurrence retenue.

Cette description ne dit rien des sommets par lesquels une occurrence se rattache au reste du graphe. Or deux occurrences d'un même motif, ou deux motifs différents, peuvent se raccorder par des sommets distincts : ce sont des points de connexion différents. La table de codes, elle, n'enregistre que la structure du motif et son code, si bien que le flux encodé est identique quel que soit le point de connexion réellement utilisé.

La conséquence est directe : le graphe ne peut pas être reconstruit à partir de la seule suite des codes. Deux graphes dont les occurrences ne diffèrent que par leurs points de rattachement produisent exactement les mêmes données encodées, donc la même longueur de description. Le modèle est plus court qu'il ne devrait l'être parce qu'il a oublié une information qu'il aurait dû transmettre : c'est une perte d'information.

# Exemple

Le graphe considéré a un sommet central $Y$, trois sommets $X$ atteints depuis $Y$ par une arête $a$, trois sommets $Z$ atteints depuis $Y$ par une arête $b$, et un sommet $W$ rattaché à l'un des $X$.

| Motif | Structure | Code |
|---|---|---|
| P1 | $\overset{X}{v_1} \xrightarrow{a} \overset{Y}{v_2} \xrightarrow{b} \overset{Z}{v_3}$ | P1 |
| Pa | $v_1 \xrightarrow{a} v_2$ | Pa |
| Pw | $\overset{W}{v_1}$ | Pw |
| Px | $\overset{X}{v_1}$ | Px |

Le graphe est couvert par deux occurrences du motif P1 (contours en pointillés bleus et rouges) et une occurrence du motif Pa (contour en pointillés verts). Les deux occurrences de P1 partagent le sommet central $Y$ : l'occurrence bleue part du sommet $X$ supérieur gauche et rejoint le sommet $Z$ supérieur droit, l'occurrence rouge part du sommet $X$ inférieur gauche et rejoint le sommet $Z$ inférieur droit. L'occurrence de Pa occupe ce même sommet $X$ inférieur gauche, qu'elle relie par une arête $a$ au sommet étiqueté $W$. La chaîne des trois occurrences ne comporte ainsi que deux points de connexion.

Les données encodées se réduisent à la suite des codes lue dans l'ordre de parcours des occurrences, ici P1, P1 puis Pa. Rien dans cette suite ne marque le sommet d'attache de chaque occurrence : la suite reste P1, P1, Pa quels que soient les points de connexion. Une même description vaut donc pour plusieurs graphes distincts, et le décodage ne permet pas de savoir comment recoller les occurrences.

# Remarque

La table doit comporter une entrée par motif, y compris le motif à un seul sommet étiqueté $W$ : la table complète comporte ainsi les quatre lignes données ci-dessus. Cette ligne n'est pas ce qui assure la couverture du graphe, puisque l'occurrence de Pa couvre déjà le sommet $W$ en même temps que le sommet $X$ inférieur gauche ; elle complète le catalogue des motifs.

La perte d'information ne vient pas du choix des motifs, mais de ce que la table ne décrit que leur forme. Elle se corrige en ajoutant à chaque motif ses points d'attache : c'est l'objet des [[Ports d'un motif de graphe]].
