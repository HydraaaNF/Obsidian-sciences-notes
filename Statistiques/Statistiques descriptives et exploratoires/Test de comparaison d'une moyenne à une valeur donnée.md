# Modèle

Un test de comparaison d'une moyenne à une valeur donnée confronte une [[Hypothèse nulle et hypothèse alternative|hypothèse nulle]] $H_0$ à une hypothèse alternative $H_1$, à partir d'un [[Échantillon et échantillonnage|échantillon]] $(X_1, \dots, X_n)$ de loi mère [[Loi gaussienne|gaussienne]] $\mathcal{N}(m, \sigma^2)$. On teste l'hypothèse nulle

$$H_0 : m = m_0,$$

où $m_0$ est la valeur donnée, contre l'une des deux hypothèses alternatives suivantes :

- $H_1 : m \neq m_0$, et le test est dit **bilatéral** ;
- $H_1 : m > m_0$, et le test est dit **unilatéral**.

L'hypothèse alternative est parfois simple (elle fixe alors la valeur de $m$, comme $H_1 : m = 650$ dans l'exemple des faiseurs de pluie ci-dessous), parfois composite ($H_1 : m \neq m_0$, $H_1 : m > m_0$).

D'après le [[Théorème de Student pour la moyenne empirique|théorème de Student pour la moyenne empirique]], la variable aléatoire

$$T_{n-1} = \frac{\overline{X} - m}{\sqrt{\frac{S'^2}{n}}} \sim \mathcal{T}_{n-1}$$

suit une [[Loi de Student|loi de Student]] à $n-1$ degrés de liberté, où $\overline{X} = \frac{1}{n} \sum_{i=1}^{n} X_i$ est la [[Moyenne empirique|moyenne empirique]] et $S'^2 = \frac{1}{n-1} \sum_{i=1}^{n} (X_i - \overline{X})^2$ la [[Loi de la variance empirique corrigée|variance empirique corrigée]]. Sous $H_0$, la [[Statistique de test|statistique de test]] s'écrit donc

$$T_{n-1} = \frac{\overline{X} - m_0}{\sqrt{\frac{S'^2}{n}}} \sim \mathcal{T}_{n-1}.$$

La forme de la [[Zone critique et seuil d'un test|zone critique]] dépend de l'hypothèse alternative :

- **Test bilatéral** ($H_1 : m \neq m_0$). La zone critique est de la forme $[-a, a]^c$, c'est-à-dire $]-\infty, -a[ \cup ]a, +\infty[$ : on rejette $H_0$ lorsque l'estimation $\overline{x}$ de $m$ est très éloignée de $m_0$, c'est-à-dire lorsque la valeur observée de $T_{n-1}$ est éloignée de $0$. Le seuil $a$ est déterminé par

$$\mathbb{P}_{H_0}[-a \leq T_{n-1} \leq a] = 1 - \alpha.$$

- **Test unilatéral** ($H_1 : m > m_0$). La zone critique est de la forme $]b, +\infty[$ : on rejette $H_0$ et on accepte $H_1$ si l'estimation $\overline{x}$ de $m$ est nettement supérieure à $m_0$. Le seuil $b$ est déterminé par

$$\mathbb{P}_{H_0}[T_{n-1} \leq b] = 1 - \alpha.$$

Dans les deux cas, la règle de décision est la même : si la valeur observée de la statistique de test appartient à la zone critique, on rejette $H_0$ et on accepte $H_1$ au [[Risque de première espèce|risque de première espèce]] $\alpha$ ; sinon, rien ne contredit $H_0$ et on conserve $H_0$.

# Exemple

**Les faiseurs de pluie.** Le niveau naturel des pluies dans la Beauce, en millimètres par an, suit une [[Loi gaussienne|loi normale]] $\mathcal{N}(600, 100^2)$. Des entrepreneurs prétendaient pouvoir augmenter le niveau moyen de pluie de 50 mm par an, par insémination des nuages au moyen d'iodure d'argent ; le procédé fut mis à l'essai durant 9 années et l'on releva les hauteurs de pluie suivantes :

| Année | 1951 | 1952 | 1953 | 1954 | 1955 | 1956 | 1957 | 1958 | 1959 |
|---|---|---|---|---|---|---|---|---|---|
| Niveau (mm) | 510 | 614 | 780 | 512 | 501 | 534 | 603 | 788 | 650 |

On note $X$ la variable aléatoire désignant la hauteur de pluie en millimètres par an. Les 9 observations ont pour moyenne empirique $\overline{x} = 610{,}2$ mm. Que peut-on conclure ? Deux hypothèses se confrontent :

- $H_0$ : *l'insémination est sans effet* ;
- $H_1$ : *l'insémination augmente réellement le niveau moyen de 50 mm par an*.

Plus formellement, ces hypothèses s'écrivent $H_0 : m = 600$ et $H_1 : m = 650$ : la valeur donnée est ici $m_0 = 600$.

**Bruit : test bilatéral.** Un échantillon de $n = 30$ observations d'un bruit, de loi mère gaussienne $\mathcal{N}(m, \sigma^2)$, donne une moyenne observée $\overline{x} = 0{,}81$ et un écart-type empirique corrigé $s' = 1{,}75$. On teste l'hypothèse simple $H_0 : m = 0$ contre l'hypothèse composite $H_1 : m \neq 0$. D'après le [[Théorème de Student pour la moyenne empirique|théorème de Student pour la moyenne empirique]],

$$T_{n-1} = \frac{\overline{X} - m}{\sqrt{\frac{S'^2}{n}}} \sim \mathcal{T}_{n-1},$$

où $n = 30$ ; par conséquent, sous $H_0$, la [[Statistique de test|statistique de test]] est

$$T_{29} = \frac{\overline{X}}{S'}\sqrt{30} \sim \mathcal{T}_{29}.$$

D'après l'hypothèse $H_1$, la forme de la zone critique est $[-a, a]^c$, c'est-à-dire $]-\infty, -a[ \cup ]a, +\infty[$ : on rejette $H_0$ lorsque l'estimation $\overline{x}$ du paramètre $m$ est très éloignée de $0$, c'est-à-dire lorsque la valeur observée de $T_{29}$ est éloignée de $0$. Pour déterminer $a$, on cherche dans la table de la loi de Student le seuil $a$ tel que

$$\mathbb{P}_{H_0}[-a \leq T_{29} \leq a] = 1 - \alpha.$$

Pour un risque de première espèce $\alpha = 0{,}1$, on obtient la valeur $a = 1{,}699$.

*Règle de décision :*

- si $\frac{\overline{x}}{s'}\sqrt{30} \in [-a, a]$, rien ne contredit $H_0$ (cet événement a a priori une probabilité $0{,}9$ de se produire) : on conserve alors $H_0$ ;
- si $\frac{\overline{x}}{s'}\sqrt{30} \notin [-a, a]$, on rejette $H_0$ et on accepte $H_1$ au risque de première espèce $\alpha$ ; autrement dit, on peut affirmer que le bruit n'est pas centré avec un risque de se tromper de 10 %.

*Application numérique :*

$$\begin{aligned} \frac{\overline{x}}{s'}\sqrt{30} &= \frac{0{,}81}{1{,}75}\sqrt{30} \\ &= 2{,}535. \end{aligned}$$

Comme l'observation de la statistique de test est dans la zone critique, c'est-à-dire $2{,}535 \notin [-1{,}699 ; 1{,}699]$, on rejette $H_0$ au risque de première espèce $\alpha = 0{,}1$ : *on affirme que le bruit n'est pas centré avec un risque de se tromper de 10 %.*

*Remarques :*

- $H_1$ est une hypothèse composite, et non une hypothèse simple comme $H_1 : m = 650$ dans l'exemple des faiseurs de pluie : on ne peut donc pas calculer le [[Risque de seconde espèce|risque de seconde espèce]]. En effet, pour calculer $\beta$, il faut connaître sous $H_1$ la loi de la statistique de test, qui dépend de la valeur de $m$ ; or $H_1 : m \neq 0$ ne fixe pas cette valeur.
- Étant donné que l'on rejette $H_0$, on peut essayer de diminuer le risque $\alpha$ que l'on prend en acceptant $H_1$. Pour cela, on considère la table de la loi de Student $\mathcal{T}_{29}$ et on cherche la valeur $t$ la plus proche de $2{,}535$ tout en restant inférieure. On obtient $t = 2{,}462$ et ce seuil correspond à un risque $\alpha = 0{,}02$, c'est-à-dire

$$\mathbb{P}_{H_0}[-2{,}462 \leq T_{29} \leq 2{,}462] = 0{,}98.$$

Ainsi, on peut rejeter $H_0$ et affirmer que le bruit n'est pas centré avec un risque d'erreur de 2 %.

Pour un risque $\alpha = 1$ %, la zone critique devient $]-\infty, -2{,}756[ \cup ]2{,}756, +\infty[$ ; comme $2{,}535 \notin ]-\infty, -2{,}756[ \cup ]2{,}756, +\infty[$, on accepte $H_0$. Autrement dit, on peut affirmer que $H_1$ est vraie avec un risque d'erreur $\alpha = 2$ %, mais on ne peut soutenir cette proposition avec un risque d'erreur $\alpha = 1$ %.

**Bruit : test unilatéral.** D'après les observations, il semble plus indiqué de modifier $H_1$ pour tester

$$H_0 : m = 0 \quad \text{contre} \quad H_1 : m > 0.$$

Sous $H_0$, on a toujours

$$T_{29} = \frac{\overline{X}}{S'}\sqrt{30} \sim \mathcal{T}_{29}.$$

Cependant, la zone critique est à présent de la forme $]b, +\infty[$ : on rejette $H_0$ et on accepte $H_1$ si l'estimation $\overline{x}$ de $m$ est nettement positive. On cherche donc dans la table de la loi de Student à $29$ degrés de liberté le seuil $b$ tel que

$$\mathbb{P}_{H_0}[T_{29} \leq b] = 1 - \alpha.$$

On obtient :

- pour $\alpha = 5$ %, le seuil $b = 1{,}699$ : comme l'observation de $T_{29}$ est dans la zone critique ($2{,}535 > 1{,}699$), *on peut rejeter $H_0$ et affirmer que l'espérance du bruit est positive avec un risque de se tromper de 5 %*. Ainsi, en modifiant $H_1$, on rejette $H_0$ avec un risque plus faible et on accepte une hypothèse $H_1$ plus précise ;
- pour $\alpha = 1$ %, le seuil $b = 2{,}462$ : on rejette de nouveau $H_0$ ; on peut affirmer que $m$ est strictement positif avec un risque d'erreur d'au plus 1 %.

# Remarque

La statistique de test $T_{n-1} = \frac{\overline{X} - m}{S'}\sqrt{n}$ suit une loi de Student à $n - 1$ degrés de liberté car $(X_1, \dots, X_n)$ est un échantillon de loi gaussienne. Cependant, dans le cas d'un échantillon de grande taille, l'hypothèse gaussienne n'est pas nécessaire : lorsque $n$ est grand, on peut approcher la loi de $T_{n-1}$ par une [[Loi gaussienne|loi normale]] $\mathcal{N}(0, 1)$.

L'écriture « sous $H_1$, on sait juste $m > 0$ » est une erreur fréquente lorsque $H_1 : m \neq 0$ : l'hypothèse alternative signifie que $m$ est non nul, et non qu'il est positif ; c'est le fait que $m$ ne soit pas fixé sous $H_1$ qui empêche de calculer le risque de seconde espèce.

La zone critique d'un test bilatéral est la réunion des deux queues symétriques de la loi de Student, $]-\infty, -a[ \cup ]a, +\infty[$ ; la restreindre à la seule queue $]a, +\infty[$ est une erreur fréquente, car une observation fortement négative de la statistique doit également conduire à rejeter $H_0$.
