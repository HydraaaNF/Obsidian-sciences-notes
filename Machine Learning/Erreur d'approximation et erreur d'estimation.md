#ml-1

# Définition

Des données sont liées par une loi inconnue $f$. Chercher l'optimum consiste à :

- choisir un [[Modèle d'apprentissage|modèle]], c'est-à-dire une famille $H$ de lois, qui forme l'[[Espace d'hypothèses|espace d'hypothèses]] de la recherche ;
- chercher la meilleure loi $h^{*}$ de $H$, celle qui explique, simule ou approxime les données ;
- retenir le résultat de la recherche, une loi $h$ de $H$.

La loi $h$ ne coïncide pas avec $f$ pour trois raisons, qui définissent trois erreurs :

- l'erreur d'approximation : $h^{*}$ peut être loin de $f$ ;
- l'erreur d'estimation : la recherche peut ne pas trouver le $h$ le plus proche de $h^{*}$ ;
- l'erreur intrinsèque : les données sont bruitées par une erreur de mesure.

# Interprétation

Le choix de la taille de la famille $H$ arbitre entre deux erreurs :

- petite famille de lois (peu de paramètres) : il est facile de trouver le $h$ le plus proche de $h^{*}$, mais $h^{*}$ peut être loin de $f$, ce qui donne une erreur d'approximation ;
- grande famille de lois (beaucoup de paramètres) : $h^{*}$ peut être proche de $f$, mais il est difficile de trouver le $h$ le plus proche de $h^{*}$, ce qui donne une erreur d'estimation ;
- données bruitées (erreur de mesure) : l'erreur intrinsèque s'ajoute quel que soit le modèle choisi.

Sur la représentation de ce cadre, la petite famille $H$ est incluse dans une famille plus vaste $H'$, elle-même incluse dans la famille de toutes les lois susceptibles d'engendrer les données ; la loi $f$ et la loi bruitée $g = f - \text{bruit}$ se situent hors de ces familles. La meilleure loi de la famille, $h^{*}$, et la loi effectivement trouvée, $h$, y sont deux points distincts : l'écart entre $f$ et $h^{*}$ mesure l'erreur d'approximation, l'écart entre $h^{*}$ et $h$ mesure l'erreur d'estimation.

# Remarque

- Les trois erreurs se cumulent : l'écart entre $h$ et $f$ se décompose en erreur d'approximation, erreur d'estimation et erreur intrinsèque. Seule l'erreur intrinsèque est irréductible, puisqu'elle vient des données elles-mêmes et non du choix du modèle.
- Le compromis entre petite et grande famille recoupe celui entre [[Surapprentissage et sous-apprentissage|sous-apprentissage et surapprentissage]] : une famille trop étroite ne peut pas s'approcher de $f$, une famille trop riche rend la recherche du $h$ optimal difficile.
