# Modèle

Le *bruit* (de transmission, de traitement, etc.) qui s'ajoute à un signal déterministe à temps continu $t \in \mathbb{R} \mapsto x(t)$ ou à temps discret $n \in \mathbb{Z} \mapsto x_n$ se modélise dans les applications par une famille de [[Variable aléatoire réelle|variables aléatoires réelles]] $(X(t))_{t \in \mathbb{R}}$ ou $(X_n)_{n \in \mathbb{Z}}$.

# Interprétation

Le bruit qui s'ajoute à un signal, même lorsqu'il est discret, est un réel, donc *a priori* ces variables aléatoires sont **[[Variable aléatoire continue|continues]]** (dans certaines applications on peut toutefois considérer des bruits [[Variable aléatoire discrète|à valeurs dans un ensemble dénombrable de réels]]). Ainsi, lors d'une observation de ce signal à l'instant $t \in \mathbb{R}$ (respectivement $n \in \mathbb{Z}$), c'est la valeur $x(t) + X(t, \omega)$ (respectivement $x_n + X_n(\omega)$), avec $\omega \in \Omega$, à laquelle on a accès, et non la valeur théorique $x(t)$ (respectivement $x_n$). Le rôle de $\omega$ est de tenir compte du fait qu'une autre observation du même signal au même instant $t$ n'aurait pas donné la même valeur, puisque le bruit n'aurait pas été le même. C'est donc bien la théorie des variables aléatoires qui est adaptée à la situation.

# Remarque

Lorsque plusieurs bruits s'ajoutent au signal déterministe (par exemple un bruit d'émission, un bruit de transmission et un bruit de traitement à la réception), il faut savoir déterminer la [[Loi d'une variable aléatoire|loi]] de la somme des variables aléatoires représentant ces bruits. C'est assez facile lorsque les bruits sont [[Indépendance de variables aléatoires|indépendants]], mais peut être très difficile dans le cas contraire. Le sujet est également important pour certaines applications relevant de l'informatique, par exemple les questions de reconnaissance ou de synthèse de la parole.

Dans de nombreuses applications, le bruit additif est modélisé par une [[Loi gaussienne|variable aléatoire gaussienne]]. Voir [[Fonction caractéristique d'un vecteur aléatoire]] pour l'étude de la loi d'une somme de variables aléatoires indépendantes.
