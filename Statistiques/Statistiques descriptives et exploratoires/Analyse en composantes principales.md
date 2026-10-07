# Définition

L'**analyse en composantes principales** (ACP) est une méthode de [[Projection linéaire des données|projection linéaire]] : on se restreint aux transformations linéaires, c'est-à-dire que

1. la nouvelle référence $\mathbf{u}$ est une combinaison linéaire de $\mathbf{v}$ ;
2. $\mathbf{x}_u$ est une combinaison linéaire de $\mathbf{x}_v$, éventuellement avec réduction de dimension.

La projection d'une observation s'écrit

$$\mathbf{y}_{q \times 1} = \mathbf{U}_{q \times p} \mathbf{x}_{p \times 1}$$

soit, en détaillant les composantes,

$$\begin{pmatrix} y_1 \\ \vdots \\ y_q \end{pmatrix} = \begin{pmatrix} u_{11} & \cdots & u_{1p} \\ \vdots & \ddots & \vdots \\ u_{q1} & \cdots & u_{qp} \end{pmatrix} \begin{pmatrix} x_1 \\ \vdots \\ x_p \end{pmatrix}$$

# Interprétation

L'ACP remplace les variables corrélées $\mathbf{x}_1 \dots \mathbf{x}_p$ par de nouvelles variables, les composantes principales $\mathbf{c}_1 \dots \mathbf{c}_q$, combinaisons linéaires non corrélées des variables $\mathbf{x}_i$ de variance maximale ; lorsque $q < p$, elle réalise une réduction de dimension.

Le [[Vocabulaire de l'analyse en composantes principales]] définit les axes principaux, les facteurs et les composantes principales ; la construction de la projection est décrite dans l'[[Algorithme de l'analyse en composantes principales]] et son optimalité est établie par les [[Théorèmes de l'analyse en composantes principales]]. Le nombre de composantes à retenir s'appuie sur l'[[Éboulis des valeurs propres]], et la [[Qualité d'une analyse en composantes principales]] rassemble les mesures permettant d'évaluer la représentation obtenue. Pour d'autres approches de réduction de dimension, voir l'[[Analyse factorielle]].

# Exemple

## Consommation alimentaire des Français

La consommation des huit aliments suivants : pain ordinaire (PAO), autre pain (PAA), vin ordinaire (VIO), autre vin (VIA), pommes de terre (POT), légumes secs (LEC), raisin de table (RAI) et plats préparés (PLP), est relevée pour huit catégories socioprofessionnelles :

| Catégorie socioprofessionnelle | Sigle | Pain ordinaire (PAO) | Autre pain (PAA) | Vin ordinaire (VIO) | Autre vin (VIA) | Pommes de terre (POT) | Légumes secs (LEC) | Raisin de table (RAI) | Plats préparés (PLP) |
|---|---|---|---|---|---|---|---|---|---|
| Exploitants agricoles | AGRI | 167 | 1 | 163 | 23 | 41 | 8 | 6 | 6 |
| Salariés agricoles | SAAG | 162 | 2 | 141 | 12 | 40 | 12 | 4 | 15 |
| Professions indépendantes | PRIN | 119 | 6 | 69 | 56 | 39 | 5 | 13 | 41 |
| Cadres supérieurs | CSUP | 87 | 11 | 63 | 111 | 27 | 3 | 18 | 39 |
| Cadres moyens | CMOY | 103 | 5 | 68 | 77 | 32 | 4 | 11 | 30 |
| Employés | EMPL | 111 | 4 | 72 | 66 | 34 | 6 | 10 | 28 |
| Ouvriers | OUVR | 130 | 3 | 76 | 52 | 43 | 7 | 7 | 16 |
| Inactifs | INAC | 138 | 7 | 117 | 74 | 53 | 8 | 12 | 20 |

Les coefficients de corrélation linéaire entre ces huit variables, exprimés en %, sont :

| | PAO | PAA | VIO | VIA | POT | LEC | RAI | PLP |
|---|---|---|---|---|---|---|---|---|
| PAO | 100 | | | | | | | |
| PAA | -75 | 100 | | | | | | |
| VIO | 83 | -57 | 100 | | | | | |
| VIA | -89 | 90 | -73 | 100 | | | | |
| POT | 66 | -30 | 52 | -40 | 100 | | | |
| LEC | 90 | -66 | 80 | -84 | 61 | 100 | | |
| RAI | -82 | 96 | -65 | 91 | -42 | -82 | 100 | |
| PLP | 85 | 78 | -82 | 72 | -55 | -73 | 85 | 100 |

Les valeurs propres, l'inertie associée et l'inertie cumulée (en %) sont :

| λ | 6.21 | 0.89 | 0.42 | 0.32 | 0.14 | 0.01 | 0.005 |
|---|---|---|---|---|---|---|---|
| Inertie (en %) | 77.57 | 11.21 | 5.26 | 3.99 | 1.74 | 0.11 | 0.06 |
| Cumulée | 77.57 | 88.78 | 94.04 | 98.0 | 99.8 | 99.9 | 100 |

La projection des observations sur les deux premiers axes sépare, sur le premier axe, les cadres (CSUP, PRIN) des exploitants et salariés agricoles (AGRI, SAAG), tandis que les inactifs (INAC) se détachent sur le deuxième axe. Le cercle des corrélations oppose, sur le premier axe, la consommation de pain ordinaire, de légumes secs, de vin ordinaire et de pommes de terre à celle d'autre pain, de raisin de table, d'autre vin et de plats préparés.

## Reconnaissance de visages (eigenfaces)

Un visage est représenté par un vecteur de pixels. L'ACP permet de trouver les composantes principales de l'ensemble des visages, les **eigenfaces** : on considère alors l'espace des paramètres (de taille $M$) plutôt que l'espace image (de taille $N^2$). Chaque visage est représenté par une combinaison linéaire des eigenfaces. Voir [[Eigenfaces]].

## Analyse sémantique latente

Chaque document est un sac de mots dans $\mathbb{R}^d$, où $d$ est le nombre de termes d'index et où $x_{ji}$ est proportionnel à la fréquence du terme $j$ dans le document $i$ :

$$\begin{gathered}\mathbf{X}_{d\times n} \approx \mathbf{U}_{d\times r}\mathbf{Z}_{r\times n}\\[4pt]\begin{pmatrix}\text{stocks: }2 & \cdots & 0\\\text{chairman: }4 & \cdots & 1\\\text{the: }8 & \cdots & 7\\\vdots & \cdots & \vdots\\\text{wins: }0 & \cdots & 2\\\text{game: }1 & \cdots & 3\end{pmatrix}\approx\begin{pmatrix}0.4 & \cdots & -0.001\\0.8 & \cdots & 0.03\\0.01 & \cdots & 0.04\\\vdots & \cdots & \vdots\\0.002 & \cdots & 2.3\\0.003 & \cdots & 1.9\end{pmatrix}\begin{pmatrix}| & & |\\\mathbf{z}_1 & \cdots & \mathbf{z}_n\\| & & |\end{pmatrix}\end{gathered}$$

Les documents sont mieux représentés dans le sous-espace des concepts obtenu par ACP sur la matrice termes/documents. Voir [[Analyse sémantique latente]].

# Remarque

L'ACP ignore l'information de classe des échantillons : l'appartenance d'un échantillon à une classe n'intervient pas dans la recherche des composantes. Deux classes de points se projettent ainsi avec recouvrement sur l'axe de l'ACP, alors que l'axe de l'[[Analyse discriminante linéaire]], qui exploite cette information, les sépare.
