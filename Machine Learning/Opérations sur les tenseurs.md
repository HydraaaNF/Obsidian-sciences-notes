#ml-1

# Définition

Les opérations sur les [[Tenseur|tenseurs]] se rangent en trois familles.

- Opérations élément par élément : addition, ou application d'une même fonction à chaque élément.
- Opérations qui combinent les éléments : moyenne, somme.
- Opérations entre tenseurs : multiplication.

# Exemple

Application d'une même fonction $f$ à chaque élément :
$$[1,\ 2,\ 3] \xrightarrow{f} [f(1),\ f(2),\ f(3)]$$

Somme des éléments :
$$[1,\ 2,\ 3] \xrightarrow{\text{sum}} 6$$

Produit de deux vecteurs, $(4,\ 5,\ 6)$ et $(1,\ 2,\ 3)$ :
$$(4,\ 5,\ 6) \times (1,\ 2,\ 3) = 4 \times 1 + 5 \times 2 + 6 \times 3 = 32$$

# Remarque

Ces opérations ne s'écrivent jamais comme une boucle Python : elles s'appliquent d'un bloc à tout le tenseur, comme sur les [[Tenseurs PyTorch|tenseurs PyTorch]].

La [[Forme d'un tenseur|forme]] des tenseurs et la [[Diffusion entre tenseurs|diffusion]] déterminent les combinaisons réalisables entre tenseurs de formes différentes.
