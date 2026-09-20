# Définition
L'ACP restreint la [[Projection vs clustering|projection]] à des transformations linéaires : la nouvelle base $u$ est une combinaison linéaire de la base $v$, et les nouvelles coordonnées $x_u$ sont une combinaison linéaire de $x_v$, éventuellement avec réduction de dimension.

$$y_{q \times 1} = U_{q \times p} \, x_{p \times 1}$$

# Interprétation
L'ACP remplace des variables corrélées $x_1, \ldots, x_p$ par de nouvelles variables non corrélées, les [[Vocabulaire de l'ACP|composantes principales]] $c_1, \ldots, c_q$, combinaisons linéaires des $x_i$ de variance maximale.
