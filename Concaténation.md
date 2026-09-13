## Notations
$\Sigma$ un alphabet

## Sur les mots

### Définition
$uv$ est la concaténations des [[Mot|mots]] $u$ et $v$ 
### Convention
Soit u un [[Mot|mot]] et $n \in \mathbb{N}$, $u^n$ est la concaténation de $n$ fois le mot $u$ et $u^0 = \epsilon$ 

### Propriétés
- Cette opération est une opération interne à $\Sigma^*$
- Cette opération est associative et non commutative
- $\epsilon$ est l'élément neutre pour la concaténation

## Sur les langages

### Définition
Soit $L_1$ et $L_2$ deux langages de $\Sigma^*$. Leur concaténation est définit par $L_1L_2 = \{u \in \Sigma^*|\exists (x, y) \in L_1 \times L_2 \text{ tq. } u = xy\}$.

### Propriétés
- Cette opération est associative mais non commutative
- $L^n$ est la concaténation de $n$ copies du langage $L$, par convention $L^0 = \epsilon$.