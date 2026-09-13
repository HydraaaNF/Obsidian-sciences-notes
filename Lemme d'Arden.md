## Énoncé
Soit $A$ et $B$ deux langages. Le langage $L = A^*B$ est le plus petit langage qui est la solution de $X = AX \cup B$.
De plus, si $\epsilon \notin A$, alors $A^*B$ est l'unique solution de cette équation.

## Démonstration
- Supposons que $L = A^*B$ est solution. On a alors: $$AL \cup B = A(A^*B) \cup B = ((AA^*\{\epsilon\})\cup \{\epsilon\})B = (A^+\cup \{\epsilon\})B = A^*B$$ donc $A^*B$ est une solution de l'équation.
- Montrons maintenant qu'elle est la plus petite. Supposons $L$, une autre solution à l'équation, on a : $$L = AL \cup B = A(AL \cup B) \cup B = A^2L \cup AB \cup B$$ $$ L = A^{n+1}L \cup \bigcup_{i=0}^{n} A^iB$$En continuant de remplacer $L$ par $AL \cup B$, on obtient que L contient tous les $A^nB$, $n > 0$, donc $A^*B$.
- Montrons que si $A$ ne contient pas $\epsilon$, alors c'est la seule solution. Soit $w \in L$ un mot de longueur $n$. On a : $$w \in L \iff w \in A^{n+1}L \cup \bigcup_{i=0}^{n} A^iB$$Comme $\epsilon \notin A$, $w$ n'appartient pas à $A^{n+1}L$, donc $w \in \bigcup_{i=0}^{n} A^iB$, donc $w \in A^*B$. On en conclut que $L \subseteq A^*B$ d'où $L = A^*B$.