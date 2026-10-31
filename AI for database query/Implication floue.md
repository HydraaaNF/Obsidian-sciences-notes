# Définition
**Cas classique.** L'inclusion classique s'exprime par une implication :

$$
(A \subset B) \iff (\forall x \in X,\; x \in A \implies x \in B)
$$

**Cas classique.** Table de vérité de $p \implies q$ :

| $p \backslash q$ | vrai | faux |
| --- | --- | --- |
| **vrai** | vrai | faux |
| **faux** | vrai | vrai |

On a $(p \implies q) \iff (\neg p \lor q)$.

**Cas flou.** Une **implication floue** est une application

$$
\Rightarrow_f \;:\; [0, 1] \times [0, 1] \to [0, 1], \qquad (p, q) \mapsto (p \Rightarrow_f q)
$$

# Propriétés
Toute implication floue doit vérifier :
- **monotonie en $p$** : $\forall q \in [0, 1]$, si $p_1 < p_2$ alors $(p_1 \Rightarrow_f q) \geq (p_2 \Rightarrow_f q)$ ;
- **monotonie en $q$** : $\forall p \in [0, 1]$, si $q_1 < q_2$ alors $(p \Rightarrow_f q_1) \leq (p \Rightarrow_f q_2)$ ;
- $\forall q \in [0, 1],\; (0 \Rightarrow_f q) = 1$ ;
- $\forall p \in [0, 1],\; (p \Rightarrow_f 1) = 1$.

On considère parfois une propriété supplémentaire : $(1 \Rightarrow_f q) = q$.

# Remarque
Il existe deux familles d'implications floues : les [[Implication de type S|S-implications]] et les [[Implication de type R|R-implications]]. Elles servent à définir l'[[Inclusion graduelle par une implication floue]]. Comparaison : [[Comparaison des implications floues]].
