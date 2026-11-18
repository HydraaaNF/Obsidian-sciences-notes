#dmv-pattern_mining_vs_deep_learning

Le passage à l'échelle d'une méthode de fouille de motifs est sa capacité à traiter des jeux dont le nombre de variables croît de plusieurs ordres de grandeur, sans perdre la qualité des motifs trouvés ni voir son temps de calcul exploser. Pour un [[Ensemble de motifs]], ce n'est pas un détail d'implémentation : c'est la condition pour que la méthode s'applique aux jeux réels les plus volumineux.

# Propriétés

Un réseau de neurones peut opérer directement dans l'espace binaire des matrices de transactions et y trouver de bons ensembles de motifs : ses entrées et ses sorties sont des vecteurs binaires, et sa [[Couche de motifs]] le maintient dans cet espace, sans représentation intermédiaire dense.

Cette capacité se résume en trois propriétés :

- le réseau définit et manipule les motifs dans l'espace binaire, celui des items présents ou absents ;
- l'apprentissage repose sur l'aller-retour entre cet espace binaire, pour la définition des motifs et la reconstruction des données, et l'espace continu, pour l'optimisation ;
- l'approche passe bien mieux à l'échelle que les méthodes d'extraction d'ensembles de motifs existantes, ce qui ouvre la possibilité d'analyser des jeux de [[Données de polymorphismes nucléotidiques simples|données de polymorphismes nucléotidiques simples]] réalistes.

# Interprétation

L'aller-retour décrit dans [[Poids binaires et optimisation différentiable]] est la clé du passage à l'échelle. Chacun des deux espaces apporte ce que l'autre ne peut pas fournir :

- l'espace binaire donne des motifs lisibles, un neurone de motif par itemset, et permet de reconstruire une transaction à partir des seuls motifs qu'elle contient ;
- l'espace continu donne une perte dérivable, donc une [[Descente de gradient]] applicable, et fait circuler l'erreur de reconstruction à travers la couche de motifs.

Le coût de l'apprentissage suit alors la taille du réseau, proportionnelle au produit du nombre d'items par le nombre de motifs, là où la recherche d'un ensemble de motifs doit parcourir un espace de candidats (voir [[Complexité de la recherche d'un ensemble de motifs]]).

C'est cette différence d'ordre de grandeur qui ouvre la possibilité d'analyser des jeux de [[Données de polymorphismes nucléotidiques simples|données SNP]] réalistes : des jeux de $10^5$ à $10^6$ items, et denses, hors de portée d'une extraction directe d'ensembles de motifs. Les mesures portent sur des jeux synthétiques jusqu'à $2\times10^4$ variables : ces tailles sont l'ordre de grandeur visé, un à deux ordres de grandeur au-delà de ce qui est mesuré. Leur traitement par un [[Auto-encodeur de motifs]] entraîné par descente de gradient relève donc de l'extrapolation, pas d'un résultat établi.

# Remarque

Le passage à l'échelle s'entend par rapport aux méthodes d'extraction d'ensembles de motifs, pas dans l'absolu. Sur données synthétiques, le gain se lit sur deux axes complémentaires :

- la qualité des motifs retrouvés, mesurée par le score F1, reste entre $0{,}89$ et $0{,}95$ de $125$ à $3{,}9\times10^3$ variables, soit un facteur trente environ, puis décline jusqu'à $\approx 0{,}57$ vers $1{,}9\times10^4$ variables (voir [[Qualité des motifs selon le nombre de variables]]) ;
- le temps de calcul reste de l'ordre de $10^4$ s au plus jusqu'à $2\times10^4$ variables, là où Asso franchit $10^3$ s vers $350$ variables et atteint $\approx 2\times10^5$ s (voir [[Temps de calcul selon le nombre de variables]]). Un repérage calé sur les seules graduations majeures place ce franchissement vers $500$ variables, écart qui ne change pas l'ordre de grandeur.

Ce n'est pas une supériorité sans limite : le score F1 finit par refluer aux très grandes dimensions ; Asso part de $\approx 0{,}90$, décroît régulièrement à partir de $\approx 250$ variables et termine à $\approx 0{,}80$ vers $1{,}2\times10^3$ variables, terme de sa courbe, et l'argument porte sur l'ordre de grandeur traitable, pas sur chaque point de la plage. L'ouverture vers l'analyse de jeux SNP réalistes est une perspective que ce comportement rend crédible, pas un résultat déjà établi sur de tels jeux.
