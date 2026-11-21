# Définition
Soit $r$ une [[Relation floue]] de schéma $X$ et $Y$ un sous-ensemble de $X$ :

$$
\pi_Y(r) = \Big\{\mu / v \ \Big|\ \exists u \in \operatorname{supp}(r),\ u.Y = v,\ \mu = \max_{u' \in \operatorname{supp}(r),\ u'.Y = v} \mu_r(u')\Big\}
$$

Les n-uplets qui ont la même valeur $v$ sur $Y$ sont fusionnés, avec le maximum de leurs degrés.

# Exemple
Relation $\text{BienPayé}$ :

| id | nom | poste | … | $\mu$ |
| --- | --- | --- | --- | --- |
| 3 | Dupont | … | … | 0,8 |
| 5 | Durand | … | … | 0,6 |
| 17 | Dupont | … | … | 0,4 |

$\pi_{\text{nom}}(\text{BienPayé})$ :

| nom | $\mu$ |
| --- | --- |
| Dupont | 0,8 |
| Durand | 0,6 |

Les deux n-uplets Dupont sont fusionnés, avec le maximum de leurs degrés.
