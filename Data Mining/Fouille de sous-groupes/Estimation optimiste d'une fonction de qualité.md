#dmv-subgroup_discovery

# Définition

Soit $q$ une [[Fonction de qualité d'un sous-groupe|fonction de qualité]] sur les [[Motif de sous-groupe|motifs de sous-groupes]]. Une estimation optimiste de $q$ est une fonction $oe$, définie sur les motifs, telle que pour tout motif $P$ et tout raffinement $P'$ de $P$ :

$$P' \supset P \implies oe(P) > q(P')$$

L'estimation ne dépend que de $P$ et majore strictement la qualité de tous les raffinements de $P$.

# Interprétation

L'estimation optimiste répond à une question locale : quelle est la meilleure qualité encore atteignable en descendant dans la partie de l'[[Espace de recherche des sous-groupes|espace de recherche]] située sous $P$ ? La réponse est bornée par $oe(P)$, et aucun raffinement de $P$ ne peut dépasser cette valeur.

Cette borne se calcule sur $P$ seul, sans parcourir ses raffinements. Elle rend donc inutile l'exploration d'une région entière de l'espace dès que sa borne est trop basse pour le critère de sélection retenu, ce qui est le mécanisme de l'[[Élagage top-k]] et, plus généralement, de la [[Recherche des sous-groupes]] exhaustive.

# Remarque

De nombreuses fonctions de qualité admettent une estimation optimiste. Si la qualité est le support, l'inclusion borne la descendance : un raffinement $P' \supset P$ couvre au plus les lignes couvertes par $P$, donc $\mathrm{support}(P') \le \mathrm{support}(P)$, mais cette borne n'est que large.

Poser $oe(P) = \mathrm{support}(P)$ ne définit donc pas une estimation optimiste : un raffinement dont le sélecteur supplémentaire ne retire aucune ligne couverte conserve le même support, si bien que $oe(P) = q(P')$, alors que la définition impose une inégalité stricte. Une estimation valide se dérive de cette borne en haussant le support d'une quantité strictement positive : pour un $\varepsilon > 0$ fixé, $oe(P) = \mathrm{support}(P) + \varepsilon$ vérifie $oe(P) > \mathrm{support}(P')$ pour tout raffinement $P'$ de $P$. La marge doit être fixée une fois pour toutes, faute de quoi $oe$ ne serait plus une fonction de $P$ seul.

Plus l'estimation est basse tout en restant valide, plus l'élagage est fort : on cherche donc une estimation valide aussi proche que possible de la qualité. Dans la famille ci-dessus, aucune marge strictement positive n'est minimale, si bien que cet optimum est approché sans être atteint.
