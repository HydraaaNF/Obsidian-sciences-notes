# Définition

La définition de la [[Probabilité conditionnelle]] conduit à la **règle de multiplication**, ou règle des **probabilités composées**. Pour deux [[Évènement|évènements]] $A$ et $B$ :

$$
\mathbb{P}[A \cap B] =
\begin{cases}
\mathbb{P}[A \mid B]\,\mathbb{P}[B] & \text{si } \mathbb{P}[B] \neq 0 \\
\mathbb{P}[B \mid A]\,\mathbb{P}[A] & \text{si } \mathbb{P}[A] \neq 0 \\
0 & \text{sinon}
\end{cases}
$$

La probabilité de l'intersection s'appelle aussi **probabilité jointe** ; elle se note $\mathbb{P}[A, B]$, et sous les conditions ci-dessus :

$$
\mathbb{P}[A \cap B] = \mathbb{P}[A, B] = \mathbb{P}[A \mid B]\,\mathbb{P}[B] = \mathbb{P}[B \mid A]\,\mathbb{P}[A]
$$

# Propriétés

**Généralisation à $n$ évènements.** Soient $A_1, \dots, A_n$ des évènements tels que $\mathbb{P}[A_1 \cap \dots \cap A_{n-1}] > 0$. Alors

$$\mathbb{P}[A_1 \cap \dots \cap A_n] = \mathbb{P}[A_1]\,\mathbb{P}[A_2 \mid A_1]\,\mathbb{P}[A_3 \mid A_1 \cap A_2] \cdots \mathbb{P}[A_n \mid A_1 \cap \dots \cap A_{n-1}]$$

# Interprétation

Pour $\mathbb{P}[B] \neq 0$, la probabilité que $A$ et $B$ se produisent simultanément s'obtient en multipliant la probabilité de $B$ par la probabilité de $A$ sachant $B$ ; symétriquement, lorsque $\mathbb{P}[A] \neq 0$, en multipliant la probabilité de $A$ par la probabilité de $B$ sachant $A$.

# Remarque

- La règle s'emploie avec un [[Système complet d'évènements]] pour obtenir la [[Formule des probabilités totales]].
- Elle s'applique également le long des branches d'un [[Arbre de probabilité]].
