#adm-9

# Définition

On considère une famille de $m$ tests d'hypothèses, le test $i$ opposant une hypothèse nulle $H_{0,i}$ à une hypothèse alternative $H_{1,i}$ et produisant une p-value $p_i$. Pour un niveau $\alpha$ fixé, la **correction de Bonferroni** rejette l'hypothèse nulle de chaque test $i$ dont la p-value vérifie

$$p_i \leqslant \frac{\alpha}{m}$$

# Interprétation

La correction contrôle le taux d'erreur global de la famille de tests, ou *family-wise error rate* (FWER), c'est-à-dire la probabilité qu'au moins un des $m$ tests rejette une hypothèse nulle qui est vraie :

$$\text{FWER} = \mathbb{P}[\text{au moins un test rejette l'hypothèse nulle à tort}]$$

Chaque test est ramené au niveau $\alpha/m$ au lieu de $\alpha$ : plus la famille compte de tests, plus le seuil de rejet de chacun est exigeant. Le [[Risque de première espèce|risque de première espèce]] de chaque test individuel diminue d'autant, ce qui compense l'accumulation des tests décrite par le [[Méta-test]].

Sous réserve que chaque p-value soit valide, c'est-à-dire que $\mathbb{P}[p_i \leqslant t] \leqslant t$ sous $H_{0,i}$, l'inégalité de Boole, ou sous-additivité d'une probabilité, appliquée aux seuls tests dont l'hypothèse nulle est vraie, donne

$$\text{FWER} = \mathbb{P}\left[\bigcup_{i \in I_0} \{p_i \leqslant \alpha/m\}\right] \leqslant \sum_{i \in I_0} \frac{\alpha}{m} = |I_0| \frac{\alpha}{m} \leqslant \alpha$$

où $I_0 = \{i \mid H_{0,i} \text{ vraie}\}$ et où $|I_0| \leqslant m$ est le nombre de tests dont l'hypothèse nulle est vraie. Le FWER est donc majoré par $\alpha$, quelle que soit la dépendance entre les tests.

# Remarque

La correction de Bonferroni est plus conservatrice que la [[Procédure de Benjamini-Hochberg]] : cette dernière contrôle le taux de fausses découvertes (FDR) avec des seuils $k\alpha/m$ plus permissifs, si bien qu'elle rejette au moins autant d'hypothèses nulles. Le contrôle du FWER est le plus strict des deux, au prix d'une [[Puissance d'un test|puissance]] plus faible.
