# Définition

La **boîte à moustaches** (en anglais *box and whisker plot*) est une représentation compacte de la moyenne et de la dispersion d'une distribution. Elle repose sur les [[Quartiles et écart interquartile|quartiles]] $Q_1$ et $Q_3$ et sur l'écart interquartile $Q_3 - Q_1$ :

- la boîte est délimitée par $Q_1$ et $Q_3$, la [[Moyenne, médiane et mode|médiane]] y étant marquée ;
- la moustache supérieure s'arrête à la plus grande valeur observée inférieure ou égale à $Q_3 + 1{,}5(Q_3 - Q_1)$ ;
- la moustache inférieure s'arrête à la plus petite valeur observée supérieure ou égale à $Q_1 - 1{,}5(Q_3 - Q_1)$ ;
- les observations situées au-delà de ces bornes sont des **valeurs aberrantes** (*outliers*), tracées individuellement.

# Interprétation

La largeur de la boîte vaut l'écart interquartile $Q_3 - Q_1$ ; elle fixe l'échelle des moustaches, qui s'étendent au plus à $1{,}5(Q_3 - Q_1)$ de part et d'autre. Pour une distribution en cloche, les quartiles se situent à $\pm 0{,}6745\sigma$ et les bornes des moustaches à $\pm 2{,}698\sigma$ de la moyenne, où $\sigma$ désigne l'[[Variance et écart-type|écart-type]] : la boîte contient alors 50 % des observations et les zones entre la boîte et les extrémités des moustaches, 24,65 % chacune.

# Exemple

Cinq groupes de mesures de la vitesse de la lumière, étiquetés 1 à 5 (axe vertical en km/s au-dessus de 299 000), sont comparés par des boîtes à moustaches ; une droite horizontale marque la vitesse vraie. Pour chaque groupe, la boîte donne la médiane et l'étalement central, les moustaches s'arrêtent aux valeurs non aberrantes, et plusieurs valeurs atypiques apparaissent comme des points isolés au-dessus ou au-dessous des moustaches.

# Remarque

Contrairement à l'[[Étendue]], qui s'appuie sur le minimum et le maximum des observations, les moustaches ne s'étirent pas jusqu'aux valeurs atypiques : une observation située au-delà des bornes est tracée séparément comme valeur aberrante.
