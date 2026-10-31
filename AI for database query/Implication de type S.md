# Définition
Une **S-implication** (S pour *strong*) part de l'équivalence classique $(p \implies q) \iff (\neg p \lor q)$ et utilise une [[Conorme triangulaire]] $\bot$ :

$$
(p \Rightarrow_f q) = \bot(1 - p,\; q)
$$

# Propriétés
- Les S-implications vérifient la **contraposition** : $(p \Rightarrow_f q) = (\neg q \Rightarrow_f \neg p)$.
- Pour toute S-implication : $(1 - p) \leq (p \Rightarrow_S q)$.

### Démonstration
Contraposition :

$$
(\neg q \Rightarrow_f \neg p) = \bot\big(1 - (1 - q),\; 1 - p\big) = \bot(q,\; 1 - p) = \bot(1 - p,\; q) = (p \Rightarrow_f q)
$$

La dernière étape utilise la commutativité de $\bot$.

# Exemple
S-implications usuelles :

| Nom | Définition | $\bot$ sous-jacente |
| --- | --- | --- |
| [[Implication de Kleene-Dienes\|Kleene-Dienes]] | $\max(1 - p,\; q)$ | $\max(u, v)$ |
| [[Implication de Reichenbach\|Reichenbach]] | $1 - p + pq$ | $u + v - uv$ |
| [[Implication de Łukasiewicz\|Łukasiewicz]] | $\min(1 - p + q,\; 1)$ | $\min(u + v,\; 1)$ |

# Remarque
Voir [[Comparaison des implications floues]]. Famille duale : [[Implication de type R]].
