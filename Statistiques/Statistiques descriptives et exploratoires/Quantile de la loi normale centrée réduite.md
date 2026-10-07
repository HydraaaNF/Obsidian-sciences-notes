# Définition

Soit $Z \sim \mathcal{N}(0,1)$ une [[Loi gaussienne|variable aléatoire de loi normale centrée réduite]]. Pour un risque $\alpha \in ]0, 1[$ (par exemple, $\alpha = 0,1$ ou $\alpha = 0,05$), on détermine à l'aide de la table de la loi normale centrée réduite le réel $u_{\frac{\alpha}{2}}$, appelé **quantile** de la loi normale centrée réduite, tel que

$$\mathbb{P}\left[ Z \in \left[ -u_{\frac{\alpha}{2}}, u_{\frac{\alpha}{2}} \right] \right] = 1 - \alpha.$$

# Interprétation

$u_{\frac{\alpha}{2}}$ définit l'intervalle centré en $0$ à risques symétriques $\left[ -u_{\frac{\alpha}{2}}, u_{\frac{\alpha}{2}} \right]$ : la variable $Z$ y tombe avec probabilité $1 - \alpha$.

# Remarque

Par symétrie de la loi normale centrée réduite, la définition équivaut à

$$\mathbb{P}\left[ Z \leq u_{\frac{\alpha}{2}} \right] = 1 - \frac{\alpha}{2}.$$

Autrement dit, $u_{\frac{\alpha}{2}}$ est le quantile d'ordre $1 - \frac{\alpha}{2}$ de la loi $\mathcal{N}(0,1)$ ; il intervient dans la construction de l'[[Intervalle de confiance de la moyenne d'une loi normale de variance connue]].
