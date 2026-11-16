#dmv-subgroup_discovery

# Définition

Pour une cible numérique, les pourcentages de présence d'une cible binaire sont remplacés par la moyenne de la valeur de la cible : la fonction de qualité compare la moyenne de la cible sur les lignes couvertes par le motif à la moyenne de la cible sur l'ensemble du jeu de données, pondérée par un facteur de couverture.

$$q_M^{a}(\text{Patt}) = \left(\frac{n}{N}\right)^{a} \cdot \left(m_{\text{patt}} - m_{\text{all}}\right)$$

où $a \in [0,1]$, $n$ est le nombre de lignes couvertes par le motif $\text{Patt}$, $N$ la taille du jeu de données, $m_{\text{patt}}$ la moyenne de la cible sur les lignes couvertes par le sous-groupe et $m_{\text{all}}$ la moyenne de la cible sur l'ensemble du jeu de données.

# Interprétation

Le paramètre $a$ règle le poids donné à la taille du sous-groupe dans la qualité du motif :

- $a = 0$ : *mean gain*, la taille du sous-groupe n'est pas prise en compte et seule compte la différence des moyennes.
- $a = 0.5$ : *mean test*, la couverture intervient par sa racine carrée.
- $a = 1$ : *impact*, la couverture intervient pleinement et le gain de moyenne est multiplié par la proportion de lignes couvertes.

Suivant la valeur de $a$, un motif qui ne couvre que quelques lignes très atypiques peut donc être préféré ou écarté au profit d'un motif plus large et moins extrême.

# Remarque

Cette fonction est une [[Fonction de qualité d'un sous-groupe|fonction de qualité]] parmi d'autres : elle ne diffère des mesures construites sur les taux de présence que par le remplacement de ces taux par la moyenne de la cible.

Pour une cible binaire, la même forme donne l'[[Exactitude relative pondérée]] : le facteur de couverture $(n/N)^a$ y multiplie l'écart entre le taux de présence dans le sous-groupe et le taux global, écart qui devient un écart de moyennes lorsque la cible est numérique. Le cas $a = 1$ appliqué à une cible indicatrice coincide avec la pondération de cette exactitude relative.

Un écart nul entre les deux moyennes annule la qualité, quelle que soit la taille du sous-groupe : la fonction mesure un écart à la moyenne générale, pas la seule taille du motif.
