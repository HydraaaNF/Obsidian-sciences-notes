#adm-9

# Modèle

La vérification d'identité, d'un locuteur ou d'un visage, s'écrit comme un test opposant deux hypothèses simples :

- $H_0$ : la personne est celle qu'elle prétend être ;
- $H_1$ : la personne est un imposteur.

La décision se prend en comparant le [[Test du rapport de vraisemblance|rapport de vraisemblance]] des deux hypothèses pour l'observation $y_1^T$ à un seuil $\beta$ :

$$\frac{p(y_1^T; H_0)}{p(y_1^T; H_1)} \begin{cases} > \beta & \text{décider } H_0 \\ < \beta & \text{décider } H_1 \end{cases}$$

# Interprétation

Le rapport mesure combien l'observation est plus vraisemblable sous l'hypothèse « la personne est authentique » que sous l'hypothèse « la personne est un imposteur » : il est grand quand la ressemblance avec la personne revendiquée l'emporte, et le seuil $\beta$ règle l'exigence de preuve avant d'accepter.

En vérification de locuteur, les deux quantités du rapport sont des [[Mélange gaussien|mélanges gaussiens]] :

- $p(y_1^T; H_0)$ est le modèle entraîné sur la voix du locuteur revendiqué ;
- $p(y_1^T; H_1)$ est le modèle de la parole en général, indépendant du locuteur.

Le rapport compare donc l'adéquation de la voix observée au modèle du locuteur revendiqué et son adéquation au modèle générique de la parole : accepter revient à juger la première nettement meilleure que la seconde.

# Remarque

Deux erreurs sont possibles :

- la **fausse acceptation**, qui accepte un imposteur, c'est-à-dire conserve $H_0$ à tort : elle correspond au [[Risque de seconde espèce|risque de seconde espèce]] ;
- le **faux rejet**, qui refuse la personne authentique, c'est-à-dire rejette $H_0$ à tort : il correspond au [[Risque de première espèce|risque de première espèce]].

Les deux erreurs se commandent l'une l'autre par le choix du seuil $\beta$ : abaisser le seuil rend l'acceptation plus facile, ce qui augmente les fausses acceptations et diminue les faux rejets ; l'élever produit l'effet inverse.

La performance d'un système de vérification dépend en outre :

- du fait que le texte prononcé est connu ou non ;
- de la taille du jeu de données ;
- de la durée du signal ;
- de la qualité du signal ;
- du locuteur testé.

La numérotation des deux erreurs est parfois inversée, la fausse acceptation étant alors appelée erreur de type 1 et le faux rejet erreur de type 2. La convention retenue ici est la convention usuelle du test d'hypothèses : l'erreur de type 1 est le rejet à tort de $H_0$, donc le faux rejet, et l'erreur de type 2 la conservation à tort de $H_0$, donc la fausse acceptation.

# Exemple

Les systèmes de vérification se comparent par leurs courbes d'erreur : pour un système donné, on porte en abscisse le taux de fausses acceptations (en %) et en ordonnée le taux de faux rejets (en %), les deux axes étant en échelle logarithmique, chaque point de la courbe correspondant à une valeur du seuil $\beta$. Les courbes descendent : plus un système tolère de fausses acceptations, moins il rejette de personnes authentiques. Des repères marquent sur chaque courbe le point de F-measure maximal et celui d'erreur totale minimale, l'erreur totale étant la moyenne des deux taux.

Les performances mesurées sur trois systèmes, exprimées en pourcentage, sont les suivantes.

| site | ENST | IRISA | LIA |
|---|---|---|---|
| %fa | 9,8 | 0,3 | 2,8 |
| %fr | 25,3 | 23,6 | 30,6 |
| F-measure | 46,9 | 84,3 | 66,0 |

Le F-measure le plus élevé, donc le meilleur compromis entre les deux taux d'erreur, est obtenu par le système IRISA, avec le taux de fausses acceptations le plus faible des trois.

L'approche par apprentissage consiste à apprendre un espace où les observations d'une même personne sont proches et celles de personnes différentes éloignées, comparaison assurée par des [[Réseaux siamois]].
