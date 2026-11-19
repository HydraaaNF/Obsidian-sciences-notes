#ml-2

# Définition

La **compression mu-law** est une loi de compression logarithmique appliquée à chaque échantillon d'un signal audio (voir [[Audio numérique]]) avant sa quantification : elle étire les faibles amplitudes et comprime les fortes, de sorte que les niveaux de quantification ne sont pas répartis uniformément en amplitude.

Pour un échantillon $x \in [-1, 1]$, la valeur compressée est

$$y = \operatorname{sgn}(x)\,\frac{\ln(1+\mu|x|)}{\ln(1+\mu)}$$

avec $\mu = 255$ et

$$\operatorname{sgn}(x) =
\begin{cases}
-1 & \text{si } x < 0 \\
0 & \text{si } x = 0 \\
1 & \text{si } x > 0
\end{cases}$$

La sortie est impaire et normalisée : $y(-1) = -1$, $y(0) = 0$, $y(1) = 1$, et $y$ reste dans $[-1, 1]$.

Tracée pour $x \in [-1, 1]$, la courbe de $y$ a la forme d'un S : elle passe par le code médian $128$ en $x = 0$, s'aplatit vers les codes $0$ et $255$ aux bornes, et son ordonnée est déjà l'échelle des codes.

La valeur compressée est ensuite arrondie sur une grille de $256$ niveaux, numérotés de $0$ à $255$ : chaque échantillon devient un code entier de $8$ bits, traité comme une classe par un modèle de génération audio.

# Propriétés

- $y$ est impaire et strictement croissante sur $[-1, 1]$ ;
- la pente est maximale en $0$ et décroît quand $|x|$ augmente : la grille est fine autour de zéro et grossière près des bornes ;
- pour $|x|$ petit, $\ln(1+\mu|x|) \approx \mu|x|$, donc $y \approx \frac{\mu}{\ln(1+\mu)}\,x$ : les faibles amplitudes sont amplifiées d'un facteur voisin de $46$ ;
- les $256$ niveaux se codent sur $8$ bits, puisque $2^8 = 256$.

# Interprétation

Le choix de $\mu = 255$ fixe à $256$ le nombre de codes, donc à $8$ bits la résolution du signal compressé. Chaque code couvre une bande d'amplitude étroite au voisinage de zéro et une bande large au voisinage des maxima : les passages faibles gardent du détail, les passages forts sont décrits plus grossièrement.

Cette réduction du nombre de valeurs possibles rend l'audio prédictible par un modèle autorégressif discret : au lieu d'une amplitude réelle, chaque position prend l'un des $256$ codes, et le réseau apprend une distribution de probabilités sur ces codes lors de l'[[Entraînement de WaveNet]].

# Exemple

Un signal sinusoïdal échantillonné sur un peu plus d'une période illustre les deux étapes.

- Avant arrondi, le signal est tracé en points aux instants d'échantillonnage ; il est qualifié de « continu » parce que ses valeurs ne sont pas encore arrondies, bien qu'il soit déjà échantillonné.
- Après compression mu-law et arrondi, les ordonnées deviennent des codes de $0$ à $255$ : les sommets de la sinusoïde s'aplatissent sur quelques codes voisins, alors que les passages par zéro restent raides.

Pour $\mu = 255$, quelques valeurs :

- $x = 0{,}01$ donne $y \approx 0{,}228$, code $157$ ;
- $x = 0{,}1$ donne $y \approx 0{,}591$, code $203$ ;
- $x = 0{,}5$ donne $y \approx 0{,}876$, code $239$ ;
- $x = 1$ donne $y = 1$, code $255$.

Une amplitude de $1\,\%$ de la pleine échelle occupe déjà le code $157$, à $29$ crans au-dessus du code médian $128$ : l'échelle est bien dilatée au voisinage de zéro.

# Remarque

La forme de la loi est parfois écrite avec un $+1$, une division par $2$ et un facteur $\mu$ supplémentaire :

$$y = \left(\operatorname{sgn}(x)\,\frac{\ln(1+\mu|x|)}{\ln(1+\mu)} + 1\right)/2 \times \mu$$

Cette écriture n'est plus impaire : elle étale la sortie sur $[0, \mu]$ au lieu de la garder normalisée dans $[-1, 1]$. Avec $\mu = 255$, elle vaut $(\operatorname{sgn}(x)\ln(1+\mu|x|)/\ln(1+\mu) + 1) \times 255/2$, c'est-à-dire exactement la valeur du code avant arrondi : la conversion en codes qu'elle opère est donc juste. Son défaut est de lier le facteur d'échelle au paramètre $\mu$ plutôt qu'au nombre de codes ; la notation de la source porte d'ailleurs une coquille sur ce facteur, $\mu^{150}$. La forme correcte de la loi est celle de la définition ; le passage aux codes entiers de $0$ à $255$ est une étape d'arrondi distincte, qui s'écrit $c = \operatorname{round}\left((y+1) \times 255/2\right)$.

Avec $\mu = 255$, la grille compte $256$ niveaux : sur le graphique, la dernière graduation de l'axe des ordonnées porte $250$ alors que la courbe atteint $255$ en $x = 1$. Le code maximal reste visible, mais il n'est pas gradué.
