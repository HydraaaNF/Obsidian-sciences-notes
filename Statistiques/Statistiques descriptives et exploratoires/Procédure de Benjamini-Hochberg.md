# Définition

La procédure de Benjamini-Hochberg est une règle de rejet portant sur $m$ tests simultanés. Elle contrôle le **taux de fausses découvertes** (FDR, *false discovery rate*), défini comme l'espérance de la proportion de tests qui rejettent l'hypothèse nulle alors qu'ils ne le devraient pas, parmi l'ensemble des tests rejetés. En notant $V$ le nombre de tests rejetant $H_0$ à tort et $R$ le nombre total de tests rejetés :

$$
\text{FDR} = \mathbb{E}\left[\frac{V}{\max(R, 1)}\right]
$$

# Algorithme

À partir des p-values $p_1, \dots, p_m$ des $m$ tests, pour un seuil $\alpha$ :

1. Trier les p-values par ordre croissant :

$$
p_{(1)} \leqslant p_{(2)} \leqslant \cdots \leqslant p_{(m)}
$$

2. Trouver le plus grand $k$ tel que

$$
p_{(k)} \leqslant \frac{k}{m}\,\alpha
$$

3. Rejeter l'hypothèse nulle pour $H_{(1)}, \dots, H_{(k)}$, où $H_{(i)}$ désigne l'hypothèse nulle dont la p-value est $p_{(i)}$.

# Interprétation

Là où un [[Méta-test]] rejette dès qu'un seul des $m$ tests rejette, la procédure de Benjamini-Hochberg raisonne sur l'ensemble des rejets et en borne la qualité : le FDR mesure la proportion attendue de faux rejets parmi les rejets, et lorsque les tests sont indépendants, la procédure garantit que cette proportion reste inférieure ou égale au seuil $\alpha$. Elle tolère donc une fraction attendue de faux rejets au lieu d'interdire toute erreur.

C'est ce qui la rend moins conservatrice que la [[Correction de Bonferroni]], qui contrôle le taux d'erreur global de la famille (FWER), à savoir la probabilité qu'au moins un test rejette l'hypothèse nulle alors qu'elle est vraie : exiger l'absence de toute erreur conduit à rejeter moins d'hypothèses.

# Remarque

L'algorithme s'arrête au plus grand indice $k$ satisfaisant le seuil, mais rejette toutes les hypothèses $H_{(1)}, \dots, H_{(k)}$ : une hypothèse de rang $i < k$ est donc rejetée même si $p_{(i)}$ dépasse son seuil individuel $\frac{i}{m}\,\alpha$. Il suffit que la plus grande p-value retenue franchisse son propre seuil.

Une confusion fréquente consiste à définir le FDR comme l'espérance du nombre de faux rejets, c'est-à-dire $\mathbb{E}[V]$ : cette quantité, parfois appelée taux d'erreur par famille, augmente avec le nombre $m$ de tests et n'est pas bornée par $\alpha$. Le FDR est une proportion, $\mathbb{E}[V/\max(R, 1)]$, dont l'espérance est bornée par $\alpha$ ; les deux quantités diffèrent dès que $R$ est aléatoire et ne doivent pas être confondues.
