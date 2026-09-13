# Définition
Soit $\Omega$ un ensemble (non vide) et soit $\mathcal{F}$ une [[Tribu|tribu]] de parties de $\Omega$. On appelle probabilité sur $\mathcal{F}$ une application $p$ définie sur $\mathcal{F}$ et à valeurs dans $[0, 1]$ vérifiant:
- $p(\Omega) = 1$
- Pour toute suite $(A_n)_{n \in \mathbb{N}}$ d'éléments de $\mathcal{F}$ vérifiant $n \neq m \implies A_n \cap A_m = \emptyset$, on a $p(\bigcup_{n \in \mathbb{N}} A_n) = \sum_{n \in \mathbb{N}} p(A_n)$
Le triplet $(\Omega, \mathcal{F}, p)$ est appelé espace probabilisé.

# Propriétés
Soit $(\Omega, \mathcal{F}, p)$ un espace probabilisé. On a:
- $p(\emptyset) = 0$.
- Si $A$ et $B$ sont deux évènements vérifiant $A \subset B$, on a $p(A) \leq p(B)$ et $p(B \setminus A) = p(B) - p(A)$
- $\forall (A, B) \in \mathcal{F}^2, p(A \cup B) = p(A) + p(B) - p(A \cap B)$
- Soit $(A_n)_{n \in \mathbb{N}}$ un suite croissante d'évènements alors $p(\bigcup_{n \in \mathbb{N}} A_n) = lim_{n \to +\infty} p(A_n)$
- Soit $(A_n)_{n \in \mathbb{N}}$ une suite décroissante d'évènements alors $p(\bigcap_{n \in \mathbb{N}} A_n) = lim_{n \to +\infty} p(A_n)$