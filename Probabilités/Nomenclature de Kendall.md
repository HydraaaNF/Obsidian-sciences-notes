# Définition

Pour classifier les différentes [[File d'attente|files d'attente]], on utilise la nomenclature

$$K_1/K_2/K_3/K_4/K_5/K_6$$

où

1. $K_1$ représente la loi des [[Processus d'arrivée et de service|temps d'inter-arrivées]] (supposés i.i.d.).
2. $K_2$ représente la loi des v.a. i.i.d. $S_n$ (loi des durées de service).
3. $K_3$ est le nombre de serveurs montés en parallèle.
4. $K_4$ est la discipline d'attente.
5. $K_5$ est la capacité de la file, c'est-à-dire le nombre de places dans la zone d'attente plus le nombre de serveurs.
6. $K_6$ est le nombre de clients susceptibles de demander un service.

# Remarque

1. $K_4$ peut être PAPS (ou FIFO), DAPS (LIFO), ou une discipline plus compliquée intégrant des priorités sur certains clients (par exemple le gestionnaire du réseau peut être prioritaire sur tout autre client). Comme on s'intéresse au nombre global de clients dans le système à l'instant $t$, la discipline de service ne joue pas de rôle prépondérant et, par défaut, elle est supposée du type PAPS.
2. Par défaut, $K_5$ et $K_6$ sont supposés $\infty$. Pour un réseau fermé (tel l'Intranet de l'Enssat), on connaît exactement le nombre potentiel de clients $K_6$, qui dans un tel cas ne doit pas être considéré comme infini.
3. On emploie des notations standard pour $K_1$ et $K_2$ :
   - la lettre $M$ est mise pour « Memoryless » : elle signifie que $T_{n+1} - T_n$ (ou $S_n$) suit une [[Loi exponentielle|loi exponentielle]] ;
   - la notation $E_k$ se lit « [[Loi gamma|loi d'Erlang]] $k$ » (c'est la loi $\Gamma(k, \beta)$) ;
   - la lettre $D$ est mise pour « déterministe » ;
   - la lettre $G$ signifie « loi générale » (notamment utilisée lorsque la loi est inconnue).

La nomenclature s'applique à toute file d'attente, par exemple la [[File M-M-1|file M/M/1]].

# Exemple

- Une file $M/D/3$ a des temps d'inter-arrivées exponentiels, des durées de service constantes, 3 serveurs montés en parallèle ; par défaut, la discipline est PAPS, la capacité du système est considérée $\infty$, ainsi que le nombre de clients potentiels.
- Une file $G/M/2/4$ a des temps d'inter-arrivées suivant une loi quelconque, des durées de service exponentielles, 2 serveurs et 2 places dans la zone d'attente ($2+2=4$) ; par défaut, la discipline est PAPS et le nombre de clients potentiels est $\infty$.
