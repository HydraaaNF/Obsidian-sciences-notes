## Définition
La fonction de transition peut être étendue de manière récursive en la fonction $\delta^*$ de $Q \times \Sigma^* \to Q$ par :
- $\delta^*(q, u) = \delta(q, u) \text{ si } |u| = 1$
- $\delta^*(q, au) = \delta^*(\delta(q, a), u)$
Donc le langage reconnu par un automate A est $L(A) = \{u \in \Sigma^*|\delta^*(q_0, u) \in F\}$
