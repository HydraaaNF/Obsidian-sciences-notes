# Définition

Un test statistique confronte une **hypothèse nulle** $H_0$ (l'hypothèse de travail) aux données observées : si ces données sont en contradiction (ou plus précisément très improbables) avec l'hypothèse de travail $H_0$, alors on rejette $H_0$ et on accepte l'**hypothèse alternative** $H_1$ ; à défaut du contraire, on conserve $H_0$.

On effectue un test d'**hypothèses simples** lorsque l'on teste l'égalité d'un paramètre à une valeur donnée, par exemple

$$H_0 : m = 600 \text{ contre } H_1 : m = 650.$$

Lorsque l'hypothèse alternative ne se réduit pas à une valeur donnée (par exemple une hypothèse composite telle $m > 600$), le test oppose une hypothèse simple à une hypothèse composite.

# Algorithme

Règle de décision d'un test.

1. On choisit une [[Statistique de test|statistique de test]], la variable aléatoire dont la loi et l'observation permettent de procéder au test et de prendre une décision. Ici, on choisit $\overline{X}$ comme estimateur de $m$ : l'échantillon $(X_1, \dots, X_9)$ étant issu d'une loi $\mathcal{N}(m, 100^2)$, la variable aléatoire $\overline{X}$ est distribuée selon la loi $\mathcal{N}(m, 100^2/9)$, soit, sous $H_0$,

$$\overline{X} \sim \mathcal{N}\left(600, \frac{100^2}{9}\right).$$

Étant donné que l'échantillon est de petite taille, il est nécessaire de manipuler des lois exactes et non asymptotiques pour réaliser le test.

2. On détermine un intervalle $\mathcal{D}$ contenant $\overline{X}$ avec une grande probabilité (par exemple $1 - \alpha = 0{,}90$ ou $0{,}95$) sous l'hypothèse $H_0$.

3. On décide :

- si l'observation $\overline{x}$ de la variable aléatoire $\overline{X}$ (ici $\overline{x} = 610{,}2$) est dans cet intervalle $\mathcal{D}$, il n'y a pas de contradiction avec $H_0$ et rien ne permet d'affirmer que $H_0$ est fausse : on conserve $H_0$ ;
- sinon ($\overline{x} \notin \mathcal{D}$), on rejette $H_0$ et on accepte $H_1$, avec toutefois une probabilité $\alpha$ de se tromper en faisant ce choix : l'observation est tombée dans la [[Zone critique et seuil d'un test|zone critique]] du test. En effet, sous $H_0$, l'intervalle $\mathcal{D}$ contient $\overline{X}$ avec une forte probabilité ; le fait que l'observation $\overline{x}$ ne soit pas dans cet intervalle remet en doute $H_0$, et si $H_0$ est vraie, la probabilité que $\overline{X}$ ne soit pas dans $\mathcal{D}$ est seulement de $\alpha$.

# Interprétation

En résumé, les issues possibles d'un test se lisent dans le tableau de décision d'un test, qui croise la décision prise (lignes) et la vérité (colonnes) :

| Décision<br>Vérité | $H_0$ | $H_1$ |
|---|---|---|
| $H_0$ | $1 - \alpha$ | $\beta$ |
| $H_1$ | $\alpha$ | $1 - \beta$ |

Dans ce tableau, $\alpha$ est le [[Risque de première espèce|risque de première espèce]], $\beta$ le [[Risque de seconde espèce|risque de seconde espèce]] et $1 - \beta$ la [[Puissance d'un test|puissance du test]].

# Exemple

Un canal de transmission ajoute un bruit aléatoire $X_t$ à tout signal $f(t)$ déterministe qu'il transmet. Pour tout $t > 0$, la variable aléatoire $X_t$ est distribuée selon une loi normale $\mathcal{N}(m, \sigma^2)$ ; autrement dit, si $f(t)$ est la valeur du signal à l'entrée du canal à l'instant $t$, la valeur de sortie correspondante est une valeur aléatoire $f(t) + X_t$ de loi $\mathcal{N}(f(t) + m, \sigma^2)$.

Afin d'étudier le bruit de transmission, on envoie un signal constant dans le canal et on observe la réponse. On fait 30 observations à des instants choisis de manière aléatoire et on calcule les erreurs observées :

$$\bar{x} = \frac{1}{30}\sum_{i=1}^{30} X_{t_i}(\omega) = \frac{1}{30}\sum_{i=1}^{30} x_i = 0{,}81$$

$$s' = \sqrt{\frac{1}{29}\sum_{i=1}^{30}(x_i-\bar{x})^2} = 1{,}75.$$

La valeur moyenne $\bar{x}$ des erreurs paraît importante pour un bruit a priori centré (i.e. $m = 0$). Afin de décider si le bruit est effectivement centré, on effectue un [[Test de comparaison d'une moyenne à une valeur donnée|test de comparaison d'une moyenne à une valeur donnée]] : l'hypothèse d'un bruit centré ($m = 0$) est une hypothèse simple, l'hypothèse alternative sur $m$ est composite.

# Remarque

Il est possible que l'effet étudié soit réel sans que son ampleur soit exactement celle annoncée, par exemple une augmentation du niveau des pluies inférieure à 50 mm. Néanmoins, dès lors que l'hypothèse avancée porte sur une augmentation précise de 50 mm, on teste $H_0$ contre $H_1$ (où $m = 650$) et non contre une hypothèse composite telle $m > 600$.
