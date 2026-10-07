# Définition

Un [[Processus stochastique]] est dit :

- **indépendant** si ses fonctions de répartition $F$ (voir [[Fonctions de répartition d'un processus stochastique]]) vérifient
$$F(\mathbf{x}; \mathbf{t}) = \prod F(\mathbf{x}_i, \mathbf{t}_i)$$

- **strictement stationnaire** si
$$F(\mathbf{x}; \mathbf{t}) = F(\mathbf{x}; \mathbf{t} + \tau) \quad \forall \mathbf{x}, \mathbf{t}, \tau, n \geq 1$$

- **stationnaire au sens large** si :
  1. $\mu(t) = \mathbb{E}[X(t)]$ ne dépend pas de $t$ ;
  2. $\mathbb{E}[X(t_1)X(t_2)] = R(t_1, t_2) = R(0, t_2 - t_1) = R(\tau)$ ;
  3. $R(0) < \infty$.

# Remarque

Le [[Processus de Poisson]] est un exemple de processus à accroissements indépendants et stationnaires.
