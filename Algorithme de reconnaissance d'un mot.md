## Avec AFD
```pseudo
\begin{algorithm}
\caption{Algortihme de reconnaissance d'un mot (AFD)}
\begin{algorithmic}
\Require $u = u_1 \ldots u_n$ le mot à reconnaître, $A = (Q, q_0, \delta, F)$ l'AFD
\Ensure \textbf{true} si le mot est reconnu, \textbf{false} sinon
\State $q \gets q_0$
\State $i \gets 1$
\While{$i \leq n$}
	\State $q \gets \delta(q, u_i)$
	\State $i \gets i + 1$
\EndWhile
\If{$q \in F$}
	\Return \textbf{true}
\EndIf
\Return \textbf{false}
\end{algorithmic}
\end{algorithm}
```
