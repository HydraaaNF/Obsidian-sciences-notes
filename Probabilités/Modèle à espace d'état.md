# Définition

Un **modèle à espace d'état** décrit conjointement deux [[Processus stochastique|processus stochastiques]], un état $X_k$ et une observation $Y_k$, par les équations

$$X_k \doteq f(X_{k-1}, W_k)$$
$$Y_k \doteq g(X_k, V_k)$$

où les bruits $V_k$ et $W_k$ sont des variables aléatoires indépendantes et identiquement distribuées (iid).

# Remarque

L'état et l'observation portent le même indice : l'équation s'écrit $Y_k \doteq g(X_k, V_k)$. Écrire $Y_K$ (un indice différent de celui de l'état $X_k$ et du bruit $V_k$ de la même équation) est une erreur fréquente.

Un modèle à espace d'état généralise le [[Modèle de Markov caché]].
