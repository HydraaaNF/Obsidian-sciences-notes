# Définition

Un modèle de mélange est une somme pondérée de lois : la vraisemblance d'un échantillon $x$ est donnée par

$$f(x) = \sum_{i=1}^K \pi_i f_i(x)$$

avec la contrainte

$$\sum_{i=1}^K \pi_i = 1.$$

$K$ est le nombre de composantes du mélange, $\pi_i$ le poids de la composante $i$ et $f_i()$ sa densité.

# Propriétés

- chaque $f_i()$ peut être une densité quelconque, et les $f_i()$ ne sont pas nécessairement de la même famille ;
- $f()$ est une densité puisque $\int_{-\infty}^{\infty} f(x)dx = 1$ ;
- le modèle s'étend aux variables discrètes.

# Interprétation

Une distribution réelle de données a souvent une forme complexe qu'un modèle gaussien ne peut pas représenter fidèlement. Un modèle de mélange est bien plus souple : en combinant plusieurs composantes, il épouse la forme de la vraie distribution. C'est la raison d'être des modèles de mélange.

Sur un jeu de données réel, la distribution peut s'écarter fortement d'une loi gaussienne : un nuage de points en forme de « V », dont chaque branche est épousée par une composante du mélange.

La forme de la densité du mélange dépend des composantes et de leurs poids : elle peut présenter plusieurs bosses, d'inégales hauteurs, des pics plus ou moins étroits. Des mélanges à deux composantes de poids respectifs $(0{,}7 ; 0{,}3)$, $(0{,}3 ; 0{,}7)$ ou $(0{,}9 ; 0{,}1)$ donnent ainsi des densités de formes très variées.

# Exemple

Un mélange à deux composantes gaussiennes : poids $\pi = [0{,}3, 0{,}7]$ et composantes $f_1 = \mathcal{N}(0, 1)$, $f_2 = \mathcal{N}(2, 1)$, deux [[Loi gaussienne|lois gaussiennes]]. D'après la définition, la densité du mélange s'écrit

$$f(x) = 0{,}3\,f_1(x) + 0{,}7\,f_2(x).$$

# Remarque

La notation des poids d'un mélange n'est pas uniforme : le poids de la composante $i$ se rencontre aussi bien noté $\pi_i$ que $w_i$ ; la notation $\pi_i$ est retenue uniformément.

Le cas particulier où toutes les composantes sont gaussiennes est traité dans [[Mélange gaussien]]. Pour l'estimation des paramètres à partir d'un échantillon, voir [[Estimation par maximum de vraisemblance d'un modèle de mélange]] ; pour le rôle des variables cachées dans un tel modèle, voir [[Variables cachées d'un modèle de mélange]].
