#dmv-pattern_mining_with_information_theory
# Définition

Les ports d'un motif de graphe décrivent comment les occurrences des motifs se connectent les unes aux autres pour reconstruire le graphe original.

Chaque motif porte un port par sommet par lequel une occurrence peut être rattachée au reste du graphe. Un port est décrit par deux éléments :

- le **Port ID**, qui identifie le sommet d'attache à l'intérieur du motif ;
- le **Port code**, qui est le symbole émis dans le flux compressé pour marquer la connexion entre deux occurrences.

Les ports complètent donc une entrée de [[Table de codes de motifs de graphes]] : à la structure du motif et à son code s'ajoute la liste de ses points d'attache, chacun avec le symbole qu'il émet.

# Exemple

| Motif | Structure | Code du motif | Port ID | Port code |
|---|---|---|---|---|
| P1 | $\overset{X}{v_1} \xrightarrow{a} \overset{Y}{v_2} \xrightarrow{b} \overset{Z}{v_3}$ | P1 | $v_1$, $v_2$ | $v_1$, $2$ |
| Pa | $v_1 \xrightarrow{a} v_2$ | Pa | $v_1$, $v_2$ | $v_1$, $v_2$ |
| Pw | $\overset{W}{v_1}$ | Pw | $v_1$ | aucun |
| Px | $\overset{X}{v_1}$ | Px | $v_1$ | aucun |

Le motif P1 possède deux ports, puisqu'une occurrence peut s'attacher par son extrémité $v_1$ ou par son sommet central $v_2$ ; ses deux port codes sont $v_1$ et $2$. Le motif Pa possède les deux mêmes ports, codés $v_1$ et $v_2$. Les motifs à un seul sommet Pw et Px n'ont qu'un port, sans port code : ce sont des sommets isolés du point de vue du raccordement.

Le graphe cible est couvert par deux occurrences de P1 (contours en pointillés bleus et rouges) et une occurrence de Pa (contour en pointillés verts), qui se chevauchent. La reconstitution se lit comme une chaîne où chaque maillon est une occurrence et où la flèche étiquetée donne le port utilisé :

$$\text{P1} \xrightarrow{v_2} \bullet \xrightarrow{v_2} \text{P1} \xrightarrow{v_1} \bullet \xrightarrow{v_1} \text{Pa}$$

La première occurrence de P1 sort par son port $v_2$ et rejoint un point de connexion, qui est aussi le port $v_2$ de la seconde occurrence de P1 ; celle-ci sort par son port $v_1$ et rejoint un second point de connexion, qui est le port $v_1$ de Pa. Les points de connexion notés $\bullet$ sont les sommets du graphe où deux occurrences se recollent, et le port code est le symbole émis à cet endroit dans le flux compressé.

# Remarque

Les ports lèvent exactement la [[Perte d'information d'une table de codes sans ports]] : la suite des codes n'est plus seulement une liste de motifs, elle porte aussi les symboles des ports employés, donc les points de raccordement. Deux graphes qui ne diffèrent que par leurs points de connexion donnent désormais des données encodées différentes.

Le port code n'a pas besoin de coïncider avec l'étiquette du sommet d'attache : pour P1, le premier port émet $v_1$ et le second émet $2$. Seul compte le fait que deux occurrences qui se raccordent émettent le même symbole au même point de connexion, ce qui suffit au décodage pour les recoller.

Le nombre de ports dépend du motif : P1 en a deux, Pw et Px un seul. Chaque port ajoute un symbole au modèle, donc un coût de description que la [[Compression d'un graphe par un ensemble de motifs]] arbitre lors de la sélection des motifs.
